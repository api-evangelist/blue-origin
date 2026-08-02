---
name: Find Blue Origin Shop products and answer store questions
description: Search the Blue Origin Shop catalogue over MCP, pull full product and variant detail, and answer buyer questions about store policies — all without credentials.
api: mcp/blue-origin-mcp.yml
endpoint: https://shop.blueorigin.com/api/mcp
operations: [search_catalog, get_product_details, search_shop_policies_and_faqs]
generated: '2026-08-02'
method: generated
source: live tools/list at https://shop.blueorigin.com/api/mcp
---

# Find Blue Origin Shop products and answer store questions

The Blue Origin Shop is the only Blue Origin surface an agent can actually read. It
speaks MCP over HTTP at `https://shop.blueorigin.com/api/mcp` and needs **no
credential** for any of the three tools in this skill.

Do not attempt to read `www.blueorigin.com` for product or company data: every path on
the corporate site, `/robots.txt` included, returns HTTP 429 behind a Vercel Security
Checkpoint.

## Preconditions

- Transport: `POST https://shop.blueorigin.com/api/mcp`, `Content-Type: application/json`,
  `Accept: application/json, text/event-stream`, JSON-RPC 2.0.
- Confirm the tool set first with `tools/list`; it returned five tools on 2026-08-02.
- Optional: `GET https://shop.blueorigin.com/.well-known/ucp` to confirm the store still
  advertises UCP `2026-04-08` and the `dev.ucp.shopping.catalog.*` capabilities.

## Steps

1. **Search the catalogue — `search_catalog`.**
   Pass `catalog.query` with the buyer's natural-language intent, or filter criteria, or
   both — at least one is required. Put buyer locale in `catalog.context`
   (`address_country` as ISO 3166-1 alpha-2, `address_region`, `postal_code`,
   `currency`) so prices and availability are correct.
   The response is UCP `dev.ucp.shopping.catalog.search` shaped and **paginated**: the
   first page is deliberately short. Only fetch more when the buyer asks, by replaying
   the call with the `pagination.cursor` returned by the previous response.

2. **Get the exact variant — `get_product_details`.**
   Required: `product_id` in Shopify GID form (`gid://shopify/Product/123`), which comes
   from the search results — never construct one.
   Pass `options` to pin a variant (e.g. `{"Size":"10","Color":"Black"}`); without it the
   first available variant is returned, which is usually **not** what the buyer asked
   for. Pass `country` and `language` for localized copy and pricing.

3. **Answer policy and logistics questions — `search_shop_policies_and_faqs`.**
   Required: `query`, a natural-language question ("what is your return policy", "do you
   ship to Canada", "what are your hours"). Optional `context` carries buyer
   circumstances. Use this instead of scraping the HTML policy pages; the store also
   serves them at `/policies/refund-policy`, `/policies/shipping-policy`,
   `/policies/privacy-policy` and `/policies/terms-of-service` if you need the source.

## Conventions and error handling

- **Rate limits.** The MCP endpoint is rate limited per IP. On HTTP 429, back off
  exponentially — do not retry tightly.
- **Errors are JSON-RPC 2.0 error objects**, not RFC 9457 problem details. See
  `errors/blue-origin-problem-types.yml`.
- **Do not use `/api/ucp/mcp`** for anonymous work: it requires a UCP agent profile URI
  and returns `-32001 invalid_profile_url` (HTTP 422) without one.
- **No idempotency contract exists** on this surface. These three tools are reads, so
  retries are safe; the cart tools are not — see the cart skill.

## Read-only fallbacks (no MCP)

If MCP is unavailable, the store publishes plain JSON:
`GET /products.json`, `GET /products/{handle}.json`,
`GET /collections/{handle}/products.json`, `GET /search?q={query}&type=product`.

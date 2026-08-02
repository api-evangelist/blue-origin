---
name: Build a Blue Origin Shop cart and hand off to buyer-approved checkout
description: Create and mutate a cart on the Blue Origin Shop over MCP — line items, buyer identity, delivery addresses, delivery options, discount and gift-card codes — then stop at the checkout URL for contemporaneous buyer approval.
api: mcp/blue-origin-mcp.yml
endpoint: https://shop.blueorigin.com/api/mcp
operations: [search_catalog, get_product_details, update_cart, get_cart]
generated: '2026-08-02'
method: generated
source: live tools/list at https://shop.blueorigin.com/api/mcp
---

# Build a Blue Origin Shop cart and hand off to buyer-approved checkout

`update_cart` is a single consolidated mutation covering the whole cart lifecycle on
`https://shop.blueorigin.com/api/mcp`. `get_cart` reads the current state including the
checkout URL. Neither requires a credential.

**Hard rule from the store's own `llms.txt`: checkout requires human approval. An agent
must not complete payment without explicit, contemporaneous buyer consent.** If you
cannot get that consent at the moment of payment, do not proceed — route the purchase
through the Shop skill at `https://shop.app/SKILL.md` instead.

## Steps

1. **Resolve the item.** Use `search_catalog`, then `get_product_details` with the
   `options` you need, to obtain the exact variant. Never invent a Shopify GID.

2. **Create the cart — `update_cart` with no `cart_id`.**
   Omitting `cart_id` creates a new cart, and in that case `add_items` is required.
   Keep the returned cart id (`gid://shopify/Cart/...`) for every later call.

3. **Add buyer and delivery context — `update_cart` with `cart_id`.**
   - `buyer_identity` — email, phone, delivery address.
   - `delivery_addresses_to_add` to append, or `delivery_addresses_to_replace` to
     replace **all** existing cart delivery addresses. Choose deliberately; replace is
     destructive.
   - Delivery options only become available once the cart has both items and a delivery
     address. Fetch the cart, then set `selected_delivery_options`.

4. **Adjust quantities — `update_cart`.**
   `update_items` changes quantities on existing lines; quantity `0` removes a line.
   `remove_line_ids` removes lines explicitly.

5. **Apply codes only when the buyer raises them.**
   `discount_codes` and `gift_card_codes` — the tool schema is explicit that you should
   only prompt for these if the customer mentions having one. Do not fish for discounts.

6. **Add instructions with `note`** if the buyer has special requirements.

7. **Read back — `get_cart` with the required `cart_id`.**
   Returns line items, shipping options, discount info and the **checkout URL**.

8. **Stop here.** Present the checkout URL and the totals to the buyer and let them
   complete payment themselves. Payment handlers advertised by the store's UCP profile
   are Google Pay, Shopify card, and Shop Pay.

## Conventions and error handling

- **No idempotency.** There is no idempotency key on this API and no documented replay
  window. Repeating an `add_items` call adds the items **again**. After any failed or
  ambiguous `update_cart`, call `get_cart` and reconcile before retrying — never blind
  retry a mutation.
- **Rate limits.** Per-IP; back off on HTTP 429.
- **Localization.** Pass `context.address_country` and `context.currency` on catalogue
  calls so cart pricing matches what the buyer was shown.
- **Errors** are JSON-RPC 2.0 error objects (`errors/blue-origin-problem-types.yml`),
  not RFC 9457.
- **Authenticated variant.** Signed-in shopper operations (order history, saved
  addresses) need the Shopify customer-account authorization server and the
  `customer-account-api:full` / `customer-account-mcp-api:full` scopes — see
  `authentication/blue-origin-authentication.yml` and `scopes/blue-origin-scopes.yml`.

## Out of scope

This is merchandise. Blue Origin exposes **no** API for launch, payload manifesting,
New Shepard seats or supplier onboarding — those run through login-walled portals
(`payloads.blueorigin.com`, `bodp.blueorigin.com`, `supplierportal.blueorigin.com`) with
no public contract.

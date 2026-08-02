# Blue Origin

Blue Origin is an American private aerospace manufacturer and spaceflight services company founded
in 2000 by Jeff Bezos and headquartered in Kent, Washington — New Shepard, New Glenn, the BE-3 and
BE-4 engines, Blue Moon and Blue Ring.

**Blue Origin publishes no public API for any of its space products.** There is no developer
portal, no API documentation and no OpenAPI, AsyncAPI or A2A agent card on any `blueorigin.com`
host. Customer, payload and supplier relationships run through login-walled portals.

The one genuinely agent-addressable surface is the **Blue Origin Shop** (`shop.blueorigin.com`), a
Shopify storefront that serves a real `llms.txt` and `agents.md`, a Universal Commerce Protocol
merchant profile, RFC 9728 protected-resource metadata, and an **anonymous MCP server at
`/api/mcp` with five tools**.

The corporate site sits behind a Vercel Security Checkpoint that answers **HTTP 429 to every
non-browser request, `/robots.txt` included** — agents cannot read `www.blueorigin.com` at all.

- Website: https://www.blueorigin.com/
- Shop (agent surface): https://shop.blueorigin.com/agents.md
- Secondary market: https://www.hiive.com/securities/blue-origin-stock

See [`apis.yml`](apis.yml) for the full APIs.json record and
[`well-known/blue-origin-well-known.yml`](well-known/blue-origin-well-known.yml) for the complete
probe matrix across all seven hosts.

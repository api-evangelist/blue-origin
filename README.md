# Blue Origin

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Blue Origin is an American private aerospace manufacturer and spaceflight services company founded in 2000 by Jeff Bezos and headquartered in Kent, Washington. It builds and flies the reusable New Shepard suborbital vehicle, the heavy-lift New Glenn orbital launch vehicle, the BE-3 and BE-4 rocket engines, the Blue Moon lunar lander and the Blue Ring orbital transfer vehicle, and it owns Honeybee Robotics. Blue Origin publishes no public developer portal, no API documentation and no machine-readable API description for any of its space products; customer, payload and supplier relationships run through authenticated portals — payloads.blueorigin.com and bodp.blueorigin.com on Salesforce Experience Cloud, and supplierportal.blueorigin.com on AWS GovCloud. The only genuinely agent-addressable surface on a blueorigin.com host is the Blue Origin Shop, a Shopify storefront that publishes a real llms.txt and agents.md, a Universal Commerce Protocol (UCP) merchant profile, RFC 9728 protected-resource metadata, and an anonymous MCP server at /api/mcp exposing five tools. The corporate site itself sits behind a Vercel Security Checkpoint that answers HTTP 429 to every non-browser request, including /robots.txt.

**Areas:** Company · Aerospace · Space · Spaceflight · Launch Services · Satellite · Rocket Engines · Defense · Manufacturing · E-Commerce · MCP

## Blue Origin on APIs.io

Everything profiled for Blue Origin is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/blue-origin/](https://apis.io/providers/blue-origin/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Blue Origin Shop MCP Server](https://apis.io/apis/blue-origin/blue-origin-shop-mcp-server/) — The Blue Origin Shop storefront exposes an anonymous Model Context Protocol endpoint at https://shop.blueorigin.com/api/mcp. A live tools/list returned five…
- [Blue Origin Shop Storefront JSON](https://apis.io/apis/blue-origin/blue-origin-shop-storefront-json/) — The read-only JSON surface of the Blue Origin Shop Shopify storefront, documented by the store's own llms.txt/agents.md: GET /products.json and GET…
- [Blue Origin Customer Portal (Payloads) Platform API](https://apis.io/apis/blue-origin/blue-origin-customer-portal-payloads-platform-api/) — payloads.blueorigin.com is Blue Origin's customer portal for payload customers, running on Salesforce Experience Cloud. Blue Origin publishes no…
- [Blue Origin Data Portal (BODP) Platform API](https://apis.io/apis/blue-origin/blue-origin-data-portal-bodp-platform-api/) — bodp.blueorigin.com is the Blue Origin Data Portal, a second Salesforce Experience Cloud community on the same Salesforce org as the payloads customer…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [blue-origin-shop](https://apis.io/servers/blue-origin/blue-origin-shop/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Blue Origin Authentication](https://apis.io/security/blue-origin/blue-origin-authentication/)
- [Blue Origin Domain Security](https://apis.io/security/blue-origin/blue-origin-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Blue Origin Scopes](https://apis.io/scopes/blue-origin/blue-origin-scopes/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.blueorigin.com/)
- [Sign up](https://shop.blueorigin.com/account/register)
- [Blog](https://www.blueorigin.com/news)
- [Terms of service](https://www.blueorigin.com/terms-of-use)
- [Privacy policy](https://www.blueorigin.com/privacy-policy)
- [GitHub](https://github.com/BlueOrigin)

## API Evangelist rating

**Kin Score 20.5** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 0.0 |
| Contract governance | 18.2 |
| Operational transparency | 2.6 |
| Developer ergonomics | 14.9 |
| Access clarity | 23.7 |

**Agent readiness 21.2** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | platform (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | platform (partial credit) |

**Regulatory alignment 30.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/blue-origin/](https://apis.io/providers/blue-origin/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Blue Origin: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/blue-origin/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

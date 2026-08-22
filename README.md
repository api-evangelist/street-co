# Street.co.uk (street-co)

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

Street.co.uk (Street Systems Limited, Manchester, England) is a UK estate agency CRM and property management platform for residential sales, lettings, property management and client accounting. In the United Kingdom there is no MLS and no RESO — residential listing distribution runs from agency CRM software out to the Rightmove and Zoopla portals — which places Street.co.uk at the agency system-of-record layer of the value chain, upstream of the portal duopoly and alongside Reapit, Alto and Apex27. Its API posture is unusually open for this sector: three OpenAPI 3.1 contracts (Street Open API, Property Feed, Spectre) are published unauthenticated on a public Scalar developer portal at developers.street.co.uk and can be downloaded as JSON or YAML by anyone. Access to the data behind them is not open — production bearer tokens are generated inside a paying agency's Street account under Settings > Account Administration > Applications, and a non-customer developer must email apis@street.co.uk to be issued a sandbox token on the staging environment. Nothing RESO, no OData `$metadata`, and no open government data is published by Street.co.uk itself; the open UK property data layer sits with HM Land Registry and Ordnance Survey, not with the CRM vendors.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/street-co/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/street-co/refs/heads/main/apis.yml)

## Tags

- Real Estate
- United Kingdom
- PropTech
- CRM
- Property Listings
- Property Management
- Rentals
- Lettings
- Estate Agency
- Valuation
- Conveyancing

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

### Street Open API

The main Street.co.uk platform API — a JSON:API-conformant REST interface over the estate agency system of record, covering properties, sales and lettings instructions, offers, applicants, viewings, valuations, tenancies, tenants, landlords, vendors, maintenance jobs and requests, inspections, invoices, documents, e-sign documents, notes, tasks, users, branches and brands, plus read access to portal listings. 74 paths and 80 operations documented in a published OpenAPI 3.1 contract.

- **Human URL:** [https://developers.street.co.uk/docs/street-open-api](https://developers.street.co.uk/docs/street-open-api)
- **Base URL:** `https://street.co.uk/open-api/v1`

#### Tags

- Real Estate
- CRM
- Property Listings
- Lettings
- Property Management
- Valuation
- United Kingdom

#### Properties

- [OpenAPI](openapi/street-co-open-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI (verbatim source)](openapi/_original/street-co-open-api-openapi.json)
- [Documentation](https://developers.street.co.uk/docs/street-open-api)
- [API Reference](https://developers.street.co.uk/docs/street-open-api/api-reference)
- [Open API product page](https://street.co.uk/developers/api)
- [Sandbox](https://demo.street.co.uk/open-api/v1) — staging environment, sandbox token by email request
- [Support](https://api-support.street.co.uk/)
- [Change Log](https://developers.street.co.uk/docs/street-open-api/updates)

### Street Property Feed API

A read-only property feed API for powering an agency's own website and property search — sales search, lettings search, a single property record, area lookups and a property features list. Five paths, all GET, documented in a published OpenAPI 3.1 contract. Serves the UK's portal-and-agency-website distribution model rather than any MLS or IDX arrangement.

- **Human URL:** [https://developers.street.co.uk/docs/street-property-feed-api](https://developers.street.co.uk/docs/street-property-feed-api)
- **Base URL:** `https://street.co.uk/api/property-feed/v1`

#### Tags

- Real Estate
- Property Listings
- Search
- Rentals
- United Kingdom

#### Properties

- [OpenAPI](openapi/street-co-property-feed-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI (verbatim source)](openapi/_original/street-co-property-feed-api-openapi.json)
- [Documentation](https://developers.street.co.uk/docs/street-property-feed-api)
- [API Reference](https://developers.street.co.uk/docs/street-property-feed-api/api-reference)
- [Sandbox](https://demo.street.co.uk/api/property-feed/v1)

### Spectre API

The public API for the Spectre products, documented on the Street.co.uk developer portal and integrated into the Street CRM. Covers Spectre Property Reports (create and retrieve property reports, retrieve report leads) and Spectre email marketing (contacts and segments). Six paths documented in a published OpenAPI 3.1 contract; tokens are issued by the Spectre team on email request.

- **Human URL:** [https://developers.street.co.uk/docs/spectre-api-docs](https://developers.street.co.uk/docs/spectre-api-docs)
- **Base URL:** `https://api.spectre.uk.com/v1`

#### Tags

- Real Estate
- Property Reports
- Marketing
- Lead Generation
- United Kingdom

#### Properties

- [OpenAPI](openapi/street-co-spectre-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI (verbatim source)](openapi/_original/street-co-spectre-api-openapi.json)
- [Documentation](https://developers.street.co.uk/docs/spectre-api-docs)
- [API Reference](https://developers.street.co.uk/docs/spectre-api-docs/api-reference)

## Common Properties

- [Website](https://street.co.uk/)
- [Developer Portal](https://developers.street.co.uk/)
- [Documentation](https://developers.street.co.uk/docs/street-open-api)
- [Blog](https://street.co.uk/blog)
- [Pricing](https://street.co.uk/pricing)
- [Integrations](https://street.co.uk/integrations)
- [Support](https://api-support.street.co.uk/)
- [Contact](mailto:apis@street.co.uk) — API team contact for sandbox and rate-limit requests
- [LLMs Text](https://developers.street.co.uk/llms.txt)
- [Review](review.yml)

## Access & Posture

- **Home market:** United Kingdom
- **RESO posture:** No RESO reference found. No Web API certification, no Data Dictionary version, no UPI, no OData `$metadata`. The UK has no MLS and no RESO adoption.
- **Access gate:** Application-approval. Production bearer tokens come from inside a paying Street.co.uk agency account (Settings > Account Administration > Applications); a non-customer must email `apis@street.co.uk` for a sandbox token on the staging environment. Spectre tokens come from `apis@spectre.uk.com`. No MLS membership, board membership, IDX/VOW licence, or agent licensing is required — the UK has none of that apparatus.
- **Open data:** None published by Street.co.uk. The open UK property data layer is governmental (HM Land Registry Price Paid Data, Ordnance Survey), not vendor-published.
- **Auth model:** HTTP Bearer token, declared in all three OpenAPI documents. No OAuth 2.0, no OpenID Connect (`/.well-known/openid-configuration` returned 404).
- **Webhooks:** Marketed on the Open API product page but not documented and not present in any published spec.
- **SDKs / Postman / CLI / MCP:** None first-party. Community JSON:API clients are recommended for PHP.

See [review.yml](review.yml) for every URL probed with its HTTP status, verbatim access-gate quotes, and harvest provenance.

## Maintainers

- Kin Lane — kin@apievangelist.com

# Street.co.uk (street-co)

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

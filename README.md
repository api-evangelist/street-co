# Street.co.uk

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

Street.co.uk (Street Systems Limited, Manchester, England) is a UK estate agency CRM and property management platform for residential sales, lettings, property management and client accounting. In the United Kingdom there is no MLS and no RESO — residential listing distribution runs from agency CRM software out to the Rightmove and Zoopla portals — which places Street.co.uk at the agency system-of-record layer of the value chain, upstream of the portal duopoly and alongside Reapit, Alto and Apex27. Its API posture is unusually open for this sector: three OpenAPI 3.1 contracts (Street Open API, Property Feed, Spectre) are published unauthenticated on a public Scalar developer portal at developers.street.co.uk and can be downloaded as JSON or YAML by anyone. Access to the data behind them is not open — production bearer tokens are generated inside a paying agency's Street account under Settings > Account Administration > Applications, and a non-customer developer must email apis@street.co.uk to be issued a sandbox token on the staging environment. Nothing RESO, no OData $metadata, and no open government data is published by Street.co.uk itself; the open UK property data layer sits with HM Land Registry and Ordnance Survey, not with the CRM vendors.

**Areas:** Real Estate · United Kingdom · PropTech · CRM · Property Listings · Property Management · Rentals · Lettings · Estate Agency · Valuation · Conveyancing

## Street.co.uk on APIs.io

Everything profiled for Street.co.uk is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/street-co/](https://apis.io/providers/street-co/)** — or go straight to one of the APIs or properties below.

### APIs (43)

- [Street.co.uk Activity API](https://apis.io/apis/street-co/street-co-activity-api/) — Activity endpoints for this API.
- [Street.co.uk Applicants API](https://apis.io/apis/street-co/street-co-applicants-api/) — Applicants endpoints for this API.
- [Street.co.uk Areas API](https://apis.io/apis/street-co/street-co-areas-api/) — Area endpoints for this API.
- [Street.co.uk Branches API](https://apis.io/apis/street-co/street-co-branches-api/) — Branches endpoints for this API.
- [Street.co.uk Brands API](https://apis.io/apis/street-co/street-co-brands-api/) — Brands endpoints for this API.
- [Street.co.uk Companies API](https://apis.io/apis/street-co/street-co-companies-api/) — Companies endpoints for this API.
- [Street.co.uk Documents API](https://apis.io/apis/street-co/street-co-documents-api/) — Documents endpoints for this API.
- [Street.co.uk E-Sign Documents API](https://apis.io/apis/street-co/street-co-e-sign-documents-api/) — E-Sign Documents endpoints for this API.
- [Street.co.uk Email API](https://apis.io/apis/street-co/street-co-email-api/) — The Email API from Street.co.uk — 2 operation(s) for email.
- [Street.co.uk Enquiries API](https://apis.io/apis/street-co/street-co-enquiries-api/) — Enquiries endpoints for this API.
- [Street.co.uk Follow Ups API](https://apis.io/apis/street-co/street-co-follow-ups-api/) — Follow Ups endpoints for this API.
- [Street.co.uk Images API](https://apis.io/apis/street-co/street-co-images-api/) — Image endpoints for this API.
- [Street.co.uk Inspections API](https://apis.io/apis/street-co/street-co-inspections-api/) — Inspections endpoints for this API.
- [Street.co.uk Interested Applicants API](https://apis.io/apis/street-co/street-co-interested-applicants-api/) — Interested Applicants endpoints for this API.
- [Street.co.uk Invoices API](https://apis.io/apis/street-co/street-co-invoices-api/) — Invoices endpoints for this API.
- [Street.co.uk Landlords API](https://apis.io/apis/street-co/street-co-landlords-api/) — Landlords endpoints for this API.
- [Street.co.uk Lettings API](https://apis.io/apis/street-co/street-co-lettings-api/) — These are the lettings specific API Endpoints.
- [Street.co.uk Lettings Applications API](https://apis.io/apis/street-co/street-co-lettings-applications-api/) — Lettings Application endpoints for this API.
- [Street.co.uk Lettings Instructions API](https://apis.io/apis/street-co/street-co-lettings-instructions-api/) — Lettings Instruction endpoints for this API.
- [Street.co.uk Lettings Offers API](https://apis.io/apis/street-co/street-co-lettings-offers-api/) — Lettings Offers endpoints for this API.
- [Street.co.uk Maintenance Jobs API](https://apis.io/apis/street-co/street-co-maintenance-jobs-api/) — Maintenance Jobs endpoints for this API.
- [Street.co.uk Maintenance Requests API](https://apis.io/apis/street-co/street-co-maintenance-requests-api/) — Maintenance Request endpoints for this API.
- [Street.co.uk Meta API](https://apis.io/apis/street-co/street-co-meta-api/) — These are specific API Endpoints for retrieving meta information such as Areas or Features.
- [Street.co.uk Move Outs API](https://apis.io/apis/street-co/street-co-move-outs-api/) — Move Outs endpoints for this API.
- [Street.co.uk Notes API](https://apis.io/apis/street-co/street-co-notes-api/) — Notes endpoints for this API.
- [Street.co.uk People API](https://apis.io/apis/street-co/street-co-people-api/) — People endpoints for this API.
- [Street.co.uk Photos and Measures API](https://apis.io/apis/street-co/street-co-photos-and-measures-api/) — Photo and Measure endpoints for this API.
- [Street.co.uk Portal Listings API](https://apis.io/apis/street-co/street-co-portal-listings-api/) — Portal Listings endpoints for this API.
- [Street.co.uk Properties API](https://apis.io/apis/street-co/street-co-properties-api/) — Properties endpoints for this API.
- [Street.co.uk Property Keys API](https://apis.io/apis/street-co/street-co-property-keys-api/) — Property Key endpoints for this API.
- [Street.co.uk Property Reports API](https://apis.io/apis/street-co/street-co-property-reports-api/) — All endpoints for Spectre Property Reports
- [Street.co.uk Questionnaire Responses API](https://apis.io/apis/street-co/street-co-questionnaire-responses-api/) — Questionnaire Response endpoints for this API.
- [Street.co.uk Sales API](https://apis.io/apis/street-co/street-co-sales-api/) — Sales endpoints for this API.
- [Street.co.uk Sales Instructions API](https://apis.io/apis/street-co/street-co-sales-instructions-api/) — Sales Instructions endpoints for this API.
- [Street.co.uk Sales Offers API](https://apis.io/apis/street-co/street-co-sales-offers-api/) — Sales Offers endpoints for this API.
- [Street.co.uk Solicitors API](https://apis.io/apis/street-co/street-co-solicitors-api/) — Solicitors endpoints for this API.
- [Street.co.uk Tasks API](https://apis.io/apis/street-co/street-co-tasks-api/) — Tasks endpoints for this API.
- [Street.co.uk Tenancies API](https://apis.io/apis/street-co/street-co-tenancies-api/) — Tenancies endpoints for this API.
- [Street.co.uk Tenants API](https://apis.io/apis/street-co/street-co-tenants-api/) — Tenants endpoints for this API.
- [Street.co.uk Users API](https://apis.io/apis/street-co/street-co-users-api/) — Users endpoints for this API.
- [Street.co.uk Valuations API](https://apis.io/apis/street-co/street-co-valuations-api/) — Valuations endpoints for this API.
- [Street.co.uk Vendors API](https://apis.io/apis/street-co/street-co-vendors-api/) — Vendors endpoints for this API.
- [Street.co.uk Viewings API](https://apis.io/apis/street-co/street-co-viewings-api/) — Viewings endpoints for this API.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Street Co Webhooks](https://apis.io/asyncapis/street-co/street-co-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [street-co](https://apis.io/servers/street-co/street-co/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Street Co Agentic Access](https://apis.io/agentic-access/street-co/street-co-agentic-access/)

#### Collections (3)

Postman and Open Collection request collections.

- [Street Open API](https://apis.io/collections/street-co/open-street-co-open-api/)
- [Property Feed](https://apis.io/collections/street-co/open-street-co-property-feed-api/)
- [Spectre API](https://apis.io/collections/street-co/open-street-co-spectre-api/)

#### Overlays (3)

OpenAPI overlays, including conversational phrasing for each operation.

- [Street Co Open Api Overlay](https://apis.io/overlays/street-co/street-co-open-api-overlay/)
- [Street Co Property Feed Api Overlay](https://apis.io/overlays/street-co/street-co-property-feed-api-overlay/)
- [Street Co Spectre Api Overlay](https://apis.io/overlays/street-co/street-co-spectre-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Street Co Authentication](https://apis.io/security/street-co/street-co-authentication/)
- [Street Co Domain Security](https://apis.io/security/street-co/street-co-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Street Co Plans Pricing](https://apis.io/plans/street-co/street-co-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Street Co Rate Limits](https://apis.io/rate-limits/street-co/street-co-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://street.co.uk/)
- [Documentation](https://developers.street.co.uk/docs/street-open-api)
- [Getting started](https://developers.street.co.uk/docs/street-open-api)
- [Pricing](https://street.co.uk/pricing)
- [Support](https://api-support.street.co.uk/)
- [Blog](https://street.co.uk/blog)
- [Terms of service](https://street.co.uk/terms)
- [Privacy policy](https://street.co.uk/privacy)

## API Evangelist rating

**Kin Score 54.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 60.6 |
| Contract governance | 18.2 |
| Operational transparency | 63.2 |
| Developer ergonomics | 62.5 |
| Access clarity | 38.2 |

**Agent readiness 30.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/street-co/](https://apis.io/providers/street-co/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Street.co.uk: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/street-co/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

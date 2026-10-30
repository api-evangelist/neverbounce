# NeverBounce

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

NeverBounce is an email verification and list cleaning service — a ZoomInfo company — that validates individual email addresses in real time and cleans bulk lists by checking syntax, mailbox existence, role addresses, disposable addresses, catch-all domains, and deliverability to reduce bounce rates for marketing, sales, and transactional senders. The NeverBounce v4 REST API at https://api.neverbounce.com/v4.2/ provides ten published operations covering single email checks (/single/check), bulk list jobs (create, parse, start, status, results, search, delete, download), account credit info, and the Proof-of-Engagement confirmation used by the browser widget, with JSON responses over HTTPS. Authentication uses a per-integration API key (format `secret_xxxx...`) passed as the `key` parameter in the query string or request body; `public_` keys drive the JavaScript widget and cannot call the standard API. Application errors — including authentication failure and throttling — are returned with an HTTP 200 and a `status` field rather than a 4xx, which is the defining runtime quirk of this API.

**Areas:** Email Verification · Email Hygiene · Deliverability · Marketing · List Cleaning · Data Quality · ZoomInfo · Email

## NeverBounce on APIs.io

Everything profiled for NeverBounce is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/neverbounce/](https://apis.io/providers/neverbounce/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [NeverBounce API v4](https://apis.io/apis/neverbounce/v4-api/) — RESTful JSON API for email verification. Provides single email verification (`/single/check`), bulk job verification (`/jobs/create`, `/jobs/parse`,…
- [NeverBounce Account API](https://apis.io/apis/neverbounce/neverbounce-account-api/) — Account credit balances and job counts by state.
- [NeverBounce Jobs API](https://apis.io/apis/neverbounce/neverbounce-jobs-api/) — Bulk list verification jobs — create, parse, start, status, results, search, delete, download.
- [NeverBounce Single API](https://apis.io/apis/neverbounce/neverbounce-single-api/) — Real-time verification of a single email address.
- [NeverBounce POE API](https://apis.io/apis/neverbounce/neverbounce-poe-api/) — Proof of Engagement. Server-side confirmation that a verification produced by the browser JavaScript widget genuinely came from NeverBounce, using the…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Neverbounce Webhooks](https://apis.io/asyncapis/neverbounce/neverbounce-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [NeverBounce Developer Docs MCP](https://apis.io/servers/neverbounce/neverbounce-developer-docs-mcp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Neverbounce Agentic Access](https://apis.io/agentic-access/neverbounce/neverbounce-agentic-access/)

#### Collections (4)

Postman and Open Collection request collections.

- [NeverBounce API v4](https://apis.io/collections/neverbounce/open-neverbounce/)
- [NeverBounce API v4 Account API](https://apis.io/collections/neverbounce/open-neverbounce-account-api/)
- [NeverBounce API v4 Account Jobs API](https://apis.io/collections/neverbounce/open-neverbounce-jobs-api/)
- [NeverBounce API v4 Account Single API](https://apis.io/collections/neverbounce/open-neverbounce-single-api/)

#### Overlays (4)

OpenAPI overlays, including conversational phrasing for each operation.

- [Neverbounce Account Overlay](https://apis.io/overlays/neverbounce/neverbounce-account-overlay/)
- [Neverbounce Jobs Overlay](https://apis.io/overlays/neverbounce/neverbounce-jobs-overlay/)
- [Neverbounce Poe Overlay](https://apis.io/overlays/neverbounce/neverbounce-poe-overlay/)
- [Neverbounce Single Overlay](https://apis.io/overlays/neverbounce/neverbounce-single-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Neverbounce Authentication](https://apis.io/security/neverbounce/neverbounce-authentication/)
- [Neverbounce Domain Security](https://apis.io/security/neverbounce/neverbounce-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Neverbounce Plans Pricing](https://apis.io/plans/neverbounce/neverbounce-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Neverbounce Rate Limits](https://apis.io/rate-limits/neverbounce/neverbounce-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.neverbounce.com)
- [Documentation](https://developers.neverbounce.com/)
- [Getting started](https://developers.neverbounce.com/docs/api-getting-started)
- [API reference](https://developers.neverbounce.com/reference/getting-started)
- [Pricing](https://www.neverbounce.com/pricing)
- [Support](https://www.neverbounce.com/contact)
- [Blog](https://www.neverbounce.com/blog)
- [Terms of service](https://www.neverbounce.com/terms-of-use)
- [Privacy policy](https://www.zoominfo.com/legal/privacy-policy)
- [GitHub](https://github.com/NeverBounce)
- [Status](https://status.neverbounce.com)

## API Evangelist rating

**Kin Score 58.7** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 52.8 |
| Contract governance | 4.5 |
| Operational transparency | 81.6 |
| Developer ergonomics | 54.2 |
| Access clarity | 76.3 |

**Agent readiness 44.7** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
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
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/neverbounce/](https://apis.io/providers/neverbounce/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for NeverBounce: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/neverbounce/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

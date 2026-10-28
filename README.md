# APIClarity

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

APIClarity is an open source (Apache-2.0) API security and observability tool that captures API traffic in a Kubernetes environment, reconstructs OpenAPI specifications from what it observes, and detects shadow APIs, zombie APIs, specification drift and broken function-level authorization. It integrates with Istio, Kong, Tyk, Kuma, a tap DaemonSet and an OpenTelemetry Collector as traffic sources, and ships as a Helm chart you deploy into your own cluster — there is no hosted service, no vendor account and no vendor API host. It was part of the OpenClarity project. APIClarity has reached end of life: the source repository was archived read-only by its owner on 2026-05-29, the last release was v0.14.5 on 2023-05-05, and both project websites (openclarity.io and apiclarity.io) now return HTTP 404. The source, the eleven published specifications, the Helm chart repository and the container images all remain publicly readable, which is what this profile is built from.

**Areas:** API Observability · API Security · API Traffic Analysis · Cisco · Kubernetes · Open Source · OpenAPI Reconstruction · OpenClarity · Service Mesh · Shadow APIs

## APIClarity on APIs.io

Everything profiled for APIClarity is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/apiclarity/](https://apis.io/providers/apiclarity/)** — or go straight to one of the APIs or properties below.

### APIs (21)

- [APIClarity Control API](https://apis.io/apis/apiclarity/apiclarity-control-api/) — Control-plane endpoints for trace sources and discovered APIs.
- [APIClarity Features API](https://apis.io/apis/apiclarity/apiclarity-features-api/) — Enabled features in the deployment.
- [APIClarity API Events API](https://apis.io/apis/apiclarity/apiclarity-apievents-api/) — The ApiEvents API from APIClarity — 4 operation(s) for apievents.
- [APIClarity API Findings API](https://apis.io/apis/apiclarity/apiclarity-apifindings-api/) — The ApiFindings API from APIClarity — 2 operation(s) for apifindings.
- [APIClarity API Inventory API](https://apis.io/apis/apiclarity/apiclarity-apiinventory-api/) — The ApiInventory API from APIClarity — 11 operation(s) for apiinventory.
- [APIClarity Bfla API](https://apis.io/apis/apiclarity/apiclarity-bfla-api/) — The bfla API from APIClarity — 16 operation(s) for bfla.
- [APIClarity Dashboard API](https://apis.io/apis/apiclarity/apiclarity-dashboard-api/) — The Dashboard API from APIClarity — 3 operation(s) for dashboard.
- [APIClarity Enable API](https://apis.io/apis/apiclarity/apiclarity-enable-api/) — The Enable API from APIClarity — 1 operation(s) for enable.
- [APIClarity Event Annotations API](https://apis.io/apis/apiclarity/apiclarity-eventannotations-api/) — The EventAnnotations API from APIClarity — 1 operation(s) for eventannotations.
- [APIClarity Fuzzer API](https://apis.io/apis/apiclarity/apiclarity-fuzzer-api/) — The fuzzer API from APIClarity — 8 operation(s) for fuzzer.
- [APIClarity Hosts To Trace API](https://apis.io/apis/apiclarity/apiclarity-hoststotrace-api/) — The HostsToTrace API from APIClarity — 1 operation(s) for hoststotrace.
- [APIClarity Local Bfla API](https://apis.io/apis/apiclarity/apiclarity-local-bfla-api/) — The local-bfla API from APIClarity — 10 operation(s) for local-bfla.
- [APIClarity Local Fuzzer API](https://apis.io/apis/apiclarity/apiclarity-local-fuzzer-api/) — The local-fuzzer API from APIClarity — 10 operation(s) for local-fuzzer.
- [APIClarity Modules API](https://apis.io/apis/apiclarity/apiclarity-modules-api/) — The Modules API from APIClarity — 14 operation(s) for modules.
- [APIClarity Notification API](https://apis.io/apis/apiclarity/apiclarity-notification-api/) — The Notification API from APIClarity — 1 operation(s) for notification.
- [APIClarity Start API](https://apis.io/apis/apiclarity/apiclarity-start-api/) — The Start API from APIClarity — 1 operation(s) for start.
- [APIClarity State API](https://apis.io/apis/apiclarity/apiclarity-state-api/) — The State API from APIClarity — 1 operation(s) for state.
- [APIClarity Stop API](https://apis.io/apis/apiclarity/apiclarity-stop-api/) — The Stop API from APIClarity — 1 operation(s) for stop.
- [APIClarity Telemetry API](https://apis.io/apis/apiclarity/apiclarity-telemetry-api/) — The Telemetry API from APIClarity — 1 operation(s) for telemetry.
- [APIClarity Version API](https://apis.io/apis/apiclarity/apiclarity-version-api/) — The Version API from APIClarity — 1 operation(s) for version.
- [APIClarity API Usage API](https://apis.io/apis/apiclarity/apiclarity-api-usage-api/) — The API Usage API from APIClarity — 1 operation(s) for api usage.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Apiclarity Notifications Webhooks](https://apis.io/asyncapis/apiclarity/apiclarity-notifications-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [apiclarity-mcp.yml](https://apis.io/servers/apiclarity/apiclarity-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Apiclarity Agentic Access](https://apis.io/agentic-access/apiclarity/apiclarity-agentic-access/)

#### Collections (5)

Postman and Open Collection request collections.

- [APIClarity API](https://apis.io/collections/apiclarity/open-apiclarity/)
- [APIClarity API Events API](https://apis.io/collections/apiclarity/open-apiclarity-api-events-api/)
- [APIClarity API Events API Inventory API](https://apis.io/collections/apiclarity/open-apiclarity-api-inventory-api/)
- [APIClarity API Events Control API](https://apis.io/collections/apiclarity/open-apiclarity-control-api/)
- [APIClarity API Events Features API](https://apis.io/collections/apiclarity/open-apiclarity-features-api/)

#### Overlays (11)

OpenAPI overlays, including conversational phrasing for each operation.

- [Apiclarity Api Events Api Overlay](https://apis.io/overlays/apiclarity/apiclarity-api-events-api-overlay/)
- [Apiclarity Api Inventory Api Overlay](https://apis.io/overlays/apiclarity/apiclarity-api-inventory-api-overlay/)
- [Apiclarity Bfla Module Overlay](https://apis.io/overlays/apiclarity/apiclarity-bfla-module-overlay/)
- [Apiclarity Control Api Overlay](https://apis.io/overlays/apiclarity/apiclarity-control-api-overlay/)
- [Apiclarity Features Api Overlay](https://apis.io/overlays/apiclarity/apiclarity-features-api-overlay/)
- [Apiclarity Fuzzer Module Overlay](https://apis.io/overlays/apiclarity/apiclarity-fuzzer-module-overlay/)
- [Apiclarity Notifications Overlay](https://apis.io/overlays/apiclarity/apiclarity-notifications-overlay/)
- [Apiclarity Plugins Telemetry Swagger Overlay](https://apis.io/overlays/apiclarity/apiclarity-plugins-telemetry-swagger-overlay/)
- [Apiclarity Spec Differ Module Overlay](https://apis.io/overlays/apiclarity/apiclarity-spec-differ-module-overlay/)
- [Apiclarity Spec Reconstructor Module Overlay](https://apis.io/overlays/apiclarity/apiclarity-spec-reconstructor-module-overlay/)
- [Apiclarity Trace Analyzer Module Overlay](https://apis.io/overlays/apiclarity/apiclarity-trace-analyzer-module-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Apiclarity Authentication](https://apis.io/security/apiclarity/apiclarity-authentication/)
- [Apiclarity Domain Security](https://apis.io/security/apiclarity/apiclarity-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Apiclarity Plans Pricing](https://apis.io/plans/apiclarity/apiclarity-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Apiclarity Rate Limits](https://apis.io/rate-limits/apiclarity/apiclarity-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Apiclarity Finops](https://apis.io/finops/apiclarity/apiclarity-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://github.com/openclarity/apiclarity)
- [Documentation](https://github.com/openclarity/apiclarity#readme)
- [Getting started](https://github.com/openclarity/apiclarity#getting-started)
- [API reference](https://github.com/openclarity/apiclarity/tree/master/api3)
- [Support](https://github.com/openclarity/apiclarity/issues)
- [GitHub](https://github.com/openclarity)

## API Evangelist rating

**Kin Score 34.4** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 45.9 |
| Contract governance | 4.5 |
| Operational transparency | 26.3 |
| Developer ergonomics | 61.3 |
| Access clarity | 0.0 |

**Agent readiness 32.5** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
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

**Regulatory alignment 16.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/apiclarity/](https://apis.io/providers/apiclarity/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for APIClarity: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/apiclarity/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

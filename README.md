# APIClarity (apiclarity)
APIClarity is an open source API security and observability tool that analyzes API traffic to reconstruct OpenAPI specifications, detect shadow and zombie APIs, identify API differences and changes, and provide API security alerts. It is part of the OpenClarity project and works with Kubernetes service meshes and API gateways for cloud-native API traffic observability.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/apiclarity/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - API Observability, API Security, API Traffic Analysis, Cisco, Kubernetes, Open Source, OpenAPI Reconstruction, OpenClarity, Service Mesh, Shadow APIs

## Timestamps

- **Created:** 2026-03-26
- **Modified:** 2026-04-19

## APIs

### APIClarity API
The APIClarity API provides programmatic access to API traffic analysis, reconstructed OpenAPI specifications, API inventory, and security findings. It allows users to query discovered APIs, review spec diffs between observed and documented API behavior, and manage API security alerts.

**Human URL:** [https://github.com/openclarity/apiclarity](https://github.com/openclarity/apiclarity)

#### Tags:

 - API Inventory, API Security, API Traffic Analysis, OpenAPI Reconstruction, Shadow APIs

#### Properties

- [Documentation](https://github.com/openclarity/apiclarity#readme)
- [OpenAPI](https://github.com/openclarity/apiclarity/blob/master/api/server/restapi/spec.json)
- [GettingStarted](https://github.com/openclarity/apiclarity#getting-started)
- [GitHubRepository](https://github.com/openclarity/apiclarity)

## Common Properties

- [Website](https://openclarity.io)
- [GitHubOrganization](https://github.com/openclarity)
- [GitHubRepository](https://github.com/openclarity/apiclarity)
- [Documentation](https://github.com/openclarity/apiclarity#readme)
- [Issues](https://github.com/openclarity/apiclarity/issues)
- [Releases](https://github.com/openclarity/apiclarity/releases)
- [License](https://github.com/openclarity/apiclarity/blob/master/LICENSE)
- [Slack](https://outshift.slack.com)

## Features

| Name | Description |
|------|-------------|
| OpenAPI Spec Reconstruction | Automatically reconstruct OpenAPI specifications from observed live API traffic without code instrumentation. |
| Shadow API Detection | Identify undocumented shadow APIs being called in production that are not reflected in official specifications. |
| Zombie API Detection | Detect deprecated or decommissioned API endpoints still receiving traffic in production. |
| API Diff Analysis | Compare observed API behavior against documented specifications to identify drifts, changes, and violations. |
| API Security Alerts | Generate security findings and alerts based on API traffic analysis and specification violations. |
| Kubernetes Integration | Deploy as a sidecar or via Helm charts for integration with Kubernetes service meshes and API gateways. |
| API Inventory | Automatically build and maintain an inventory of all APIs discovered in the environment. |

## Use Cases

| Name | Description |
|------|-------------|
| API Discovery | Discover all APIs running in a Kubernetes environment including undocumented and shadow APIs. |
| API Security Posture Assessment | Assess API security by detecting shadow APIs, spec violations, and suspicious traffic patterns. |
| API Specification Generation | Generate OpenAPI specifications from live traffic for APIs that lack formal documentation. |
| API Governance | Enforce API consistency by detecting deviations between actual API behavior and official specifications. |
| Incident Response | Investigate API security incidents using traffic analysis, API inventory, and spec diff data. |

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com

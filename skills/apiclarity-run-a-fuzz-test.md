---
name: apiclarity-run-a-fuzz-test
description: Actively fuzz a discovered API against its specification and read the findings. HUMAN APPROVAL REQUIRED — this sends real traffic at a real service.
api: APIClarity Fuzzer module
base: /api/modules/fuzzer (relative — the host is your own deployment)
operations:
  - POST /modules/fuzzer/fuzz/{apiID}/start
  - POST /modules/fuzzer/fuzz/{apiID}/stop
  - GET /modules/fuzzer/fuzz/{apiID}/progress
  - GET /modules/fuzzer/fuzz/{apiID}/report
  - GET /modules/fuzzer/tests/{apiID}
  - GET /modules/fuzzer/apiFindings/{apiID}
  - GET /modules/fuzzer/annotatedspec/{apiID}
  - GET /modules/fuzzer/state
operation_ids:
  - fuzzerStartTest
  - fuzzerStopTest
  - fuzzerGetTestProgress
  - fuzzerGetTestReport
  - fuzzerGetTests
  - fuzzerGetAPIFindings
  - fuzzerGetAnnotatedSpec
  - fuzzergetState
source: openapi/_original/apiclarity-global-openapi.gen.yml
generated: '2026-09-04'
method: generated
---

# Run a fuzz test

> **Stop and read this first.** `fuzzerStartTest` is the highest-consequence operation in
> APIClarity. It sends generated traffic at a live API. There is **no dry-run mode**, **no
> idempotency key**, and `fuzzerStopTest` halts the run without unsending requests already
> delivered. An agent must not call this without explicit human approval, and never against a
> target the operator has not named.

## 1. Check the module is up

    GET /modules/fuzzer/state                            # fuzzergetState
    GET /modules/fuzzer/version                          # fuzzergetVersion

`TestingModuleState` returns `version` and `APIsInCache`.

## 2. Make sure the API has a specification

The fuzzer derives its test cases from the spec. Without one there is nothing to fuzz:

    GET /apiInventory/{apiId}/specs

If neither spec is present, provide or reconstruct one first.

## 3. Start the test

    POST /modules/fuzzer/fuzz/{apiID}/start              # fuzzerStartTest

Body is `TestInput`: `depth` (a `TestInputDepthEnum`) and `auth` (an `AuthorizationScheme` —
`BasicAuth`, `BearerToken` or `ApiToken`, so the fuzzer can reach authenticated endpoints).

This operation declares real error responses rather than a catch-all: **400** Status Bad
Request, **404** Service not found, **500** Internal Error.

## 4. Watch it

    GET /modules/fuzzer/fuzz/{apiID}/progress            # fuzzerGetTestProgress

`ShortTestProgress` returns `progress` (0-100) and `starttime`. 404 "Service not found" means no
test is running for that API.

To stop:

    POST /modules/fuzzer/fuzz/{apiID}/stop               # fuzzerStopTest

204 on success. Again: this halts the run. It does not roll anything back on the target.

## 5. Read the report

    GET /modules/fuzzer/fuzz/{apiID}/report              # fuzzerGetTestReport
    GET /modules/fuzzer/tests/{apiID}                    # fuzzerGetTests
    GET /modules/fuzzer/report/{apiID}/{timestamp}       # fuzzerGetReport
    GET /modules/fuzzer/report/{apiID}/{timestamp}/short # fuzzerGetShortReportByTimestamp

`FuzzingStatusAndReport` carries `status`, `progress` and a `report[]` of `FuzzingReportItem` —
each with `testType`, `status`, `findings[]` and `paths[]` of `FuzzingReportPath`
(`verb`, `uri`, `payload`, `response`, `result`). `Vulnerabilities` rolls the whole run up into
`critical` / `high` / `medium` / `low` / `total`.

## 6. Read findings against the spec

    GET /modules/fuzzer/apiFindings/{apiID}              # fuzzerGetAPIFindings
    GET /modules/fuzzer/annotatedspec/{apiID}            # fuzzerGetAnnotatedSpec

`apiFindings` returns the shared `APIFinding` schema — the same shape the trace analyzer and
BFLA modules emit, so findings unify across the security surface. `annotatedspec` returns the
OpenAPI document with findings attached to the operations they belong to, which is the artifact
worth handing to the API's owner. 404 "Spec not found" if there is no spec to annotate.

## Notifications

`TestProgressNotification` and `TestReportNotification` are pushed to
`POST /notification/{apiID}` if a listener is registered — poll only if it is not.

## Guardrails an agent should encode

- Require an explicit human confirmation naming the target `apiID` before `fuzzerStartTest`.
- Never retry `fuzzerStartTest` on timeout. No idempotency key exists; a retry is a second run.
- Treat a 500 as "check whether it started anyway" — call `fuzzerGetTestProgress` before retrying.

> APIClarity was archived read-only on 2026-05-29; the last release was v0.14.5 (2023-05-05).

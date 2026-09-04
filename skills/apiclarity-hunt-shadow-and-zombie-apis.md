---
name: apiclarity-hunt-shadow-and-zombie-apis
description: Find endpoints running in production that no specification documents (shadow) or that a specification marks deprecated (zombie).
api: APIClarity Core API + Spec Differ module
base: /api (relative — the host is your own deployment)
operations:
  - GET /apiInventory
  - POST /modules/spec_differ/{apiID}/start
  - POST /modules/spec_differ/{apiID}/stop
  - GET /apiEvents
  - GET /apiEvents/{eventId}
  - GET /apiEvents/{eventId}/providedSpecDiff
  - GET /apiEvents/{eventId}/reconstructedSpecDiff
  - GET /dashboard/apiUsage/latestDiffs
operation_ids:
  - spec_differStartDiffer
  - spec_differStopDiffer
source: openapi/_original/apiclarity-global-openapi.gen.yml
generated: '2026-09-04'
method: generated
---

# Hunt shadow and zombie APIs

A shadow API is an endpoint taking production traffic that no specification documents. A zombie
API is one a specification marks deprecated that is still being called. APIClarity finds both by
comparing observed traffic against the spec.

## 1. Make sure the API has a spec to diff against

Diffing needs a baseline. Either upload one:

    PUT /apiInventory/{apiId}/specs/providedSpec

or reconstruct one first (see `apiclarity-reconstruct-and-approve-a-spec`). `GET /apiInventory`
exposes `hasProvidedSpec[is]` and `hasReconstructedSpec[is]` filters so you can find APIs that
have neither.

## 2. Turn the differ on

    POST /modules/spec_differ/{apiID}/start              # spec_differStartDiffer
    POST /modules/spec_differ/{apiID}/stop               # spec_differStopDiffer

## 3. Pull the events that diverged

`GET /apiEvents` **requires** `startTime`, `endTime`, `page`, `pageSize`, `sortKey` and
`showNonApi`. Filter to divergent traffic:

    GET /apiEvents?startTime=...&endTime=...&page=1&pageSize=100
        &sortKey=time&sortDir=DESC&showNonApi=false
        &hasSpecDiff[is]=true

Narrow further with `specDiffType[is]`, `path[start]`, `statusCode[gte]`, `method[is]`,
`apiInfoId[is]` — over forty bracketed filters are declared.

## 4. Read the actual difference

    GET /apiEvents/{eventId}/providedSpecDiff
    GET /apiEvents/{eventId}/reconstructedSpecDiff

Each returns an `ApiEventSpecDiff`: `diffType`, `oldSpec`, `newSpec`. `diffType` is the
classification — it is what separates a shadow endpoint from a zombie one from ordinary drift.
Diff against the **provided** spec to audit against what you published; diff against the
**reconstructed** spec to see what changed in reality.

## 5. Roll it up

    GET /dashboard/apiUsage/latestDiffs
    GET /dashboard/apiUsage/mostUsed
    GET /apiUsage/hitCount?startTime=...&endTime=...

`ApiUsages` splits counts into `existingApis`, `newApis` and `apisWithDiff` — the one-number
answer to "is our documented surface drifting?"

## Conventions that will bite you

- `page` and `pageSize` are required, not optional. So are `startTime` and `endTime` on
  `/apiEvents`. Omitting them is a request error, not a default.
- Collections come back as `{ items: [...], total: n }`.
- Errors are `{"message": "..."}`, not problem+json.
- There is no rate limiting and no `Retry-After`; you are calling your own cluster.

## Automate it

Register a notification listener and you get `SpecDiffsNotification` pushed to
`POST /notification/{apiID}` instead of polling. Payload is `BaseNotification` + `APIDiffs`,
discriminated on `notificationType`. Retries and payload signing are not documented — assume
neither.

> APIClarity was archived read-only on 2026-05-29; the last release was v0.14.5 (2023-05-05).

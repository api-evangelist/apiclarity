---
name: apiclarity-reconstruct-and-approve-a-spec
description: Turn observed traffic into an approved OpenAPI specification for an API APIClarity has discovered.
api: APIClarity Core API
base: /api (relative — the host is your own deployment)
operations:
  - GET /apiInventory
  - GET /apiInventory/apiId/fromHostAndPort
  - POST /modules/specreconstructor/{apiID}/start
  - POST /modules/specreconstructor/{apiID}/stop
  - GET /apiInventory/{apiId}/suggestedReview
  - POST /apiInventory/{reviewId}/approvedReview
  - GET /apiInventory/{apiId}/reconstructed_swagger.json
operation_ids:
  - specreconstructorPostAPIIDStart
  - specreconstructorPostAPIIDStop
source: openapi/_original/apiclarity-global-openapi.gen.yml
generated: '2026-09-04'
method: generated
---

# Reconstruct and approve an OpenAPI specification

APIClarity's headline capability. You point it at traffic, it proposes a specification, a human
approves the path parameterisation, and you get an OpenAPI document for an API that never had one.

**Before you start.** APIClarity runs in your own cluster. There is no vendor host — the
specification declares `servers: [{url: /api}]`, so substitute your own. The documented local
path is `kubectl port-forward -n apiclarity svc/apiclarity-apiclarity 9999:8080`, making the
base `http://localhost:9999/api`. The management API declares no securityScheme; whatever
authentication sits in front of it is your ingress, not APIClarity's.

## 1. Find the API

`GET /apiInventory` requires `page`, `pageSize` and `sortKey` — they are declared required, not
optional. Filter with the bracketed operators, e.g. `name[contains]`.

    GET /apiInventory?page=1&pageSize=50&sortKey=name&sortDir=ASC&name[contains]=catalogue

If you already know the host and port, resolve it directly:

    GET /apiInventory/apiId/fromHostAndPort?host=catalogue&port=80

That returns 404 "API ID Not Found" if APIClarity has not observed the API yet. A 404 here means
generate traffic, not retry.

## 2. Start reconstruction

    POST /modules/specreconstructor/{apiID}/start        # specreconstructorPostAPIIDStart

Returns 204. Reconstruction quality is a function of traffic coverage — exercise the endpoints
you care about before moving on. Stop it when you have enough:

    POST /modules/specreconstructor/{apiID}/stop         # specreconstructorPostAPIIDStop

Start and stop are the reversal pair for this flow. Neither states a window, and nothing is
undone by stopping — the traffic already learned stays learned.

## 3. Review the suggested parameterisation

    GET /apiInventory/{apiId}/suggestedReview

Returns a `SuggestedReview` with `id` and `reviewPathItems[]`, each pairing a `suggestedPath`
(e.g. `/orders/{orderId}`) with the concrete `apiEventsPaths` it was inferred from. **This step
exists because the inference is a guess.** APIClarity cannot tell an identifier segment from a
literal one without you. Read the concrete paths before accepting the suggestion.

## 4. Approve

    POST /apiInventory/{reviewId}/approvedReview

Note the path parameter is the **reviewId** from step 3, not the apiId.

**There is no un-approve.** No operation reverses this, no retention window is stated, and the
API has no idempotency key — POSTing twice is two approvals, not one. If an agent runs this
flow, put the gate here.

## 5. Fetch the result

    GET /apiInventory/{apiId}/reconstructed_swagger.json

Returns the reconstructed OpenAPI document itself. `GET /apiInventory/{apiId}/specs` returns
both the provided and reconstructed specs side by side.

To replace the reconstruction with a spec you already have:

    PUT /apiInventory/{apiId}/specs/providedSpec

400 "Spec validation failure" means the document did not validate — fix it before retrying.

## Errors

Every failure is `{"message": "..."}` (schema `ApiResponse`), media type `application/json`, not
RFC 9457. Most operations on this flow declare only a `default` catch-all, so read the message;
there is no code to switch on. See `errors/apiclarity-problem-types.yml`.

## What you will be notified about

If you have registered a notification listener, this flow emits `NewDiscoveredAPINotification`
when the API first appears and `SpecDiffsNotification` when observed traffic later diverges from
the approved spec. See `asyncapi/apiclarity-notifications-webhooks.yml`.

> APIClarity was archived read-only on 2026-05-29; the last release was v0.14.5 (2023-05-05).
> These operations are accurate against the published specifications, but nothing is maintained.

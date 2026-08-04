# Veriff (veriff-com)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Veriff is a global identity verification platform that combines AI and human review to verify people online. Its API-first IDV stack covers document and biometric (face-match, liveness) verification, KYC/AML onboarding, proof of address, and database/watchlist (PEP and sanctions) screening, orchestrated around verification sessions with HMAC-secured REST endpoints and decision/event webhooks.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/veriff-com/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/veriff-com/refs/heads/main/apis.yml)

## Authentication

Every request carries `X-AUTH-CLIENT` (your integration's public API key) and `X-HMAC-SIGNATURE` (a hex-encoded HMAC-SHA256 signature). POST/PATCH sign the raw payload body; GET/DELETE sign the resource ID (for example the session ID). `POST /sessions` requires only `X-AUTH-CLIENT`. Retrieve your exact base URL and shared secret from the Veriff Customer Portal.

## Tags

- Identity Verification
- KYC
- AML
- Biometrics
- Document Verification
- Fraud Prevention

## Timestamps

- **Created:** 2026-07-01
- **Modified:** 2026-07-01

## APIs

### Veriff Sessions API

Creates verification sessions that give an end-user a hosted or in-context flow to verify identity. Supports vendorData/endUserData correlation, callback URLs, session submission (PATCH) and deletion (DELETE).

- **Human URL:** [https://devdocs.veriff.com/docs/how-to-generate-sessions-manually](https://devdocs.veriff.com/docs/how-to-generate-sessions-manually)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- Sessions
- Identity Verification
- Onboarding

#### Properties

- [Documentation](https://devdocs.veriff.com/docs/how-to-generate-sessions-manually)
- [API Reference](https://devdocs.veriff.com/apidocs/v1sessions)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/veriff-com.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/veriff-com.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Veriff Decisions API

Retrieves the verification decision for a session — status (approved, declined, resubmission_requested, expired, abandoned, review), extracted document and person data, insights, and risk labels.

- **Human URL:** [https://devdocs.veriff.com/apidocs/v1sessionsiddecision-1](https://devdocs.veriff.com/apidocs/v1sessionsiddecision-1)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- Decisions
- Verifications
- Results

#### Properties

- [API Reference](https://devdocs.veriff.com/apidocs/v1sessionsiddecision-1)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/veriff-com.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/veriff-com.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Veriff Person API

Returns the verified person object for a session — name, date of birth, nationality/citizenship, gender, and identifiers extracted from the verification.

- **Human URL:** [https://devdocs.veriff.com/apidocs/veriff-public-api-guides](https://devdocs.veriff.com/apidocs/veriff-public-api-guides)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- Person
- Extracted Data
- PII

#### Properties

- [API Reference](https://devdocs.veriff.com/apidocs/veriff-public-api-guides)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/veriff-com.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/veriff-com.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Veriff Media API

Uploads document, face, and NFC media into a session and retrieves media metadata and individual image files by session, attempt, or media ID for server-to-server integrations.

- **Human URL:** [https://devdocs.veriff.com/apidocs/v1sessionsidmedia-3](https://devdocs.veriff.com/apidocs/v1sessionsidmedia-3)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- Media
- Images
- Document Upload

#### Properties

- [API Reference](https://devdocs.veriff.com/apidocs/v1sessionsidmedia-3)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/veriff-com.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/veriff-com.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Veriff Watchlist Screening API

Queries the AML watchlist-screening result for a session — Politically Exposed Persons (PEP), sanctions, and adverse-media matches with hit details.

- **Human URL:** [https://devdocs.veriff.com/apidocs/veriff-public-api-guides](https://devdocs.veriff.com/apidocs/veriff-public-api-guides)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- AML
- Watchlist
- PEP
- Sanctions

#### Properties

- [API Reference](https://devdocs.veriff.com/apidocs/veriff-public-api-guides)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/veriff-com.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/veriff-com.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Veriff Attempts API

Lists the individual verification attempts made within a session and exposes the media captured on each attempt.

- **Human URL:** [https://devdocs.veriff.com/apidocs/veriff-public-api-guides](https://devdocs.veriff.com/apidocs/veriff-public-api-guides)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- Attempts
- Sessions

#### Properties

- [API Reference](https://devdocs.veriff.com/apidocs/veriff-public-api-guides)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/veriff-com.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/veriff-com.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Veriff Webhooks API

Server-to-server Decision and Event webhooks (callbacks) that Veriff POSTs to your endpoint as a verification progresses and concludes, each signed with `x-auth-client` and an `x-hmac-signature` over the payload body.

- **Human URL:** [https://devdocs.veriff.com/docs/webhooks-guide](https://devdocs.veriff.com/docs/webhooks-guide)
- **Base URL:** `https://stationapi.veriff.com/v1`

#### Tags

- Webhooks
- Callbacks
- Events

#### Properties

- [Documentation](https://devdocs.veriff.com/docs/webhooks-guide)
- [OpenAPI](openapi/veriff-com-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [GitHub Organization](https://github.com/veriff)
- [LinkedIn](https://www.linkedin.com/company/veriff)
- [Website](https://www.veriff.com)
- [Documentation](https://devdocs.veriff.com)
- [Plans](plans/veriff-com-plans-pricing.yml)
- [Rate Limits](rate-limits/veriff-com-rate-limits.yml)
- [Fin Ops](finops/veriff-com-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

# Qase (qase)

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

Qase is a cloud test management platform (TestOps) for QA and engineering teams to author test cases, organize them into suites and plans, launch and complete test runs, publish automated results from CI pipelines, and track defects. The **Qase TestOps API v1** is a token-authenticated REST API at `https://api.qase.io/v1` covering Projects, Test Cases, Suites, Test Runs, Test Results, Defects, and Plans. Qase publishes a machine-readable OpenAPI source specification on GitHub ([qase-tms/specs](https://github.com/qase-tms/specs)) and pre-generated clients for PHP, Python, JavaScript/TypeScript, Java, and Go. A newer **v2** API is also published.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/qase/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/qase/refs/heads/main/apis.yml)

## Access Model

- **Public, documented REST API.** Full reference at [developers.qase.io](https://developers.qase.io); base URL `https://api.qase.io/v1`.
- **Authentication:** an API token (personal or application) passed in the `Token` header on every request over HTTPS. Access is further constrained by the user's role-based permissions.
- **Availability:** the API is included on **every** plan, including the free tier. The Free plan caps API-published results at 25,000 per month; higher tiers raise or remove that cap.
- **Rate limits:** 1,000 requests/minute per user (token) and 3,000 requests/minute per IP; HTTP 429 on exceed.
- **No public WebSocket API.** Qase's own surface is request/response REST plus outbound webhooks. See `review.yml`.
- **Not open source (the platform),** but the API spec, clients, and framework reporters are open on GitHub under [qase-tms](https://github.com/qase-tms).

## Tags

- Test Runs
- Test Management
- Test Cases
- QA
- Testing
- TestOps
- Test Results
- Defects
- Quality Assurance
- Test Automation

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Qase Test Runs API

Create, list, retrieve, update, delete, and complete test runs in a project, and toggle a public shareable report link. A test run is an execution of a selected set of test cases; filter runs by status (in_progress, passed, failed, aborted), milestone, environment, and start-time window. Endpoints are scoped by project code at `/run/{code}` and `/run/{code}/{id}`.

- **Human URL:** [https://developers.qase.io/reference/get-runs](https://developers.qase.io/reference/get-runs)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Test Runs
- Runs
- Test Execution
- QA

#### Properties

- [API Reference](https://developers.qase.io/reference/get-runs)
- [Documentation](https://developers.qase.io/docs/getting-started)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Qase Test Results API

Publish and manage test run results - the pass/fail/blocked/skipped outcome of each executed case. Create a single result for a run, bulk-create many results in one request (the endpoint automation reporters use to push CI results), list results across runs, and get, update, or delete a result by run id and hash at `/result/{code}`.

- **Human URL:** [https://developers.qase.io/reference/create-result](https://developers.qase.io/reference/create-result)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Test Results
- Results
- CI
- Test Automation

#### Properties

- [API Reference](https://developers.qase.io/reference/create-result)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Qase Test Cases API

Manage the test case repository - create, list, get, update, and delete test cases with titles, steps, preconditions, severity, priority, type, and suite assignment. Endpoints are scoped by project code at `/case/{code}` and `/case/{code}/{id}`.

- **Human URL:** [https://developers.qase.io/reference/get-cases](https://developers.qase.io/reference/get-cases)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Test Cases
- Cases
- Repository
- QA

#### Properties

- [API Reference](https://developers.qase.io/reference/get-cases)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Qase Test Suites API

Organize test cases into hierarchical suites. Create, list, get, update, and delete test suites, including nesting via a parent suite, at `/suite/{code}` and `/suite/{code}/{id}`.

- **Human URL:** [https://developers.qase.io/reference/get-suites](https://developers.qase.io/reference/get-suites)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Test Suites
- Suites
- Organization

#### Properties

- [API Reference](https://developers.qase.io/reference/get-suites)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Qase Projects API

Create, list, retrieve, and delete projects - the top-level containers, identified by a 2-10 character code, that hold cases, suites, runs, results, plans, and defects. Endpoints live at `/project` and `/project/{code}`.

- **Human URL:** [https://developers.qase.io/reference/get-projects](https://developers.qase.io/reference/get-projects)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Projects
- Workspaces
- Administration

#### Properties

- [API Reference](https://developers.qase.io/reference/get-projects)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Qase Defects API

Track defects raised against failed test results. List and filter defects by status, get a defect, delete it, mark it resolved, and update its status at `/defect/{code}` and related paths.

- **Human URL:** [https://developers.qase.io/reference/get-defects](https://developers.qase.io/reference/get-defects)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Defects
- Bugs
- Issue Tracking
- QA

#### Properties

- [API Reference](https://developers.qase.io/reference/get-defects)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Qase Test Plans API

Create, list, get, update, and delete test plans - reusable selections of test cases that can be launched as a test run. Endpoints live at `/plan/{code}` and `/plan/{code}/{id}`.

- **Human URL:** [https://developers.qase.io/reference/get-plans](https://developers.qase.io/reference/get-plans)
- **Base URL:** `https://api.qase.io/v1`

#### Tags

- Test Plans
- Plans
- Test Selection

#### Properties

- [API Reference](https://developers.qase.io/reference/get-plans)
- [OpenAPI](openapi/qase-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/qase.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/qase.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Authentication](authentication/qase-authentication.yml)
- [GitHub Organization](https://github.com/qase-tms)
- [LinkedIn](https://www.linkedin.com/company/qaseio)
- [Website](https://qase.io)
- [Documentation](https://developers.qase.io)
- [Plans](plans/qase-plans-pricing.yml)
- [Rate Limits](rate-limits/qase-rate-limits.yml)
- [Fin Ops](finops/qase-finops.yml)
- [Source Code](https://github.com/qase-tms/specs)
- [Blog](https://qase.io/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

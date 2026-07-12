# Qase (qase)

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

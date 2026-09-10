# Future Improvements

## Test Management

- Move canonical test cases into a dedicated test-management platform while retaining exportable Excel evidence.
- Maintain requirement, scenario, test case, execution, and defect links as controlled relationships.
- Add change history and approval fields for test case maintenance.

## Execution Evidence

- Capture browser and browser version for every cycle.
- Record application build/version where exposed.
- Add execution timestamp and tester identity to execution evidence.
- Capture screenshots automatically or manually for all failed/blocked cases.
- Store evidence using the canonical Test Case ID and Bug ID naming convention.

## Functional Coverage Expansion

The following coverage areas were identified as candidates for future expansion and were intentionally not silently added to the original 96-case baseline:

- boundary-length validation for key text fields;
- special-character and Unicode input handling;
- duplicate-record behavior;
- pagination boundary cases;
- advanced filtering combinations;
- date boundary and invalid-date handling;
- role-based negative authorization across additional modules;
- session timeout and concurrent-session scenarios;
- bulk operations where supported;
- attachment/file validation where supported;
- browser refresh/back-navigation behavior during form entry;
- direct-URL authorization checks.

## Non-Functional Coverage

Future iterations should add dedicated coverage for:

- accessibility checks aligned with WCAG principles;
- cross-browser compatibility;
- responsive layout;
- performance and response-time baselines;
- security testing beyond functional negative checks;
- API testing if endpoints are available;
- resilience and recovery behavior.

## Automation Opportunities

The strongest automation candidates are:

- valid/invalid login regression;
- employee search and CRUD verification;
- user search and CRUD verification;
- leave request/approval workflow;
- candidate creation/search workflow;
- directory search;
- session/logout verification.

Automation should reference the same canonical Test Case IDs to preserve traceability between manual and automated coverage.

## CI / Reporting

A future automated layer could:

- execute smoke tests on every deployment;
- run regression on release candidates;
- publish HTML reports;
- retain screenshots/traces on failure;
- update execution metrics;
- flag critical-path failures immediately.

## Portfolio Enhancements

- Add controlled screenshots after real re-execution.
- Add a lightweight architecture/test-flow diagram.
- Add release-specific execution snapshots rather than a single retained baseline.
- Add a defect lifecycle example showing Open → Fixed → Retest → Closed.
- Add repository-level badges and navigation in the final GitHub README.

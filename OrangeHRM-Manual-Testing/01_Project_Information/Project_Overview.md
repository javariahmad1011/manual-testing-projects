# OrangeHRM Manual QA Project Overview

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Application Under Test | OrangeHRM Demo |
| Document | Project Overview |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Primary Evidence | Supplied OrangeHRM functional regression test workbook |

## 1. Purpose

This repository records the end-to-end manual QA lifecycle for the OrangeHRM Demo application. It is structured as a release-quality QA evidence pack rather than a collection of disconnected test cases. Requirements, test planning, test design, execution, defects, closure evidence, metrics, and portfolio presentation are intended to remain traceable to one another.

The supplied test workbook is the execution baseline. Existing test intent and coverage are preserved. Naming, traceability, execution metadata, and repository structure are standardized in later deliverables without reducing the original coverage.

## 2. Current QA Baseline

The source workbook contains **96 executed functional/regression test cases** across **13 modules**. The recorded result is **92 passed, 4 failed, 0 blocked, and 0 not executed**, producing a **95.83% pass rate**.

| Module | Code | Total | Passed | Failed | Pass Rate |
|---|---:|---:|---:|---:|---:|
| Login | `LGN` | 12 | 11 | 1 | 91.7% |
| Forgot Password | `FGP` | 5 | 4 | 1 | 80.0% |
| Dashboard | `DSH` | 5 | 5 | 0 | 100.0% |
| Admin | `ADM` | 10 | 10 | 0 | 100.0% |
| PIM | `PIM` | 16 | 16 | 0 | 100.0% |
| Leave | `LEV` | 10 | 10 | 0 | 100.0% |
| Time | `TIM` | 8 | 8 | 0 | 100.0% |
| Recruitment | `REC` | 8 | 7 | 1 | 87.5% |
| My Info | `MYI` | 6 | 5 | 1 | 83.3% |
| Performance | `PRF` | 5 | 5 | 0 | 100.0% |
| Directory | `DIR` | 4 | 4 | 0 | 100.0% |
| Buzz | `BUZ` | 3 | 3 | 0 | 100.0% |
| Session | `SES` | 4 | 4 | 0 | 100.0% |

Priority distribution recorded in the baseline is **44 High**, **37 Medium**, and **15 Low**.

The four failed source cases are retained as unresolved execution findings until the dedicated defect-management deliverables are produced:

- `TC-LGN-012` — credential case-sensitivity behavior.
- `TC-FGP-003` — password reset request behavior for an unregistered username.
- `TC-REC-005` — invalid candidate email format validation.
- `TC-MYI-004` — ESS restriction for Job/Salary editing.

The supplied workbook does not contain detailed Actual Result text, defect IDs, screenshots for those failures, a formal product build identifier, or a vendor-authored requirements specification. Those gaps are explicitly managed in this repository rather than backfilled with invented evidence.

## 3. Application Areas Covered

The current baseline covers authentication, password recovery, dashboard navigation and widgets, system-user administration, employee lifecycle data, leave processing, time and attendance, recruitment, self-service employee information, performance, directory search, social feed behavior, and session controls.

Functional scope is defined in [Application Scope](./Application_Scope.md). Test-derived requirements are catalogued in [Requirement Analysis](./Requirement_Analysis.md).

## 4. QA Operating Model

The project follows a controlled traceability chain:

`Requirement → Test Scenario → Test Case → Execution Result → Defect (when applicable) → Retest/Regression → Closure Evidence`

This chain is implemented across the planned repository artifacts:

- Requirements and scope: `01_Project_Information`
- Planning, risk, estimation, environment, and RTM: `02_Test_Planning`
- Functional and release test suites: `03_Test_Design`
- Execution evidence, test data, and defect log: `04_Test_Execution`
- Individual defect reports: `05_Defect_Reports`
- Closure, metrics, limitations, and lessons learned: `06_Test_Closure`

## 5. Identifier Standard

Canonical identifiers use a stable three-part convention:

- Requirement: `RQ-<MODULE>-###`
- Test Scenario: `TS-<MODULE>-###`
- Test Case: `TC-<MODULE>-###`
- Defect: `BUG-###`

The current workbook uses legacy prefixes such as `TC_LOGIN_001`. These source IDs are not discarded. During the Functional Test Cases deliverable they will be normalized to canonical IDs while preserving a source-to-canonical mapping for auditability.

Module codes are defined in [Requirement Analysis](./Requirement_Analysis.md).

## 6. Test Approach

The existing suite is primarily functional regression coverage with positive, negative, validation, authorization, navigation, data-management, and basic security-oriented checks. Later planning artifacts will classify tests into smoke, sanity, regression, high-priority, and critical-path suites without duplicating or weakening the functional source coverage.

No claim is made here that the portfolio reproduces OrangeHRM's internal vendor QA process. This repository documents the QA process applied to the deployed Demo application as an external black-box system.

## 7. Quality Gates

The project will use the following release-style gates when later execution and closure artifacts are produced:

1. All Critical Path tests executed.
2. All High-priority tests executed or explicitly waived with rationale.
3. No unresolved Critical/Blocker defect at closure.
4. Every failed test case linked to a defect, accepted limitation, or documented expectation mismatch.
5. Retests and relevant regression executed after fixes.
6. RTM status reconciled with the final execution report.
7. Closure metrics reconcile to the test execution dataset.

These are repository quality gates, not claims about OrangeHRM vendor release criteria.

## 8. Assumptions and Constraints

The baseline is based on the public/demo application behavior represented by the supplied cases. Formal backend contracts, database access, production logs, vendor requirements, and deployment pipeline data are not available in the current evidence set. A build version will remain `Not provided / Demo environment` until a verifiable build identifier is available.

Where a failed test may reflect ambiguous expected behavior rather than a confirmed product defect, the finding will remain in triage until requirement intent is validated. This is particularly relevant to case sensitivity, account-enumeration messaging, role permissions, and any demo-specific limitations.

## 9. Related Documents

- [Requirement Analysis](./Requirement_Analysis.md)
- [Application Scope](./Application_Scope.md)
- [STLC](./STLC.md)
- [SDLC](./SDLC.md)
- [Test Objectives](./Test_Objectives.md)
- Planned: `../02_Test_Planning/Test_Plan.md`
- Planned: `../02_Test_Planning/Requirement_Traceability_Matrix.xlsx`
- Planned: `../03_Test_Design/Functional_Test_Cases/`
- Planned: `../04_Test_Execution/Test_Execution_Report.xlsx`
- Planned: `../06_Test_Closure/Test_Summary_Report.md`

## 10. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Initial project-information baseline created from supplied functional regression evidence. | Quality Assurance |

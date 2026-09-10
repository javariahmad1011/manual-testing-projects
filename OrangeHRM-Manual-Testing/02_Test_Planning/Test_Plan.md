# OrangeHRM Manual Testing — Test Plan

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Test Plan |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Test Basis | 96-case OrangeHRM functional regression baseline and 91 test-derived requirements |

## 1. Purpose

This Test Plan defines the controls for a repeatable manual QA cycle against the OrangeHRM Demo application. It converts the supplied execution snapshot into a managed release-style test process with controlled scope, traceability, environment readiness, defect handling, reporting, retest, regression, and closure gates.

The plan is governed by `01_Project_Information/Requirement_Analysis.md`, `Application_Scope.md`, `STLC.md`, and `Test_Objectives.md`. The supplied 96 test cases remain the coverage baseline; planning activities do not remove or reinterpret those cases.

## 2. Test Basis and Baseline

| Baseline Item | Current Position |
|---|---:|
| Functional modules | 13 |
| Test-derived requirements | 91 |
| Existing test cases | 96 |
| High-priority cases | 44 |
| Medium-priority cases | 37 |
| Low-priority cases | 15 |
| Passed in supplied execution snapshot | 92 |
| Failed in supplied execution snapshot | 4 |
| Source pass rate | 95.83% |

The four failed cases are carried forward as unresolved QA findings until actual behavior, requirement intent, and reproducibility are captured during controlled execution. A failed source case is not automatically treated as a confirmed product defect.

## 3. Test Scope

### In scope

Manual UI validation across:

- Login and Forgot Password
- Dashboard
- Admin
- PIM
- Leave
- Time
- Recruitment
- My Info
- Performance
- Directory
- Buzz
- Session Management

Coverage includes positive flows, negative validation, CRUD operations, search/filter behavior, selected role restrictions, file upload, workflow status changes, logout/session controls, and basic protected-route checks already represented by the source suite.

### Out of scope

API contract testing, direct database validation, performance/load testing, penetration testing, accessibility certification, native mobile testing, infrastructure/deployment validation, full localization coverage, production-data validation, and a complete authorization matrix are outside the current committed baseline. See `01_Project_Information/Application_Scope.md` for the controlled boundary.

## 4. Test Objectives

The cycle will:

1. Preserve 100% traceability for all 96 existing cases.
2. Validate the 91 test-derived requirements represented by the source suite.
3. Execute critical business flows before broad regression.
4. Record actual results, status, browser, environment, execution date, build/version identifier where available, executor, and comments for every executed case.
5. Raise a controlled defect or other formal disposition for every reproducible failed case.
6. Retest fixes and run impacted sanity/regression coverage.
7. Reconcile RTM, execution, defect, and closure metrics before a release-style recommendation.

Detailed measurable objectives are maintained in `01_Project_Information/Test_Objectives.md`.

## 5. Test Approach

Execution will follow this sequence:

`Environment readiness → Smoke → Functional/Regression execution → Defect triage → Fix/retest → Sanity → Impacted regression → Critical-path confirmation → Closure`

Risk and priority determine execution order. High-priority authentication, employee, user-administration, leave, recruitment, time, and session workflows are executed before lower-risk reporting/social behavior.

The detailed approach, techniques, suite-selection rules, evidence standard, and severity/priority model are defined in `Test_Strategy.md`.

## 6. Planned Test Deliverables

| Stage | Deliverable | Purpose |
|---|---|---|
| Project Information | `01_Project_Information/*` | Requirement, scope, lifecycle, and objective baseline |
| Test Planning | `02_Test_Planning/Test_Plan.md` | Master test controls |
| Test Planning | `02_Test_Planning/Test_Strategy.md` | Execution and coverage strategy |
| Test Planning | `02_Test_Planning/Test_Environment.md` | Environment/readiness control |
| Test Planning | `02_Test_Planning/Test_Estimation.md` | Effort and schedule basis |
| Test Planning | `02_Test_Planning/Risk_Assessment.md` | Quality and execution risk register |
| Test Planning | `02_Test_Planning/Requirement_Traceability_Matrix.xlsx` | Requirement → scenario → case → status traceability |
| Test Design | `03_Test_Design/Functional_Test_Cases/` | Standardized executable cases |
| Test Design | Smoke/Regression/Sanity/Critical Path suites | Risk-based release subsets |
| Test Execution | `04_Test_Execution/*` | Actual execution, data, evidence, and defects |
| Defect Management | `05_Defect_Reports/*` | Reproducible defect records |
| Closure | `06_Test_Closure/*` | Metrics, residual risk, and recommendation |

The RTM created in this planning phase establishes the traceability baseline. It will be reconciled again after Functional Test Cases and execution artifacts are finalized.

## 7. Entry Criteria

Broad regression execution may start only when:

- Target OrangeHRM Demo endpoint is reachable.
- Required Admin and ESS-capable accounts are available.
- Core navigation loads without an environment-wide blocker.
- Required test data can be created or identified.
- Upload fixtures are available for image, resume, and document scenarios.
- Test cases and expected results are baselined.
- The execution cycle identifier and environment details have been recorded.
- Smoke suite has no unresolved blocker that prevents meaningful regression.

If a criterion cannot be met, execution may proceed only for unaffected scope and the dependency must be logged.

## 8. Exit Criteria

The controlled test cycle is ready for closure when:

- 100% of planned Critical Path cases are executed.
- 100% of planned High-priority cases are executed or formally dispositioned.
- All remaining planned cases are executed, blocked with rationale, or explicitly deferred by scope decision.
- Every failure has a controlled defect, accepted limitation, or requirement clarification.
- Fixed defects have retest evidence.
- Required sanity and impacted regression are complete.
- No unresolved Critical/Blocker defect remains unless explicitly accepted.
- RTM status reconciles with execution status.
- Known limitations and residual risks are documented.
- Execution and closure metrics reconcile to the approved scope.

Pass percentage alone does not satisfy exit criteria.

## 9. Suspension and Resumption Criteria

Execution will be suspended for affected scope when:

- Authentication or environment access prevents the majority of test execution.
- The demo is unstable enough to invalidate repeatable results.
- Shared test data is corrupted or reset during execution.
- A blocker prevents creation of prerequisite employee/user/leave/time/recruitment data.
- A deployment/change occurs without an identifiable test baseline and materially changes expected behavior.

Execution resumes after the blocking condition is resolved, environment readiness is rechecked, and smoke coverage confirms that the build/environment is testable.

## 10. Roles and Responsibilities

| Role | Responsibility |
|---|---|
| QA Lead / Test Owner | Scope control, strategy, risk decisions, quality gates, defect triage, metrics reconciliation, closure recommendation |
| QA Engineer | Test preparation, data setup, manual execution, evidence capture, defect reporting, retest/regression updates |
| Product / Requirement Owner (where available) | Clarifies ambiguous expected behavior and accepts/rejects requirement changes |
| Engineering / Developer (where applicable) | Investigates confirmed defects and provides fixes/build information |

These are project responsibilities only; no named OrangeHRM vendor personnel are implied.

## 11. Defect Management

A failure must be reproducible before it is classified as a confirmed defect. Every formal defect will capture the test case linkage, environment, browser, build/version where available, severity, priority, prerequisites, steps, actual result, expected result, status, owner, reporter, and date.

Planned workflow:

`New → Triaged → Assigned → In Progress → Ready for Retest → Closed`

Controlled alternatives: `Rejected`, `Duplicate`, `Cannot Reproduce`, `Deferred`, `Accepted Limitation`.

Severity reflects impact. Priority reflects fix urgency. They are not interchangeable.

## 12. Test Data Management

Reusable data will be controlled in `04_Test_Execution/Test_Data.xlsx`. Data dependencies include system users, employees, ESS credentials, leave entitlement, leave requests, projects/activities, timesheets, candidates, vacancies, performance records, directory data, Buzz posts, and supported upload fixtures.

Test data should be uniquely identifiable where practical and cleaned up when deletion is part of the scenario. Shared-demo state must never be assumed to remain unchanged between sessions.

## 13. Environment and Configuration Control

The supplied workbook does not identify the original browser, OS, URL, build/version, or row-level execution date. These values will not be invented.

Before controlled re-execution, the exact target URL, browser/version, OS, account/role, execution date, and any visible build/release identifier will be recorded according to `Test_Environment.md`. If the demo exposes no build identifier, the execution timestamp and environment URL become the minimum reproducibility baseline.

## 14. Reporting and Communication

Execution reporting will include:

- Total planned, executed, passed, failed, blocked, and not executed.
- Execution percentage and pass percentage.
- Module-level status.
- Priority-level status.
- Open defects by severity/status.
- Blockers and environment/data issues.
- Retest/regression position.
- Residual risks and closure recommendation.

The source workbook metrics are retained as a baseline snapshot and will not be mixed with later re-execution metrics without a clearly identified cycle.

## 15. Change Control

Any change to requirement intent, scope, test coverage, or expected result requires impact analysis across:

`Requirement → Scenario → Test Case → Suite membership → Risk → Execution → Defect → Closure`

Expected results must not be changed solely to make a failing test pass.

## 16. Assumptions and Dependencies

- The OrangeHRM Demo remains accessible for manual UI testing.
- Admin-capable and ESS-capable test accounts can be obtained or created.
- Shared demo data may change independently of this test cycle.
- No formal vendor SRS/PRD has been supplied; the repository uses test-derived requirements.
- Browser/build data from the historical execution is unavailable.
- Some workflows require prerequisite data from earlier modules.
- Password reset confirmation is UI-verifiable; actual email delivery is outside the current baseline unless evidence becomes available.

## 17. Approval / Baseline Position

This plan is considered baselined for the portfolio when its scope, strategy, environment controls, estimation model, risks, and traceability baseline are mutually consistent. Later deliverables may refine execution details without silently reducing the 96-case source coverage.

## 18. Related Documents

- `../01_Project_Information/Project_Overview.md`
- `../01_Project_Information/Requirement_Analysis.md`
- `../01_Project_Information/Application_Scope.md`
- `../01_Project_Information/STLC.md`
- `../01_Project_Information/Test_Objectives.md`
- `./Test_Strategy.md`
- `./Test_Environment.md`
- `./Test_Estimation.md`
- `./Risk_Assessment.md`
- `./Requirement_Traceability_Matrix.xlsx`

## 19. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Established the controlled manual test plan for the 96-case OrangeHRM baseline. | Quality Assurance |

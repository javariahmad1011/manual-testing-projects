# OrangeHRM Software Testing Life Cycle (STLC)

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | STLC |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |

## 1. STLC Model

This project uses a traceability-driven manual testing lifecycle. The STLC is applied to the OrangeHRM Demo as an externally deployed application; QA evidence is controlled within this repository.

`Requirement Analysis → Test Planning → Test Design → Environment & Data Readiness → Test Execution → Defect Management → Retest & Regression → Test Closure`

## 2. Lifecycle Stages and Repository Evidence

| Stage | Entry Inputs | QA Activities | Controlled Outputs | Repository Evidence |
|---|---|---|---|---|
| 1. Requirement Analysis | Supplied test baseline, observed application behavior, known module scope | Derive testable requirements, identify ambiguity, map source coverage, record gaps without silently adding tests | Requirement catalogue, scope baseline, assumptions, coverage gaps | `01_Project_Information/Requirement_Analysis.md`, `Application_Scope.md` |
| 2. Test Planning | Approved scope and requirements | Define strategy, test levels/types, resources, environment, estimation, risks, entry/exit criteria | Test Plan, Strategy, Environment, Estimation, Risk Assessment | `02_Test_Planning/` |
| 3. Test Design | Requirements, risks, source test cases | Standardize test IDs and columns, improve steps/expected results, assign requirement/scenario IDs, derive release suites | Functional cases, smoke, regression, sanity, critical-path, high-priority suites | `03_Test_Design/` |
| 4. Environment & Data Readiness | Test Plan, Test Environment definition, test data needs | Confirm access, roles, browser/environment, reusable data, upload files, data dependencies | Environment readiness and controlled test data | `02_Test_Planning/Test_Environment.md`, `04_Test_Execution/Test_Data.xlsx` |
| 5. Test Execution | Approved test suite and ready environment | Execute, capture actual results, status, browser/build/date/executor/comments, evidence | Execution dataset and summary | `04_Test_Execution/Test_Execution_Report.xlsx`, `Execution_Summary.xlsx`, screenshots |
| 6. Defect Management | Failed execution evidence | Reproduce, classify Severity/Priority, document expected vs actual, assign, track status | Defect Log and individual bug reports | `04_Test_Execution/Defect_Log.xlsx`, `05_Defect_Reports/` |
| 7. Retest & Regression | Fix/build or accepted clarification | Retest resolved defects, run impacted sanity/regression/critical path, update status | Retest result and regression evidence | `03_Test_Design/Sanity_Test_Suite.xlsx`, `Regression_Test_Suite.xlsx`, execution reports |
| 8. Test Closure | Reconciled execution, defects, RTM, risks | Validate exit criteria, reconcile metrics, document limitations/lessons/future work | Summary, metrics, limitations, lessons learned | `06_Test_Closure/` |

## 3. Requirement Analysis Exit Criteria

Requirement Analysis is complete when:

- Functional scope is defined.
- Every existing source test can be tied to a test-derived requirement.
- Ambiguous expectations are explicitly flagged.
- Missing edge cases are recorded separately from existing coverage.
- Identifier conventions are established.
- No unsupported product behavior is presented as a confirmed requirement.

The current [Requirement Analysis](./Requirement_Analysis.md) maps all 96 source tests.

## 4. Test Planning Exit Criteria

Planning will be considered ready when the following are baselined:

- Test Plan and Test Strategy.
- Test Environment.
- Estimation.
- Risk Assessment.
- RTM structure.
- Entry and exit criteria.
- Defect Severity/Priority model.
- Execution ownership and evidence expectations.

## 5. Test Design Exit Criteria

Test design will be complete when:

- All 96 source cases are standardized without coverage reduction.
- Required professional columns are present.
- Canonical Requirement, Scenario, and Test Case IDs are applied.
- Steps, data, preconditions, and expected results are executable and unambiguous.
- Smoke, regression, sanity, high-priority, and critical-path subsets reference canonical test cases.
- Any approved new edge cases are clearly identified as additions rather than source rewrites.

## 6. Execution Status Model

Standard execution status values will be:

- `Not Executed`
- `Pass`
- `Fail`
- `Blocked`

A case is **Pass** only when the observed result satisfies the expected result. A case is **Fail** when a reproducible discrepancy exists. A case is **Blocked** when execution cannot be completed because of an environmental, data, dependency, access, or upstream issue. `Not Executed` is reserved for cases not started in the execution cycle.

## 7. Defect Workflow

The planned defect workflow is:

`New → Triaged → Assigned → In Progress → Ready for Retest → Closed`

Alternative terminal/control states may include `Rejected`, `Duplicate`, `Cannot Reproduce`, `Deferred`, or `Accepted Limitation`, but each requires rationale.

A failed test must not be marked passed because a defect was raised. The test remains failed for that execution until a successful retest is recorded.

## 8. Retest and Regression Rules

- Retest validates the specific defect fix against the failing case.
- Sanity validates the affected area and immediate dependencies.
- Regression validates risk-selected unaffected and impacted functions.
- Critical Path validates release-essential business workflows.
- The RTM and Execution Report are updated from the same canonical case IDs to prevent metric drift.

## 9. Test Closure Gates

Closure requires:

- Execution totals reconcile to the approved scope.
- All failed cases have a disposition.
- Retest results are recorded for fixed defects.
- No unresolved Critical/Blocker defect unless formally accepted.
- RTM status matches execution status.
- Known limitations are documented.
- Metrics are reproducible from execution data.
- Lessons learned and future improvements are recorded.

See [Test Objectives](./Test_Objectives.md) for measurable project outcomes and `../06_Test_Closure/Test_Summary_Report.md` for the future closure decision.

## 10. Baseline Position

The supplied workbook represents an existing regression execution snapshot: **96 total, 92 pass, 4 fail**. The repository is now formalizing the upstream requirement/planning controls and downstream defect/closure evidence around that source result.

The four failures will not be converted into formal bugs until actual observed behavior and requirement intent are sufficiently captured.

## 11. Related Documents

- [Project Overview](./Project_Overview.md)
- [Requirement Analysis](./Requirement_Analysis.md)
- [Application Scope](./Application_Scope.md)
- [SDLC](./SDLC.md)
- [Test Objectives](./Test_Objectives.md)

## 12. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Defined repository STLC, evidence gates, defect flow, and closure controls. | Quality Assurance |

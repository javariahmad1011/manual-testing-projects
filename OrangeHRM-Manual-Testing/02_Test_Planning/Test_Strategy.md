# OrangeHRM Manual Testing — Test Strategy

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Test Strategy |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Strategy Type | Risk-based manual functional and regression testing |

## 1. Strategy Statement

The OrangeHRM test strategy uses risk-based manual testing against the 96-case source baseline. Functional coverage is organized around requirement traceability, business criticality, workflow dependencies, and failure impact rather than equal-weight execution.

The strategy deliberately separates source evidence from planned controls. The historical workbook shows 92 Pass and 4 Fail, but it does not contain sufficient actual-result, build, browser, or environment detail to classify all four findings as confirmed defects. Controlled re-execution will close that evidence gap.

## 2. Quality Risk Focus

The highest testing emphasis is placed on:

- Authentication and protected-session behavior.
- System-user administration and role-sensitive access.
- Employee record creation, maintenance, search, and deletion.
- Leave submission and approval/rejection workflow.
- Timesheet, attendance, and approval workflow.
- Recruitment candidate/vacancy lifecycle.
- ESS access restrictions and self-service data changes.
- Data integrity across dependent workflows.

Dashboard visualizations, Directory, Performance reporting, and Buzz remain in regression scope but carry lower release risk than authentication, employee, administration, leave, time, recruitment, and session controls.

## 3. Test Levels and Types

| Test Type | Purpose | Source/Planned Coverage |
|---|---|---|
| Functional | Validate observable UI behavior against test-derived requirements | All 96 baseline cases |
| Positive | Confirm supported business flows with valid data | Broad baseline coverage |
| Negative | Validate invalid credentials, mandatory fields, malformed data, invalid date ranges, and authorization expectations | Existing source cases plus approved future additions |
| Smoke | Confirm the environment supports critical business workflows before broad execution | 20–30 canonical cases in later Smoke Suite |
| Regression | Validate important functionality across all in-scope modules | 70–100 canonical cases in later Regression Suite |
| Sanity | Verify changed/fixed functionality and immediate dependencies | Small impact-based suite after fixes |
| Critical Path | Validate release-essential end-to-end workflows | Small business-critical subset |
| Role/Permission | Validate Admin/ESS behavior where requirement evidence exists | Admin, My Info, Leave/Time approval, protected access |
| Session/Access Control | Validate logout, browser-back, timeout, and protected URLs | Session baseline |
| File Upload | Validate supported employee image, document, and resume uploads | PIM/Recruitment/My Info |
| Basic security-oriented functional checks | Validate rejection of represented malicious/unauthorized input patterns | Login SQL-injection-style case and session access checks |

Performance, penetration, accessibility certification, API/database, and infrastructure testing are not claimed by this strategy.

## 4. Test Design Techniques

Existing source tests will be preserved and normalized. Improvements may make cases more executable but will not silently change coverage.

Techniques applied during standardization include:

- Equivalence partitioning for valid/invalid field classes.
- Boundary analysis where field/date limits are known or observable.
- Decision-table thinking for permissions and workflow states.
- State-transition coverage for leave, timesheets, recruitment, and sessions.
- CRUD lifecycle coverage for users/employees/candidates/vacancies.
- Negative/error-guessing checks for mandatory fields and malformed input.
- Risk-based prioritization for suite selection.
- Traceability analysis to identify untested or multiply-covered requirements.

Missing edge cases already identified in `01_Project_Information/Requirement_Analysis.md` remain separate candidates until explicitly approved.

## 5. Priority Model

The source priority baseline is retained:

| Priority | Source Count | Execution Intent |
|---|---:|---|
| High | 44 | Execute first; primary smoke/regression/critical-path candidates |
| Medium | 37 | Execute after high-risk flows; include based on module/change impact |
| Low | 15 | Execute in full regression where time/environment permits; lower release weight |

Priority is attached to the test case/business need. Defect Severity is assigned separately based on observed impact.

## 6. Defect Severity Model

| Severity | Definition | Typical OrangeHRM Example |
|---|---|---|
| Critical / Blocker | Prevents use of a release-essential area, causes broad access/security/data-loss risk, or blocks most testing | Valid users cannot authenticate; protected pages accessible without authentication; core environment unusable |
| High / Major | Major business workflow fails with no reasonable workaround | Cannot create employee/system user, cannot submit/approve required workflow, unauthorized role can edit restricted data |
| Medium | Functional issue with limited impact or available workaround | Filter/validation/status behavior incorrect but core workflow remains usable |
| Low / Minor | Cosmetic, low-impact, or non-blocking issue | Non-critical text/layout/secondary display discrepancy |

Formal defects will use the terminology selected in `Defect_Log.xlsx`; the impact definitions above remain the decision basis.

## 7. Defect Priority Model

| Priority | Definition |
|---|---|
| P1 | Fix immediately; release/test continuation is at risk |
| P2 | Fix before release or before affected workflow is accepted |
| P3 | Fix when scheduled; workaround or limited impact exists |
| P4 | Low urgency; backlog/cosmetic improvement |

Severity and Priority may differ. A high-severity defect can be deferred for business reasons, and a lower-severity defect can be high priority if it blocks a visible acceptance criterion.

## 8. Suite Selection Strategy

### Smoke

Smoke selects only functions required to prove the environment is testable: authentication, dashboard, critical user/employee CRUD, leave, time, recruitment, directory, and logout/session.

### Regression

Regression contains the important positive, negative, CRUD, search/filter, workflow, permission, and session behaviors across all 13 modules. Duplicate-value cases are avoided where they add no regression signal.

### Sanity

Sanity is change-driven. A fix is tested by:

`Failed case retest + direct dependency + same-feature negative/positive pair + one upstream/downstream business check where relevant`

### Critical Path

Critical Path contains the smallest set of business workflows whose failure would materially undermine release confidence. It is not a second regression suite.

Suite membership will reference canonical `TC-XXX-###` identifiers rather than copy divergent test definitions.

## 9. Execution Ordering

Within a test cycle:

1. Environment/access check.
2. Smoke suite.
3. High-priority functional/regression.
4. Medium-priority regression.
5. Low-priority regression.
6. Defect retest as fixes become available.
7. Sanity around fixes.
8. Impacted regression.
9. Final Critical Path confirmation where release gating is required.
10. Metrics reconciliation and closure.

Dependent workflows should use controlled data created earlier in the same cycle where practical.

## 10. Test Data Strategy

Test data must be:

- Clearly identifiable as QA/demo data.
- Reusable where stability is needed.
- Unique where duplicate constraints are under test.
- Created before dependent workflow execution.
- Cleaned up where the test explicitly verifies deletion.
- Recorded in `04_Test_Execution/Test_Data.xlsx`.

Data dependencies are particularly important for employee → ESS user → leave/time/My Info flows and vacancy → candidate → recruitment status flows.

Shared demo data is treated as volatile. Searches and counts should validate targeted records rather than assume fixed global totals.

## 11. Environment Strategy

The exact browser, OS, URL, and build/version used in the original 92/4 execution are unknown. Controlled re-execution will establish a named environment record before results are considered reproducible.

A single primary supported browser is sufficient for the core portfolio cycle unless cross-browser execution is explicitly added. Additional browser runs must be recorded as separate execution evidence, not implied from one run.

See `Test_Environment.md`.

## 12. Evidence Standard

For each executed case, the standardized artifact will capture:

- Requirement ID
- Test Case ID
- Module and Feature
- Preconditions
- Steps and Test Data
- Expected Result
- Actual Result
- Priority
- Severity where relevant to failure
- Status
- Executed By
- Execution Date
- Environment
- Browser
- Build Version
- Comments

Screenshots are required for failures and strongly recommended for ambiguous validation/permission behavior. A screenshot does not replace a written Actual Result.

## 13. Failure Triage Strategy

For a failed test:

1. Reproduce once with controlled data.
2. Confirm prerequisites and environment health.
3. Compare observed behavior to the test-derived requirement.
4. Check whether the expectation is ambiguous or unsupported by available product evidence.
5. Capture Actual Result and evidence.
6. Classify as defect, environment/data issue, requirement clarification, accepted limitation, or test correction.
7. Maintain the original execution result; do not overwrite history.
8. Retest against the identified fix/change and run impact-based sanity/regression.

The four source failures requiring this process are `TC-LGN-012`, `TC-FGP-003`, `TC-REC-005`, and `TC-MYI-004`.

## 14. Regression Impact Analysis

Regression scope expands based on:

- Shared page/component impact.
- Common validation or authentication change.
- Data/entity dependency.
- Role/permission dependency.
- Workflow state dependency.
- Module navigation impact.
- Defect recurrence risk.
- Historical failure area.

A fix to authentication, authorization, employee identity, or shared navigation has broader regression impact than an isolated Buzz presentation issue.

## 15. Traceability and Metric Control

`Requirement_Traceability_Matrix.xlsx` is the canonical planning bridge between requirement, scenario, test case, and status. Later Functional Test Cases, suite workbooks, execution reports, defects, and closure documents must use the same IDs.

No separate suite may redefine the expected result of a canonical test case.

Metrics are calculated from controlled execution data. Historical 92/4 metrics remain clearly labeled as the supplied source baseline.

## 16. Quality Gates

A release-style QA recommendation is withheld when:

- Smoke is blocked.
- A Critical/Blocker defect remains unresolved without explicit acceptance.
- Critical Path is incomplete.
- High-priority execution is materially incomplete.
- Failures lack disposition/evidence.
- RTM and execution totals do not reconcile.
- Environment/build identity is insufficient to reproduce the result.

## 17. Related Documents

- `Test_Plan.md`
- `Test_Environment.md`
- `Test_Estimation.md`
- `Risk_Assessment.md`
- `Requirement_Traceability_Matrix.xlsx`
- `../01_Project_Information/Requirement_Analysis.md`
- `../01_Project_Information/Application_Scope.md`
- `../01_Project_Information/STLC.md`

## 18. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Defined risk-based manual testing strategy, suite controls, evidence, and triage rules. | Quality Assurance |

# OrangeHRM Manual Testing — Test Estimation

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Test Estimation |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Estimation Basis | One QA engineer, controlled manual regression cycle, 96 baseline cases |

## 1. Estimation Objective

This estimate covers a controlled manual execution cycle for the existing 96-case OrangeHRM baseline, including environment/data readiness, test execution, defect handling allowance, retest/impacted regression allowance, and reporting/closure.

It does not include development fix effort, vendor support time, automation development, performance/security testing, or the effort to create entirely new edge-case coverage.

## 2. Execution Complexity Model

The source suite contains:

| Priority | Cases | Average Planned Execution Effort | Estimated Effort |
|---|---:|---:|---:|
| High | 44 | 12 minutes | 8.8 hours |
| Medium | 37 | 10 minutes | 6.2 hours |
| Low | 15 | 8 minutes | 2.0 hours |
| **Total direct execution** | **96** | **10.6 minutes average** | **17.0 hours** |

The planned duration includes navigation, data entry, observable verification, and basic result recording. It does not assume every case requires fresh account/entity creation from zero; dependent test data is reused where safe.

## 3. Supporting QA Effort

| Activity | Estimate | Basis |
|---|---:|---|
| Environment readiness and smoke setup | 1.5 h | URL/browser/build/account checks and smoke readiness |
| Test data preparation / cleanup | 3.0 h | Users, employees, leave, time, recruitment, uploads |
| Direct execution | 17.0 h | Priority-weighted 96-case estimate |
| Failure reproduction and defect documentation allowance | 4.0 h | Based on current 4-failure source snapshot; ~1 h each including evidence/triage |
| Retest and impacted sanity/regression allowance | 5.5 h | Targeted retest plus affected dependencies |
| Execution reporting / RTM reconciliation | 2.5 h | Status, module/priority metrics, defect linkage |
| Test closure review | 1.5 h | Residual risk, limitations, summary |
| **Subtotal** | **35.0 h** |  |
| Contingency (10%) | 3.5 h | Shared demo volatility, data reset, navigation/rework |
| **Planned QA effort** | **38.5 h** | Approximately 4.8 QA days at 8 h/day |

## 4. Recommended Schedule

For one QA engineer, plan **5 working days** for a controlled full cycle:

| Day | Planned Focus |
|---|---|
| Day 1 | Environment readiness, test data, smoke, authentication/dashboard/admin start |
| Day 2 | PIM and employee-dependent flows |
| Day 3 | Leave, Time, Recruitment |
| Day 4 | My Info, Performance, Directory, Buzz, Session; failure reproduction/defects |
| Day 5 | Retest/sanity/impacted regression where fixes are available; RTM/metrics/closure reporting |

This is an effort model, not a guarantee of elapsed time. Developer turnaround can extend calendar duration without increasing continuous QA execution effort.

## 5. Estimation Assumptions

- One experienced manual QA engineer performs the cycle.
- The demo is generally available.
- Admin and ESS-capable access can be established.
- Test data can be created in the UI.
- No major environment-wide blocker persists.
- The source test intent remains stable during execution.
- Four current failures are used only as a defect-handling planning allowance, not as assumed confirmed bugs.
- Shared setup and created records can be reused across logically dependent cases.
- Screenshots are captured primarily for failures/ambiguities, not every passing step.
- Build/version capture is lightweight if exposed by the application.

## 6. Estimation Exclusions

Not included:

- Engineering investigation/fix implementation.
- Waiting time for requirement clarification.
- New feature test design beyond the current baseline.
- Full cross-browser matrix.
- Accessibility, performance, penetration/security campaigns.
- API/database validation.
- Test automation.
- Production verification.

If any exclusion is added to scope, the estimate must be recalculated.

## 7. Variance Triggers

Re-estimate when:

- More than 10% of cases become blocked by data/environment issues.
- Failure rate materially exceeds the 4-case source baseline.
- A change affects authentication, common navigation, authorization, or employee identity.
- The demo resets or changes during the cycle.
- Cross-browser execution is added.
- New edge cases are approved into committed scope.
- Major requirement clarification changes expected behavior.

## 8. Execution Efficiency Controls

To protect quality without inflating effort:

- Create reusable prerequisite records once and reference their IDs.
- Execute related module cases in logical sequences.
- Run smoke before full regression.
- Use canonical test cases instead of duplicated suite definitions.
- Capture failure evidence at first reliable reproduction.
- Reuse environment metadata at cycle level while still recording row-level browser/environment/build fields.
- Use the RTM and execution report as single sources for reconciliation.

## 9. Schedule Risk

The largest calendar risks are external to test execution: demo instability, shared-data reset, unclear expected behavior, and fix turnaround. These are tracked in `Risk_Assessment.md`.

## 10. Related Documents

- `Test_Plan.md`
- `Test_Strategy.md`
- `Test_Environment.md`
- `Risk_Assessment.md`
- `Requirement_Traceability_Matrix.xlsx`

## 11. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Established priority-weighted effort and five-day controlled execution-cycle estimate. | Quality Assurance |

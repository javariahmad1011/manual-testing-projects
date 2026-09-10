# OrangeHRM Test Design

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Deliverable | Functional Test Cases |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Source | `OrangeHRM_Professional_QA_Test_Report (1).xlsx` |

## 1. Design Baseline

This folder contains the standardized executable functional test cases for the OrangeHRM Demo application.

The supplied source coverage is preserved in full:

- **13 functional modules**
- **96 existing test cases**
- **91 test-derived requirements**
- **44 High / 37 Medium / 15 Low priority cases**
- Historical source execution: **92 Pass / 4 Fail**

No source test case has been removed, merged away, or replaced by a newly invented test.

The canonical test definitions in this folder are the downstream test-design source for Smoke, Regression, Sanity, Critical Path, execution reporting, defects, and closure metrics.

## 2. Workbook Inventory

| Module | Workbook | Cases | High | Medium | Low | Source Pass | Source Fail |
|---|---|---:|---:|---:|---:|---:|---:|
| Login | `Login.xlsx` | 12 | 6 | 5 | 1 | 11 | 1 |
| Forgot Password | `Forgot_Password.xlsx` | 5 | 1 | 3 | 1 | 4 | 1 |
| Dashboard | `Dashboard.xlsx` | 5 | 2 | 2 | 1 | 5 | 0 |
| Admin | `Admin.xlsx` | 10 | 6 | 3 | 1 | 10 | 0 |
| PIM | `PIM.xlsx` | 16 | 6 | 8 | 2 | 16 | 0 |
| Leave | `Leave.xlsx` | 10 | 5 | 3 | 2 | 10 | 0 |
| Time | `Time.xlsx` | 8 | 6 | 2 | 0 | 8 | 0 |
| Recruitment | `Recruitment.xlsx` | 8 | 5 | 3 | 0 | 7 | 1 |
| My Info | `My_Info.xlsx` | 6 | 3 | 1 | 2 | 5 | 1 |
| Performance | `Performance.xlsx` | 5 | 1 | 3 | 1 | 5 | 0 |
| Directory | `Directory.xlsx` | 4 | 0 | 2 | 2 | 4 | 0 |
| Buzz | `Buzz.xlsx` | 3 | 0 | 1 | 2 | 3 | 0 |
| Session | `Session.xlsx` | 4 | 3 | 1 | 0 | 4 | 0 |

**Total: 96 cases | 44 High | 37 Medium | 15 Low | 92 Pass | 4 Fail**

## 3. Standardized Test Case Schema

Every module workbook uses the same 20-column execution schema:

`Requirement ID → Test Case ID → Module → Feature → Test Scenario → Preconditions → Test Steps → Test Data → Expected Result → Actual Result → Priority → Severity → Type → Status → Executed By → Execution Date → Environment → Browser → Build Version → Comments`

The workbooks include filters, frozen headers/identifier columns, wrapped content, controlled widths, borders, conditional status/priority/severity formatting, and dropdown validation for controlled fields.

## 4. Identifier Control

Canonical IDs follow the repository naming standard established in `01_Project_Information/Requirement_Analysis.md` and `02_Test_Planning/Requirement_Traceability_Matrix.xlsx`.

Examples:

- Requirement: `RQ-LGN-001`
- Scenario: `TS-LGN-001`
- Test Case: `TC-LGN-001`
- Defect: `BUG-001`

Scenario IDs are retained at the start of the **Test Scenario** field. The original source test ID is retained in **Comments** as `Legacy ID` so source history remains auditable.

Where multiple test cases validate one requirement/scenario, they intentionally share the same `RQ-*` and `TS-*` identifier. For example, valid rejection paths may have separate test cases while mapping to one requirement.

## 5. Test Design Improvements Applied

The source cases were improved without changing their coverage intent:

- Legacy IDs converted to canonical repository IDs.
- Requirement traceability applied to every test case.
- Feature names normalized to business-function terminology.
- Preconditions added based on the tested workflow and prerequisite data.
- Step numbering/punctuation normalized while preserving source actions.
- Expected results normalized for readability without changing the tested behavior.
- Priority values preserved from the supplied source.
- Severity added as the potential business impact if the test fails.
- Primary test type assigned using the strategy taxonomy.
- Execution evidence fields added for controlled re-execution.
- Historical Pass/Fail status preserved rather than reset or rewritten.
- Missing historical execution details are explicitly marked as not recorded instead of being invented.

## 6. Historical Execution Evidence

The source workbook records Pass/Fail status but does not provide detailed Actual Result, executor, execution date, browser, build/version, or exact environment information.

Accordingly:

- **Actual Result** states that detailed source evidence was not recorded.
- **Executed By**, **Execution Date**, **Browser**, and **Build Version** remain explicitly identified as not recorded.
- **Environment** is marked as a historical source baseline with details not recorded.
- The existing Pass/Fail state is retained.
- `ENV-DEMO-01` is the planned controlled environment for the next execution cycle, not retroactively assigned to historical results.

The four historical failures retained for triage are:

| Test Case | Module | Triage Position |
|---|---|---|
| `TC-LGN-012` | Login | Confirm intended credential case-sensitivity behavior before defect classification. |
| `TC-FGP-003` | Forgot Password | Capture the actual response for an unregistered username and assess account-enumeration exposure. |
| `TC-REC-005` | Recruitment | Capture malformed-email validation behavior and compare it with the test baseline. |
| `TC-MYI-004` | My Info | Confirm ESS Job/Salary permission expectations and identify which controls are editable. |

Formal defect records are intentionally deferred to the Defect Log and Bug Reports deliverables, where reproducible actual results and evidence can be recorded.

## 7. Missing Edge Cases Identified — Not Added to the 96-Case Baseline

The following gaps were identified during QA review and remain **separate recommendations**. They have not been inserted into these workbooks or assigned canonical test case IDs.

- **Login:** whitespace handling, Enter-key submission, credential length boundaries, repeated failed-login behavior.
- **Forgot Password:** repeated reset requests, username whitespace/case behavior, delivery verification where supported.
- **Admin:** current-admin delete/disable safeguards, username boundaries, password-policy boundaries, explicit Admin-role authorization.
- **PIM:** duplicate employee IDs, invalid/oversized uploads, date boundaries, downstream effects of employee deletion.
- **Leave:** insufficient entitlement, overlapping leave, past dates, partial-day requests, cancellation, approval authorization.
- **Time:** invalid hour totals, duplicate/overlapping attendance actions, reject flow, edit-after-submit/approval behavior.
- **Recruitment:** duplicate candidate data, unsupported/oversized resumes, invalid status transitions, vacancy field boundaries.
- **My Info:** broader field-validation and permission coverage beyond the tested Job/Salary restriction.
- **Performance:** invalid review dates, KPI boundaries, reviewer permissions.
- **Directory:** no-result/partial-match behavior and employee-detail authorization.
- **Buzz:** empty/oversized posts, edit/delete permissions, media upload, feed-state boundaries.
- **Session:** concurrent sessions, exact timeout boundaries, browser-restart persistence, role-level protected-route access.

Any approved additions will be created later as explicitly new coverage; they will not be presented as part of the original 96-case source baseline.

## 8. Traceability Chain

The controlled repository flow is:

`Requirement_Analysis.md → Requirement_Traceability_Matrix.xlsx → Functional Test Case workbook → Test Suite membership → Test Execution → Defect / disposition → Test Closure`

Relevant upstream artifacts:

- `../../01_Project_Information/Requirement_Analysis.md`
- `../../02_Test_Planning/Test_Plan.md`
- `../../02_Test_Planning/Test_Strategy.md`
- `../../02_Test_Planning/Requirement_Traceability_Matrix.xlsx`

Planned downstream artifacts:

- `../Smoke_Test_Suite.xlsx`
- `../Regression_Test_Suite.xlsx`
- `../Sanity_Test_Suite.xlsx`
- `../Critical_Path_Test_Cases.xlsx`
- `../../04_Test_Execution/Test_Execution_Report.xlsx`
- `../../04_Test_Execution/Defect_Log.xlsx`
- `../../05_Defect_Reports/`
- `../../06_Test_Closure/Test_Summary_Report.md`

Suite workbooks will reference these canonical test cases rather than create divergent copies of expected results.

## 9. Change Control

A canonical functional test case may be changed only when there is a documented requirement clarification, confirmed application change, test correction, or approved coverage expansion.

A failing result must not be converted to Pass by rewriting the expected result after execution.

Changes affecting requirement intent must be reconciled through the RTM before the repository is re-baselined.

## 10. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Standardized all 96 supplied functional cases into 13 requirement-traceable module workbooks; preserved historical execution status and documented edge-case candidates separately. | Quality Assurance |

# OrangeHRM Requirement Analysis

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Requirement Analysis |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Requirement Source | Test-derived from supplied OrangeHRM test workbook |

## 1. Analysis Basis

No vendor-authored SRS, BRD, PRD, acceptance criteria set, or change request was supplied with the baseline. Therefore, the requirements in this document are **test-derived QA requirements** extracted from the expected behavior already represented by the user's test cases.

This distinction is deliberate. The catalog is suitable for planning, scenario design, RTM construction, defect triage, and portfolio traceability, but it must not be represented as OrangeHRM's contractual product specification.

The source suite contains **96 test cases**. All 96 are represented in this requirement catalog; coverage has not been reduced.

## 2. Requirement Analysis Rules

A requirement is considered testable when it describes one observable business or system behavior, can be mapped to at least one scenario/test case, and has an expected result that can be evaluated in the deployed demo environment.

Where multiple source cases validate different conditions of one behavior, they are grouped under one requirement. Where the source case represents a distinct capability, it retains a distinct requirement.

Failed execution status does not alter the requirement definition. It changes the baseline satisfaction state and later triggers defect triage.

## 3. Module and Identifier Normalization

The source workbook uses legacy test IDs. Canonical IDs for the repository are shown below.

| Module | Source Test ID Pattern | Canonical Test Case | Requirement | Scenario |
|---|---|---|---|---|
| Login | `TC_LOGIN_###` | `TC-LGN-###` | `RQ-LGN-###` | `TS-LGN-###` |
| Forgot Password | `TC_FP_###` | `TC-FGP-###` | `RQ-FGP-###` | `TS-FGP-###` |
| Dashboard | `TC_DASH_###` | `TC-DSH-###` | `RQ-DSH-###` | `TS-DSH-###` |
| Admin | `TC_ADM_###` | `TC-ADM-###` | `RQ-ADM-###` | `TS-ADM-###` |
| PIM | `TC_PIM_###` | `TC-PIM-###` | `RQ-PIM-###` | `TS-PIM-###` |
| Leave | `TC_LV_###` | `TC-LEV-###` | `RQ-LEV-###` | `TS-LEV-###` |
| Time | `TC_TM_###` | `TC-TIM-###` | `RQ-TIM-###` | `TS-TIM-###` |
| Recruitment | `TC_REC_###` | `TC-REC-###` | `RQ-REC-###` | `TS-REC-###` |
| My Info | `TC_MI_###` | `TC-MYI-###` | `RQ-MYI-###` | `TS-MYI-###` |
| Performance | `TC_PERF_###` | `TC-PRF-###` | `RQ-PRF-###` | `TS-PRF-###` |
| Directory | `TC_DIR_###` | `TC-DIR-###` | `RQ-DIR-###` | `TS-DIR-###` |
| Buzz | `TC_BUZZ_###` | `TC-BUZ-###` | `RQ-BUZ-###` | `TS-BUZ-###` |
| Session | `TC_SES_###` | `TC-SES-###` | `RQ-SES-###` | `TS-SES-###` |

The original source ID will be retained in the standardized Functional Test Case workbooks as a migration/reference field or comment where needed, so no historical identity is lost.

## 4. Requirement Catalogue

**Baseline requirement count: 91.**  
**Satisfied at source execution baseline: 87.**  
**Failed at source execution baseline: 4.**

| Requirement ID | Scenario ID | Module | Test-derived Requirement | Covered By | Baseline |
|---|---|---|---|---|---|
| `RQ-LGN-001` | `TS-LGN-001` | Login | The login page shall render the username field, password field, Login action, and OrangeHRM branding required to begin authentication. | `TC-LGN-001` | Satisfied baseline |
| `RQ-LGN-002` | `TS-LGN-002` | Login | The application shall authenticate a user who submits valid credentials and shall navigate the authenticated user to the Dashboard. | `TC-LGN-002` | Satisfied baseline |
| `RQ-LGN-003` | `TS-LGN-003` | Login | The authentication flow shall reject invalid credentials without granting access. | `TC-LGN-003`, `TC-LGN-004` | Satisfied baseline |
| `RQ-LGN-004` | `TS-LGN-004` | Login | The login form shall enforce mandatory username and password input before authentication is attempted. | `TC-LGN-005`, `TC-LGN-006`, `TC-LGN-007` | Satisfied baseline |
| `RQ-LGN-005` | `TS-LGN-005` | Login | The password control shall mask entered password characters. | `TC-LGN-008` | Satisfied baseline |
| `RQ-LGN-006` | `TS-LGN-006` | Login | The authentication boundary shall reject SQL-injection-style input and prevent unauthorized access. | `TC-LGN-009` | Satisfied baseline |
| `RQ-LGN-007` | `TS-LGN-007` | Login | The login action shall remain stable under rapid or duplicate submission of an empty form and shall not create an application error. | `TC-LGN-010` | Satisfied baseline |
| `RQ-LGN-008` | `TS-LGN-008` | Login | The login page shall provide functional navigation to the password recovery flow. | `TC-LGN-011` | Satisfied baseline |
| `RQ-LGN-009` | `TS-LGN-009` | Login | Credential comparison shall follow the expected case-sensitivity behavior defined by the test baseline. | `TC-LGN-012` | Failed baseline |
| `RQ-FGP-001` | `TS-FGP-001` | Forgot Password | The password reset page shall load with the username input and reset workflow controls. | `TC-FGP-001` | Satisfied baseline |
| `RQ-FGP-002` | `TS-FGP-002` | Forgot Password | A password reset request submitted for a registered username shall return the expected confirmation response. | `TC-FGP-002` | Satisfied baseline |
| `RQ-FGP-003` | `TS-FGP-003` | Forgot Password | A password reset request for an unregistered username shall respond without unnecessarily exposing account existence. | `TC-FGP-003` | Failed baseline |
| `RQ-FGP-004` | `TS-FGP-004` | Forgot Password | The password reset flow shall require a username before submission. | `TC-FGP-004` | Satisfied baseline |
| `RQ-FGP-005` | `TS-FGP-005` | Forgot Password | The Cancel action on the password reset page shall return the user to the Login page. | `TC-FGP-005` | Satisfied baseline |
| `RQ-DSH-001` | `TS-DSH-001` | Dashboard | The Dashboard shall load after successful authentication and display the expected operational widgets. | `TC-DSH-001` | Satisfied baseline |
| `RQ-DSH-002` | `TS-DSH-002` | Dashboard | The authenticated navigation shall expose the modules represented in the current test baseline. | `TC-DSH-002` | Satisfied baseline |
| `RQ-DSH-003` | `TS-DSH-003` | Dashboard | Dashboard Quick Launch actions shall navigate to their corresponding functional areas. | `TC-DSH-003` | Satisfied baseline |
| `RQ-DSH-004` | `TS-DSH-004` | Dashboard | The Employee Distribution by Sub Unit visualization shall render distribution data. | `TC-DSH-004` | Satisfied baseline |
| `RQ-DSH-005` | `TS-DSH-005` | Dashboard | The user profile menu shall expose the expected account/support/logout options. | `TC-DSH-005` | Satisfied baseline |
| `RQ-ADM-001` | `TS-ADM-001` | Admin | The Admin module shall load the System Users grid and existing user records. | `TC-ADM-001` | Satisfied baseline |
| `RQ-ADM-002` | `TS-ADM-002` | Admin | An authorized administrator shall be able to create a system user using valid role, employee, status, username, and password data. | `TC-ADM-002` | Satisfied baseline |
| `RQ-ADM-003` | `TS-ADM-003` | Admin | The system shall prevent creation of a system user with a duplicate username. | `TC-ADM-003` | Satisfied baseline |
| `RQ-ADM-004` | `TS-ADM-004` | Admin | The Add User workflow shall validate all mandatory fields. | `TC-ADM-004` | Satisfied baseline |
| `RQ-ADM-005` | `TS-ADM-005` | Admin | The Add User workflow shall reject a password and confirmation password that do not match. | `TC-ADM-005` | Satisfied baseline |
| `RQ-ADM-006` | `TS-ADM-006` | Admin | An authorized administrator shall be able to edit an existing system user and persist the change. | `TC-ADM-006` | Satisfied baseline |
| `RQ-ADM-007` | `TS-ADM-007` | Admin | An authorized administrator shall be able to delete a selected test system user after confirmation. | `TC-ADM-007` | Satisfied baseline |
| `RQ-ADM-008` | `TS-ADM-008` | Admin | System Users search shall support filtering by username. | `TC-ADM-008` | Satisfied baseline |
| `RQ-ADM-009` | `TS-ADM-009` | Admin | System Users search shall support combined filtering by user role and status. | `TC-ADM-009` | Satisfied baseline |
| `RQ-ADM-010` | `TS-ADM-010` | Admin | The Reset action shall clear System Users search criteria and restore the unfiltered list. | `TC-ADM-010` | Satisfied baseline |
| `RQ-PIM-001` | `TS-PIM-001` | PIM | The PIM module shall load the Employee List grid. | `TC-PIM-001` | Satisfied baseline |
| `RQ-PIM-002` | `TS-PIM-002` | PIM | An authorized user shall be able to create an employee with the mandatory name fields and receive an employee ID. | `TC-PIM-002` | Satisfied baseline |
| `RQ-PIM-003` | `TS-PIM-003` | PIM | The employee creation flow shall support upload of a valid employee image. | `TC-PIM-003` | Satisfied baseline |
| `RQ-PIM-004` | `TS-PIM-004` | PIM | The employee creation flow shall validate mandatory employee name fields. | `TC-PIM-004` | Satisfied baseline |
| `RQ-PIM-005` | `TS-PIM-005` | PIM | Employee creation shall support creation of associated ESS login credentials when Create Login Details is enabled. | `TC-PIM-005` | Satisfied baseline |
| `RQ-PIM-006` | `TS-PIM-006` | PIM | Authorized users shall be able to update and persist employee Personal Details. | `TC-PIM-006` | Satisfied baseline |
| `RQ-PIM-007` | `TS-PIM-007` | PIM | Authorized users shall be able to add and persist employee Contact Details. | `TC-PIM-007` | Satisfied baseline |
| `RQ-PIM-008` | `TS-PIM-008` | PIM | Authorized users shall be able to add and persist employee Emergency Contacts. | `TC-PIM-008` | Satisfied baseline |
| `RQ-PIM-009` | `TS-PIM-009` | PIM | Authorized users shall be able to add and persist employee Dependents. | `TC-PIM-009` | Satisfied baseline |
| `RQ-PIM-010` | `TS-PIM-010` | PIM | Authorized users shall be able to add and persist employee Work Experience. | `TC-PIM-010` | Satisfied baseline |
| `RQ-PIM-011` | `TS-PIM-011` | PIM | Authorized users shall be able to add and persist employee Education and Skills information. | `TC-PIM-011` | Satisfied baseline |
| `RQ-PIM-012` | `TS-PIM-012` | PIM | Authorized users shall be able to upload and retrieve supported employee attachments. | `TC-PIM-012` | Satisfied baseline |
| `RQ-PIM-013` | `TS-PIM-013` | PIM | Employee search shall support filtering by employee name. | `TC-PIM-013` | Satisfied baseline |
| `RQ-PIM-014` | `TS-PIM-014` | PIM | Employee search shall support filtering by employee ID. | `TC-PIM-014` | Satisfied baseline |
| `RQ-PIM-015` | `TS-PIM-015` | PIM | Authorized users shall be able to delete a selected test employee record after confirmation. | `TC-PIM-015` | Satisfied baseline |
| `RQ-PIM-016` | `TS-PIM-016` | PIM | Authorized users shall be able to update and persist employee Job and employment attributes. | `TC-PIM-016` | Satisfied baseline |
| `RQ-LEV-001` | `TS-LEV-001` | Leave | The Leave module shall load with the leave functions represented in the current baseline. | `TC-LEV-001` | Satisfied baseline |
| `RQ-LEV-002` | `TS-LEV-002` | Leave | A user shall be able to submit a leave request with a valid leave type and valid date range. | `TC-LEV-002` | Satisfied baseline |
| `RQ-LEV-003` | `TS-LEV-003` | Leave | The leave application flow shall reject an invalid date range where the From date is later than the To date. | `TC-LEV-003` | Satisfied baseline |
| `RQ-LEV-004` | `TS-LEV-004` | Leave | The leave application flow shall persist an entered comment with the leave request. | `TC-LEV-004` | Satisfied baseline |
| `RQ-LEV-005` | `TS-LEV-005` | Leave | Leave List shall display submitted requests and support the tested filtering workflow. | `TC-LEV-005` | Satisfied baseline |
| `RQ-LEV-006` | `TS-LEV-006` | Leave | An authorized administrator shall be able to approve or reject a pending leave request and persist the resulting status. | `TC-LEV-006`, `TC-LEV-007` | Satisfied baseline |
| `RQ-LEV-007` | `TS-LEV-007` | Leave | My Leave shall show leave history for the authenticated employee. | `TC-LEV-008` | Satisfied baseline |
| `RQ-LEV-008` | `TS-LEV-008` | Leave | An authorized user shall be able to add employee leave entitlement and update the corresponding balance. | `TC-LEV-009` | Satisfied baseline |
| `RQ-LEV-009` | `TS-LEV-009` | Leave | An authorized user shall be able to configure and persist the leave period start date. | `TC-LEV-010` | Satisfied baseline |
| `RQ-TIM-001` | `TS-TIM-001` | Time | The Time module shall load the current-period Timesheet view. | `TC-TIM-001` | Satisfied baseline |
| `RQ-TIM-002` | `TS-TIM-002` | Time | A user shall be able to create and save a timesheet entry for a project/activity with entered hours. | `TC-TIM-002` | Satisfied baseline |
| `RQ-TIM-003` | `TS-TIM-003` | Time | A completed timesheet shall be submittable for approval and shall transition to Submitted status. | `TC-TIM-003` | Satisfied baseline |
| `RQ-TIM-004` | `TS-TIM-004` | Time | An authorized administrator shall be able to approve a submitted timesheet. | `TC-TIM-004` | Satisfied baseline |
| `RQ-TIM-005` | `TS-TIM-005` | Time | Attendance shall support Punch In and Punch Out with timestamps and calculated duration. | `TC-TIM-005`, `TC-TIM-006` | Satisfied baseline |
| `RQ-TIM-006` | `TS-TIM-006` | Time | Employee Time reports shall be generatable for a selected employee and date range. | `TC-TIM-007` | Satisfied baseline |
| `RQ-TIM-007` | `TS-TIM-007` | Time | An authorized user shall be able to create a project under Project Info and make it available for timesheet selection. | `TC-TIM-008` | Satisfied baseline |
| `RQ-REC-001` | `TS-REC-001` | Recruitment | The Recruitment module shall load the Candidates list. | `TC-REC-001` | Satisfied baseline |
| `RQ-REC-002` | `TS-REC-002` | Recruitment | An authorized user shall be able to add a candidate with valid name, email, and vacancy data. | `TC-REC-002` | Satisfied baseline |
| `RQ-REC-003` | `TS-REC-003` | Recruitment | Candidate creation shall support upload and persistence of a supported resume file. | `TC-REC-003` | Satisfied baseline |
| `RQ-REC-004` | `TS-REC-004` | Recruitment | The Add Candidate flow shall validate mandatory name and email fields. | `TC-REC-004` | Satisfied baseline |
| `RQ-REC-005` | `TS-REC-005` | Recruitment | The Add Candidate flow shall reject an invalid email format with validation feedback. | `TC-REC-005` | Failed baseline |
| `RQ-REC-006` | `TS-REC-006` | Recruitment | An authorized user shall be able to create a vacancy with valid job title and hiring manager data. | `TC-REC-006` | Satisfied baseline |
| `RQ-REC-007` | `TS-REC-007` | Recruitment | An authorized user shall be able to move a candidate through the tested recruitment status workflow and retain status history. | `TC-REC-007` | Satisfied baseline |
| `RQ-REC-008` | `TS-REC-008` | Recruitment | Candidate search shall support filtering by vacancy and application status. | `TC-REC-008` | Satisfied baseline |
| `RQ-MYI-001` | `TS-MYI-001` | My Info | My Info shall display the personal details of the authenticated employee. | `TC-MYI-001` | Satisfied baseline |
| `RQ-MYI-002` | `TS-MYI-002` | My Info | An employee shall be able to update and persist permitted personal contact details. | `TC-MYI-002` | Satisfied baseline |
| `RQ-MYI-003` | `TS-MYI-003` | My Info | An employee shall be able to upload and persist a valid profile picture. | `TC-MYI-003` | Satisfied baseline |
| `RQ-MYI-004` | `TS-MYI-004` | My Info | An ESS user shall be restricted from editing Job/Salary information according to the expected permission model. | `TC-MYI-004` | Failed baseline |
| `RQ-MYI-005` | `TS-MYI-005` | My Info | An authenticated user shall be able to change the account password using the tested password-change workflow. | `TC-MYI-005` | Satisfied baseline |
| `RQ-MYI-006` | `TS-MYI-006` | My Info | An employee shall be able to add and persist dependent information in My Info. | `TC-MYI-006` | Satisfied baseline |
| `RQ-PRF-001` | `TS-PRF-001` | Performance | The Performance module shall load the review/tracker management area represented in the test baseline. | `TC-PRF-001` | Satisfied baseline |
| `RQ-PRF-002` | `TS-PRF-002` | Performance | An authorized user shall be able to create and persist a Performance Review for valid employee, reviewer, and date data. | `TC-PRF-002` | Satisfied baseline |
| `RQ-PRF-003` | `TS-PRF-003` | Performance | An authorized user shall be able to create and associate a KPI with a job title. | `TC-PRF-003` | Satisfied baseline |
| `RQ-PRF-004` | `TS-PRF-004` | Performance | The Employee Trend Report shall generate performance trend information for a selected employee. | `TC-PRF-004` | Satisfied baseline |
| `RQ-PRF-005` | `TS-PRF-005` | Performance | Manage Reviews shall support the tested search/filter criteria. | `TC-PRF-005` | Satisfied baseline |
| `RQ-DIR-001` | `TS-DIR-001` | Directory | The Directory shall load employee cards/listing and search controls. | `TC-DIR-001` | Satisfied baseline |
| `RQ-DIR-002` | `TS-DIR-002` | Directory | Directory search shall support filtering by employee name. | `TC-DIR-002` | Satisfied baseline |
| `RQ-DIR-003` | `TS-DIR-003` | Directory | Directory search shall support filtering by job title and location. | `TC-DIR-003` | Satisfied baseline |
| `RQ-DIR-004` | `TS-DIR-004` | Directory | Selecting an employee in Directory shall open the corresponding employee detail view. | `TC-DIR-004` | Satisfied baseline |
| `RQ-BUZ-001` | `TS-BUZ-001` | Buzz | Buzz shall load the post feed and post composer. | `TC-BUZ-001` | Satisfied baseline |
| `RQ-BUZ-002` | `TS-BUZ-002` | Buzz | An authenticated user shall be able to create a text post and see it in the feed. | `TC-BUZ-002` | Satisfied baseline |
| `RQ-BUZ-003` | `TS-BUZ-003` | Buzz | An authenticated user shall be able to like and comment on a post with corresponding UI updates. | `TC-BUZ-003` | Satisfied baseline |
| `RQ-SES-001` | `TS-SES-001` | Session | Logout shall terminate the authenticated session and return the user to the Login page. | `TC-SES-001` | Satisfied baseline |
| `RQ-SES-002` | `TS-SES-002` | Session | Browser back navigation after logout shall not restore access to authenticated content. | `TC-SES-002` | Satisfied baseline |
| `RQ-SES-003` | `TS-SES-003` | Session | An inactive authenticated session shall require re-authentication after the configured timeout threshold. | `TC-SES-003` | Satisfied baseline |
| `RQ-SES-004` | `TS-SES-004` | Session | Direct navigation to authenticated internal URLs without a valid session shall be blocked and redirected to Login. | `TC-SES-004` | Satisfied baseline |

## 5. Baseline Requirement Failures Requiring Triage

The following requirement-level gaps are carried forward from the source workbook:

| Requirement | Test Case | Triage Focus |
|---|---|---|
| `RQ-LGN-009` | `TC-LGN-012` | Confirm intended username/password case-sensitivity rules before classifying the observed behavior as a defect. |
| `RQ-FGP-003` | `TC-FGP-003` | Confirm expected non-enumerating password-reset response and capture the actual demo response. |
| `RQ-REC-005` | `TC-REC-005` | Capture actual validation behavior for malformed email input and compare with expected validation. |
| `RQ-MYI-004` | `TC-MYI-004` | Confirm ESS permission model for Job/Salary data and capture which controls are editable/read-only in the demo. |

Detailed defects are intentionally not invented in this phase. They will be created from execution evidence in the Defect Log and individual Bug Reports deliverables.

## 6. Requirement Ambiguities / Evidence Gaps

The following items require control during later planning and execution:

- **Formal source requirements are absent.** Expected behavior is currently inferred from test intent.
- **Build/version is absent.** The execution baseline cannot yet be tied to a specific application build.
- **Actual Result is absent for source cases.** Pass/fail exists, but detailed observed output is not recorded.
- **Execution context is incomplete.** Browser, environment URL, user role per case, execution date, and executor are not recorded at row level.
- **Role matrix is incomplete.** Admin and ESS behaviors are present, but the full authorization matrix is not.
- **Demo-state dependency exists.** Search, approval, reporting, vacancy, employee, and directory cases depend on available demo data or newly created test data.

These gaps will be addressed where possible in `02_Test_Planning`, `03_Test_Design`, and `04_Test_Execution`.

## 7. Missing Edge Cases Identified — Not Added to Existing Coverage

The following are candidate gaps identified during senior QA review. They are **not silently added** to the 96-case source baseline and should be reviewed before inclusion in a future test-design expansion:

- Authentication input boundaries: leading/trailing whitespace, keyboard submission, username/password length boundaries, repeated failed-login handling.
- Password recovery abuse controls: repeated requests, whitespace/case handling, actual email delivery where the demo supports it.
- Admin safeguards: deleting/disabling the currently logged-in administrator, username length/character rules, password-policy boundaries, role-based access to Admin.
- PIM data integrity: duplicate employee IDs, invalid/oversized upload files, date boundaries, deletion impact on dependent records.
- Leave business rules: insufficient entitlement, overlapping requests, past dates, partial-day requests, cancellation, approval authorization.
- Time controls: invalid hour totals, duplicate/overlapping attendance events, reject workflow, edit-after-submit/approval rules.
- Recruitment boundaries: duplicate candidate data, unsupported/oversized resumes, invalid status transitions, vacancy field boundaries.
- My Info field validation and permission coverage beyond Job/Salary.
- Performance boundaries: invalid review dates, KPI value limits, reviewer permission rules.
- Directory no-result/partial-match behavior and authorization around employee detail access.
- Buzz empty/oversized content, edit/delete permissions, media upload, and feed-state edge cases.
- Session and access controls: concurrent sessions, exact inactivity timeout behavior, session persistence across browser restart, and protected-route authorization by role.

Any approved additions will receive new IDs and will be explicitly distinguishable from the original 96 cases.

## 8. Change Control

Requirement changes will follow this rule:

`Requirement change → impact analysis → scenario/test impact → RTM update → execution scope update → regression impact → closure reconciliation`

No requirement or expected result should be altered merely to convert a failing test into a pass. Expectation changes require documented rationale.

## 9. Traceability Connections

This document is the upstream source for:

- `../02_Test_Planning/Requirement_Traceability_Matrix.xlsx`
- `../02_Test_Planning/Risk_Assessment.md`
- `../03_Test_Design/Functional_Test_Cases/`
- `../03_Test_Design/Smoke_Test_Suite.xlsx`
- `../03_Test_Design/Regression_Test_Suite.xlsx`
- `../03_Test_Design/Sanity_Test_Suite.xlsx`
- `../03_Test_Design/Critical_Path_Test_Cases.xlsx`
- `../04_Test_Execution/Defect_Log.xlsx`
- `../06_Test_Closure/Test_Summary_Report.md`

See also [Application Scope](./Application_Scope.md), [STLC](./STLC.md), and [Test Objectives](./Test_Objectives.md).

## 10. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Established test-derived requirements and source-to-canonical traceability baseline for all 96 supplied cases. | Quality Assurance |

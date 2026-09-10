# OrangeHRM Application Scope

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Application Scope |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |

## 1. Scope Statement

The test scope is limited to the OrangeHRM Demo behaviors represented by the supplied manual test baseline. The current scope covers 13 functional modules and 96 executable cases. It is intended to validate primary employee-management, administrative, self-service, workflow, and session behaviors through the user interface.

Scope is controlled by [Requirement Analysis](./Requirement_Analysis.md). Later test suites may select subsets of these cases for smoke, sanity, regression, high-priority, or critical-path execution, but selection does not remove the underlying functional coverage.

## 2. In-Scope Functional Coverage

| Module | In-Scope Functions |
|---|---|
| Login | Login page rendering, valid authentication, invalid credentials, required fields, password masking, SQL-injection-style rejection, duplicate empty submission stability, password-recovery navigation, credential case behavior. |
| Forgot Password | Reset page, valid username request, invalid username response, required username, cancel navigation. |
| Dashboard | Post-login dashboard load, widgets, sidebar modules, Quick Launch navigation, employee distribution chart, profile dropdown. |
| Admin | System Users list, add user, duplicate username, mandatory validation, password confirmation, edit, delete, username/role/status filters, reset filters. |
| PIM | Employee list, employee creation, image upload, required fields, ESS login creation, personal/contact/emergency/dependent data, qualifications, attachments, search, delete, job details. |
| Leave | Leave module navigation, apply leave, date validation, comments, leave list, approve/reject, own leave history, entitlements, leave-period configuration. |
| Time | Timesheets, timesheet entries, submission, approval, attendance punch in/out, employee time reports, project creation. |
| Recruitment | Candidates list, add candidate, resume upload, mandatory validation, email validation, vacancy creation, pipeline status, candidate filters. |
| My Info | Own personal data, contact updates, profile picture, ESS Job/Salary permissions, password change, dependents. |
| Performance | Performance area load, reviews, KPIs, employee trend reporting, review search/filter. |
| Directory | Directory load, employee-name search, job title/location search, employee detail navigation. |
| Buzz | Feed load, text post, like and comment. |
| Session | Logout, browser-back protection after logout, inactivity timeout, direct protected-URL access. |

## 3. In-Scope Test Characteristics

The baseline includes:

- Positive functional flows.
- Negative credential and field-validation checks.
- Mandatory-field validation.
- CRUD-style UI workflows for supported entities.
- Search/filter behavior.
- Basic role/permission checks where source coverage exists.
- Basic session/access control checks.
- File upload checks where source coverage exists.
- Basic security-oriented input rejection represented by the login SQL-injection-style test.
- Workflow status transitions for leave, time, and recruitment.
- UI navigation and selected dashboard/report rendering.

## 4. User Roles Represented

The supplied suite clearly exercises:

| Role | Coverage |
|---|---|
| Administrator / privileged user | System users, employee data, leave decisions, timesheet approval, recruitment, performance/configuration-style actions. |
| ESS / employee self-service user | My Info, leave, timesheet/attendance behaviors, session actions, and role-restriction checks. |

The repository does **not** assume a complete role-permission matrix beyond what is evidenced by the supplied tests.

## 5. Out of Scope for the Current Baseline

The following are not represented sufficiently in the supplied test source and are therefore outside the current committed baseline:

- API/service contract testing.
- Direct database validation.
- Production data validation.
- Load, stress, soak, or scalability testing.
- Full penetration/security assessment.
- Automated vulnerability scanning.
- Native mobile application testing.
- Browser/device compatibility matrix execution beyond any environment later explicitly recorded.
- Accessibility conformance testing.
- Localization/internationalization testing.
- Email infrastructure verification beyond UI confirmation of password-reset request behavior.
- Backup, restore, disaster recovery, deployment, infrastructure, and observability validation.
- Vendor source-code review or unit/integration test review.
- Full authorization matrix across all OrangeHRM roles and every module.
- Payment, payroll, benefits, or other functionality not represented in the supplied suite.

Items in the separate edge-case review in [Requirement Analysis](./Requirement_Analysis.md) are also not part of the original 96-case baseline unless approved later.

## 6. Environment Boundary

The source workbook identifies the product as the OrangeHRM Demo application but does not record a build number, per-test environment, browser, OS, or execution timestamp. `02_Test_Planning/Test_Environment.md` will formalize the execution environment used for the portfolio.

Until that artifact is baselined, environment-dependent conclusions should be described as applicable to the tested Demo deployment only.

## 7. Test Data Boundary

The existing cases reference representative data such as Admin credentials, employee names, job titles, leave dates, vacancies, project names, and uploaded files. The source does not provide a centrally controlled test-data catalog.

`../04_Test_Execution/Test_Data.xlsx` will later normalize reusable data, ownership, creation/cleanup requirements, and dependencies while preserving the intent of the existing cases.

## 8. Scope Prioritization

The source priority mix is:

- High: 44
- Medium: 37
- Low: 15

High priority indicates business or control significance in the source suite, but it is not automatically equivalent to defect Severity. Priority and Severity will remain separate fields in the standardized test and defect artifacts.

## 9. Scope Change Procedure

A scope change requires:

1. Requirement impact review.
2. Test scenario/test case impact review.
3. Risk and estimation update where applicable.
4. RTM update.
5. Regression/smoke/critical-path suite impact assessment.
6. Execution and closure metric reconciliation.

No scope item is removed solely because the Demo application cannot currently support the expected behavior; unsupported or ambiguous behavior must be documented as a defect, limitation, or requirement clarification.

## 10. Related Documents

- [Project Overview](./Project_Overview.md)
- [Requirement Analysis](./Requirement_Analysis.md)
- [STLC](./STLC.md)
- [SDLC](./SDLC.md)
- [Test Objectives](./Test_Objectives.md)
- Planned: `../02_Test_Planning/Test_Plan.md`
- Planned: `../02_Test_Planning/Test_Environment.md`
- Planned: `../03_Test_Design/Functional_Test_Cases/`

## 11. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Established committed functional scope from the supplied 96-case OrangeHRM baseline. | Quality Assurance |

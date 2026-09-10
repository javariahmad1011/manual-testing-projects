# OrangeHRM Manual Testing — Test Environment

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Test Environment |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Environment ID | ENV-DEMO-01 |

## 1. Environment Objective

This document defines the minimum environment information required to make OrangeHRM manual execution reproducible. The supplied 96-case workbook does not contain the original browser, operating system, exact URL, build/version, execution date, or executor at row level. Those values are therefore treated as historical evidence gaps and are not invented.

`ENV-DEMO-01` is the controlled identifier for the next repository execution against the OrangeHRM Demo deployment.

## 2. Environment Baseline

| Attribute | Planned / Controlled Value | Evidence Status |
|---|---|---|
| Application | OrangeHRM Demo | Confirmed from project source |
| Environment ID | `ENV-DEMO-01` | Defined by QA |
| Environment Type | Public/demo web application | Project boundary |
| Exact Test URL | Record at start of controlled execution | Not present in source workbook |
| Build / Release Version | Record visible identifier if exposed; otherwise `Not Exposed` | Not present in source workbook |
| Primary Browser | Record browser name and exact version at execution | Not present in source workbook |
| Operating System | Record OS name and version at execution | Not present in source workbook |
| Screen / Viewport | Record only where UI behavior is layout-sensitive | Not present in source workbook |
| Network | Stable internet connection; note material interruptions | Execution control |
| Execution Time Zone | Record with execution date/time where relevant | Not present in source workbook |
| Admin Account | Available and validated before smoke | Required dependency |
| ESS Account | Available/created before role-sensitive cases | Required dependency |
| Email Delivery | Not required for current baseline; UI reset confirmation only | Out of baseline |
| Database / API Access | None required | Out of scope |

The exact URL/browser/OS/build values become authoritative only when recorded during the controlled cycle.

## 3. Browser Control

The core portfolio cycle should use one named primary browser so results are internally consistent. Record:

`Browser name + full version + execution date`

If an issue appears browser-specific, reproduce on a second browser before classifying it as application-wide. Cross-browser coverage must be explicitly recorded as additional execution and is not implied by the baseline.

## 4. Build and Deployment Identification

Before smoke execution:

1. Capture any visible OrangeHRM version/build identifier.
2. If no version is visible, record `Build Version = Not Exposed`.
3. Record the exact environment URL.
4. Record execution start date/time.
5. If the demo visibly changes during the cycle, stop affected testing and re-run smoke before continuing.

A public demo may be updated independently of this repository. Time-stamped environment evidence is therefore important.

## 5. Account and Role Readiness

| Account / Role | Required For | Readiness Check |
|---|---|---|
| Administrator / privileged account | Dashboard, Admin, PIM, leave approval, time approval, recruitment, performance configuration | Login succeeds; required modules visible |
| ESS / employee account | My Info, leave/self-service, timesheet/attendance, permission restrictions | Login succeeds; expected self-service areas visible |
| Newly created system user | Admin CRUD and duplicate username cases | Unique username and known cleanup path |
| Newly created employee | PIM CRUD and downstream workflow data | Unique employee identity; record ID captured |

The current source suite does not prove a complete role-permission matrix. Role expectations outside tested behavior must not be inferred.

## 6. Test Data Dependencies

The environment must support controlled creation or identification of:

- Unique system user.
- Employee record and employee ID.
- Employee image file.
- Employee document attachment.
- ESS credentials where applicable.
- Leave type/entitlement and valid future leave dates.
- Project/customer/activity and timesheet data.
- Attendance state for Punch In/Punch Out.
- Candidate, vacancy, hiring manager, and resume file.
- Performance review/KPI data.
- Directory-searchable employee data.
- Buzz post/comment data.

Reusable values will be maintained in `../04_Test_Execution/Test_Data.xlsx`.

## 7. Upload Fixture Requirements

Prepare local non-sensitive fixtures before execution:

| Fixture | Used By | Control |
|---|---|---|
| Valid JPG/PNG employee image | PIM / My Info | Small supported image; no personal data |
| Valid PDF/DOC document | PIM Attachments | QA placeholder content |
| Valid PDF resume | Recruitment | Synthetic candidate content only |

Unsupported-size/type boundary tests are candidate edge cases and are not part of the original 96-case baseline.

## 8. Environment Readiness Checklist

Before Smoke:

- [ ] Target URL captured and reachable.
- [ ] Browser name/version recorded.
- [ ] OS/version recorded.
- [ ] Build/version captured or marked `Not Exposed`.
- [ ] Admin login validated.
- [ ] ESS login available or creation path validated.
- [ ] Dashboard and left navigation load.
- [ ] Test data prerequisites identified.
- [ ] Upload fixtures available.
- [ ] No known outage or environment-wide blocker.
- [ ] Execution cycle ID and date created.

If any critical item is unavailable, log the condition and restrict execution to unaffected scope.

## 9. Shared Demo Environment Risks

The public/demo nature of the application can introduce:

- Data created/deleted by other users.
- Search-result drift.
- Pre-existing usernames/employees/candidates.
- Changed configuration or leave data.
- Demo reset between sessions.
- Vendor deployment changes during a test cycle.

Mitigations:

- Use unique, timestamped/suffixed QA data where practical.
- Capture created record identifiers.
- Avoid assertions based on fixed global counts.
- Re-check prerequisites before dependent tests.
- Re-run smoke after material environment change.
- Preserve screenshots for failures and volatile state.

These risks are tracked in `Risk_Assessment.md`.

## 10. Environment Incident Classification

A test is `Blocked`, not `Fail`, when the expected application behavior cannot be evaluated because of an environment, access, dependency, or test-data condition.

Examples:

- Demo endpoint unavailable.
- Required role/account cannot authenticate for reasons unrelated to the tested function.
- Prerequisite record cannot be created because of an upstream outage.
- Page fails to load across broad areas due to environment instability.

Application behavior that is reproducibly incorrect in an otherwise healthy environment remains a test failure.

## 11. Historical Baseline Limitation

The existing 92 Pass / 4 Fail snapshot cannot be tied to a recorded browser/build/environment configuration from the supplied workbook. It remains valid as source status history but not as a fully reproducible execution record.

The standardized `04_Test_Execution/Test_Execution_Report.xlsx` will close this gap.

## 12. Related Documents

- `Test_Plan.md`
- `Test_Strategy.md`
- `Risk_Assessment.md`
- `../01_Project_Information/Application_Scope.md`
- `../04_Test_Execution/Test_Data.xlsx`
- `../04_Test_Execution/Test_Execution_Report.xlsx`

## 13. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Defined controlled demo environment, readiness gates, account/data dependencies, and historical evidence gaps. | Quality Assurance |

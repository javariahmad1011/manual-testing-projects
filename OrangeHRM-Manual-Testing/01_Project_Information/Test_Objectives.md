# OrangeHRM Test Objectives

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Test Objectives |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |

## 1. Primary Objective

Provide defensible manual QA evidence that the OrangeHRM Demo functions represented by the agreed scope behave as expected for core administrative and employee workflows, and that release-relevant risks are visible through traceable tests, execution results, defects, and closure metrics.

## 2. Measurable Quality Objectives

| ID | Objective | Measure / Evidence |
|---|---|---|
| OBJ-01 | Preserve complete source coverage while professionalizing the repository. | All 96 supplied test cases retained and mapped to canonical IDs; no source case removed. |
| OBJ-02 | Establish end-to-end traceability. | Every standardized test case maps to Requirement ID and Scenario ID; later RTM maps Requirement → Scenario → Test Case → Status. |
| OBJ-03 | Validate authentication and protected-session behavior. | Login, password recovery, logout, post-logout navigation, timeout, and protected-URL cases executed with documented results. |
| OBJ-04 | Validate administrator control of system users and employee records. | Admin and PIM create/search/update/delete/validation flows executed. |
| OBJ-05 | Validate employee lifecycle and self-service data handling. | PIM and My Info profile, contact, dependent, job, attachment/image, and permission behaviors executed where covered. |
| OBJ-06 | Validate business workflow state transitions. | Leave approval/rejection, timesheet submission/approval, recruitment pipeline status, and related list/search behaviors executed. |
| OBJ-07 | Validate high-priority release exposure. | All High-priority cases in the approved execution cycle executed or explicitly dispositioned. |
| OBJ-08 | Ensure failures become actionable quality evidence. | Every failed case linked to a defect, accepted limitation, or documented expectation clarification with reproducible Actual vs Expected behavior. |
| OBJ-09 | Maintain reliable execution metrics. | Test totals, execution percentage, pass/fail/blocked counts, module totals, and defect counts reconcile across Execution Report, RTM, and Closure. |
| OBJ-10 | Separate test priority from defect severity. | Standardized cases contain Priority and Severity fields; defect records use independent Severity and Priority classifications. |
| OBJ-11 | Protect the critical business path after change. | Approved Critical Path suite reaches 100% execution; unresolved critical-path failures are explicitly surfaced at closure. |
| OBJ-12 | Produce reusable release suites without duplicating the master source. | Smoke, sanity, regression, high-priority, and critical-path suites reference canonical functional tests. |

## 3. Risk-Focused Test Objectives

The project gives particular attention to behaviors that can cause loss of access, unauthorized access, incorrect employee data, broken workflow decisions, or inability to perform core HR operations.

Risk focus includes:

- Authentication and session boundaries.
- User administration and permissions.
- Employee creation and data maintenance.
- Leave request and approval decisions.
- Timesheet/attendance capture and approval.
- Recruitment candidate/vacancy workflow.
- Data validation that prevents invalid records.
- Search/filter behavior needed to locate operational records.
- File upload and profile-data persistence where covered.

Detailed scoring and mitigation ownership will be created in `../02_Test_Planning/Risk_Assessment.md`.

## 4. Baseline Execution Position

Current supplied execution evidence:

| Metric | Baseline |
|---|---:|
| Total Test Cases | 96 |
| Executed | 96 |
| Passed | 92 |
| Failed | 4 |
| Blocked | 0 |
| Not Executed | 0 |
| Execution Rate | 100% |
| Pass Rate | 95.83% |
| High Priority | 44 |
| Medium Priority | 37 |
| Low Priority | 15 |

This is a historical/current source snapshot, not the final repository closure decision. Detailed Actual Results and defect linkage still need to be established for the four failures.

## 5. Release-Style Exit Objectives

The future test-closure recommendation should not be considered complete until:

- 100% of planned Critical Path tests are executed.
- 100% of planned High-priority tests are executed or formally dispositioned.
- No unresolved Critical/Blocker defect remains unless explicitly accepted.
- Failed cases are linked to controlled defects/limitations/clarifications.
- Fixed defects have retest evidence.
- Required sanity/regression has completed.
- RTM and execution metrics reconcile.
- Known limitations and residual risk are documented.

Pass percentage alone is not a sufficient release decision criterion.

## 6. Non-Objectives

This project does not currently attempt to certify:

- OrangeHRM production readiness.
- Vendor compliance to an unpublished specification.
- Performance/scalability targets.
- Security penetration resistance.
- Accessibility conformance.
- API/database correctness.
- Native mobile compatibility.
- Full cross-browser/device compatibility.
- Complete role authorization across every OrangeHRM role.

Those areas require evidence not present in the supplied baseline and are controlled as out of scope in [Application Scope](./Application_Scope.md).

## 7. Coverage Expansion Policy

Candidate missing edge cases are documented separately in [Requirement Analysis](./Requirement_Analysis.md). They are not counted in the original 96-test baseline. If approved later, each addition will receive a new canonical ID and an explicit rationale so portfolio metrics remain transparent.

## 8. Related Documents

- [Project Overview](./Project_Overview.md)
- [Requirement Analysis](./Requirement_Analysis.md)
- [Application Scope](./Application_Scope.md)
- [STLC](./STLC.md)
- [SDLC](./SDLC.md)
- Planned: `../02_Test_Planning/Test_Plan.md`
- Planned: `../02_Test_Planning/Risk_Assessment.md`
- Planned: `../06_Test_Closure/Test_Summary_Report.md`

## 9. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Defined measurable QA objectives, baseline metrics, risk focus, and closure-quality goals. | Quality Assurance |

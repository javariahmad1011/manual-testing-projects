# OrangeHRM Manual Testing — Risk Assessment

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | Risk Assessment |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |
| Scoring | Probability (1–5) × Impact (1–5) |

## 1. Risk Model

Risk Exposure = `Probability × Impact`

| Score | Rating | QA Response |
|---:|---|---|
| 15–25 | High | Active mitigation; prioritize in planning/execution; escalate if realized |
| 8–14 | Medium | Mitigate and monitor during cycle |
| 1–7 | Low | Accept/monitor unless conditions change |

This register covers test-project and product-quality risks visible from the current source. It does not claim knowledge of OrangeHRM vendor internals.

## 2. Risk Register

| Risk ID | Risk | Category | Probability | Impact | Exposure | Rating | Mitigation / Control | Trigger / Evidence | Owner |
|---|---|---|---:|---:|---:|---|---|---|---|
| RSK-001 | No formal SRS/PRD is supplied, so expected behavior is test-derived and some assertions may be ambiguous. | Requirements | 4 | 5 | 20 | High | Keep test-derived requirements explicitly labeled; do not change expectations to force passes; route ambiguous failures to clarification before defect confirmation. | Failure conflicts with observable product behavior or expected rule is not independently supported. | QA Lead |
| RSK-002 | Public/demo data can be changed or reset by other users, invalidating prerequisites and search assertions. | Environment/Data | 5 | 4 | 20 | High | Use unique QA data, capture created IDs, validate prerequisites before dependent tests, avoid fixed global counts, maintain controlled Test Data sheet. | Created record disappears/changes; search returns unrelated state; demo reset detected. | QA Engineer |
| RSK-003 | Original execution does not record browser, OS, URL, build/version, or detailed Actual Results, reducing reproducibility of the 92/4 baseline. | Evidence | 5 | 4 | 20 | High | Treat historical metrics as source snapshot only; capture full environment and Actual Result in controlled re-execution. | A source failure cannot be reproduced or tied to a deployment/browser. | QA Lead |
| RSK-004 | Authentication/session failure could block most of the suite or expose protected content. | Product/Execution | 3 | 5 | 15 | High | Execute login/logout/protected-route smoke first; suspend affected scope on environment-wide authentication blocker. | Valid login fails broadly; logout does not terminate session; protected URLs accessible unauthenticated. | QA Lead |
| RSK-005 | Incomplete role-permission evidence may cause incorrect defect classification, especially for ESS restrictions. | Requirements/Security | 4 | 4 | 16 | High | Restrict claims to represented Admin/ESS behavior; capture exact editable/read-only controls; clarify permission intent before classifying ambiguous failures. | Role sees unexpected module/control or `TC-MYI-004` cannot be conclusively assessed. | QA Lead |
| RSK-006 | Employee/user records are prerequisites for Leave, Time, My Info, Directory and other downstream workflows; upstream data failure can create cascading blockers. | Data/Dependency | 3 | 5 | 15 | High | Create and validate core employee/user data early; preserve identifiers; separate upstream blocker from downstream functional failure. | Employee/ESS creation fails or record unavailable to dependent modules. | QA Engineer |
| RSK-007 | Demo application may change during the cycle without a QA-controlled deployment notice. | Environment | 4 | 4 | 16 | High | Capture execution timestamp/build if visible; re-run smoke after material UI/behavior change; keep cycle metrics separate. | UI/navigation/behavior changes mid-cycle; visible version changes. | QA Lead |
| RSK-008 | Password reset behavior may be difficult to validate beyond UI confirmation because actual email delivery is not part of the source baseline. | External Dependency | 3 | 3 | 9 | Medium | Validate only the UI response represented by the source tests; do not claim email delivery unless evidence is available. | Reset request succeeds but email channel cannot be observed. | QA Engineer |
| RSK-009 | Upload scenarios can fail because of local fixture format/size rather than product behavior. | Test Data | 3 | 3 | 9 | Medium | Use known-valid synthetic JPG/PNG/PDF/DOC fixtures; record fixture details; separate unsupported-boundary testing from baseline. | Upload rejected unexpectedly; file corrupt/unsupported. | QA Engineer |
| RSK-010 | Workflow state dependencies (leave/timesheet/recruitment) can cause false failures if a record is in the wrong status. | Test Data/Workflow | 3 | 4 | 12 | Medium | Create/record prerequisite status during the same cycle; verify current status before transition assertions. | Approval/status action unavailable because record is not in expected state. | QA Engineer |
| RSK-011 | Shared navigation/component changes can create wide regression impact not obvious from a single defect. | Product Regression | 3 | 4 | 12 | Medium | Use impact analysis across authentication, navigation, common forms, role controls, and entity dependencies; expand regression accordingly. | Fix/change touches shared layout, validation, auth, or common component. | QA Lead |
| RSK-012 | Failure evidence may be insufficient if only Pass/Fail is recorded without Actual Result and screenshot. | Evidence | 3 | 4 | 12 | Medium | Require written Actual Result for every failure and screenshot for reproducible/ambiguous failures. | Defect triage cannot understand discrepancy from test status alone. | QA Engineer |
| RSK-013 | Case-sensitive credential expectation may reflect an unclear rule rather than a defect. | Requirements | 3 | 3 | 9 | Medium | Reproduce `TC-LGN-012`; distinguish username case handling from password case handling; classify only after expectation is confirmed. | Observed case behavior differs from current expected result. | QA Lead |
| RSK-014 | Recruitment malformed-email validation may differ in message wording while still enforcing the rule. | Requirements/UI | 3 | 3 | 9 | Medium | Validate the actual business rule (invalid email rejected) separately from exact message text unless text is a requirement. | `TC-REC-005` fails only because message text differs. | QA Lead |
| RSK-015 | Time/session tests can be duration-dependent and increase cycle time or produce inconsistent results if timeout configuration is unknown. | Execution | 3 | 3 | 9 | Medium | Record configured/observed timeout where possible; execute long-wait session tests in parallel with other non-conflicting work; document observed threshold. | `TC-SES-003` exceeds expected duration or timeout threshold is not exposed. | QA Engineer |

## 3. Top Risks Requiring Active Control

The immediate controls for this project are:

1. **Requirement ambiguity (`RSK-001`, `RSK-005`)** — preserve test-derived labeling and require evidence before defect confirmation.
2. **Shared demo volatility (`RSK-002`, `RSK-007`)** — create identifiable data and capture the execution environment/time.
3. **Historical evidence gaps (`RSK-003`, `RSK-012`)** — controlled re-execution must record Actual Result and environment metadata.
4. **Core access/dependency failures (`RSK-004`, `RSK-006`)** — smoke authentication and create foundational employee/user data before downstream workflows.

## 4. Risk-Based Execution Implications

High-risk functions are scheduled early. A blocker in Login, Session, Admin access, or PIM employee setup can invalidate large portions of later execution, so these areas are validated before Leave, Time, Recruitment, and self-service dependent flows.

Low-priority cases remain in regression scope; risk-based ordering is not a mechanism for silently removing them.

## 5. Risk Review Cadence

Review the register:

- Before controlled execution.
- After smoke.
- When a new Critical/High defect is raised.
- When environment/demo state changes.
- Before deciding impacted regression scope.
- At test closure.

Update Probability/Impact only when evidence changes the exposure. Preserve revision rationale.

## 6. Risk Acceptance

A High residual risk may remain open only with explicit rationale in `06_Test_Closure/Known_Limitations.md` and the final Test Summary. QA should not convert unresolved exposure into a pass-rate-only release recommendation.

## 7. Related Documents

- `Test_Plan.md`
- `Test_Strategy.md`
- `Test_Environment.md`
- `Test_Estimation.md`
- `Requirement_Traceability_Matrix.xlsx`
- `../01_Project_Information/Requirement_Analysis.md`
- `../01_Project_Information/Application_Scope.md`

## 8. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Established risk register, scoring model, mitigations, and execution implications. | Quality Assurance |

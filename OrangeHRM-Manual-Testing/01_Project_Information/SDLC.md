# OrangeHRM SDLC and QA Integration

| Document Control | Value |
|---|---|
| Project | OrangeHRM Manual Testing |
| Document | SDLC |
| Version | 1.0 |
| Status | Baselined |
| Owner | Quality Assurance |
| Baseline Date | 10 September 2026 |

## 1. Context

OrangeHRM Demo is treated in this portfolio as an externally developed, deployed application. This repository does **not** claim knowledge of OrangeHRM's internal engineering lifecycle, release governance, source code, unit testing, CI/CD pipeline, or vendor acceptance process.

For portfolio control, QA work is integrated into an iterative software delivery model that mirrors how a manual QA engineer would operate within a product team.

## 2. QA Integration Across an Iterative SDLC

| SDLC Stage | Engineering/Product Focus | QA Lead / QA Engineer Contribution | Repository Evidence |
|---|---|---|---|
| Discovery / Requirements | Define business problem, workflow, acceptance intent | Challenge ambiguity, identify testability, establish requirement IDs, identify risks and dependencies | `Requirement_Analysis.md`, `Application_Scope.md`, `Test_Objectives.md` |
| Design | Define UI/workflow/data/permission behavior | Review testability, role impacts, validation rules, negative paths, data needs | `02_Test_Planning/Test_Strategy.md`, `Risk_Assessment.md` |
| Implementation | Build or configure application changes | Prepare/maintain test cases, data, smoke/regression impact, environment readiness | `03_Test_Design/`, `02_Test_Planning/Test_Environment.md` |
| Build / Deployment to Test | Deploy testable increment | Verify environment/build, run smoke checks, confirm blockers before broader execution | `Smoke_Test_Suite.xlsx`, `04_Test_Execution/Execution_Summary.xlsx` |
| Verification | Validate requirements and risks | Execute functional/regression tests, capture evidence, raise defects, maintain RTM | `04_Test_Execution/`, `05_Defect_Reports/`, RTM |
| Fix / Retest | Correct verified defects | Retest defect, run sanity and impacted regression, update disposition | `Sanity_Test_Suite.xlsx`, `Regression_Test_Suite.xlsx`, Defect Log |
| Release Readiness | Decide whether quality is acceptable for release | Present quality status, residual risk, failed/blocked cases, defect exposure, recommendation | `06_Test_Closure/Test_Summary_Report.md`, `Metrics_Report.md` |
| Post-Release / Improvement | Learn from release and production feedback | Record lessons, improve suites, identify automation candidates, refine risk model | `Lessons_Learned.md`, `Future_Improvements.md` |

## 3. Quality Feedback Loop

The repository uses a closed QA feedback loop:

`Requirement → Design Risk → Test Coverage → Execution Evidence → Defect/Clarification → Fix/Decision → Regression → Closure → Improvement`

A defect can reveal a missing or ambiguous requirement. A clarification can change an expected result. Both changes must flow back through Requirement Analysis and the RTM rather than being handled only in the defect record.

## 4. Definition of Ready for QA

A change or testable increment is considered ready for QA when the team has sufficient information to execute without guessing:

- Intended behavior is understood or ambiguity is explicitly recorded.
- Test environment is accessible.
- Required role/permissions are available.
- Required test data can be created or located.
- Relevant build/environment identifier is known where available.
- Known deployment limitations are communicated.
- Impacted tests can be identified.

For the existing baseline, missing build and detailed Actual Result information are documented limitations rather than assumed values.

## 5. Definition of Done from QA Perspective

A testable increment is QA-complete when:

- Agreed in-scope tests have a recorded outcome.
- Failed tests have a disposition.
- Fixed defects have successful retest evidence.
- Relevant regression has completed.
- Critical-path exposure is understood.
- Residual risks/limitations are documented.
- RTM and execution metrics reconcile.

QA completion does not independently mean a product is released; it provides quality evidence for the release decision.

## 6. Change Impact Assessment

For any application change, QA evaluates impact across:

- Directly changed function.
- Upstream prerequisites.
- Downstream workflows.
- Shared data entities.
- Role/permission behavior.
- Navigation.
- Session/authentication impact.
- Reporting/search/filter impact.
- Existing defects and regression history.

This impact assessment determines whether the change requires a targeted sanity run, module regression, cross-module regression, or critical-path execution.

## 7. Relationship to STLC

The SDLC describes where QA participates in product delivery. The [STLC](./STLC.md) describes how QA controls its own testing activities and evidence.

The two are intentionally connected:

- SDLC requirement/design work feeds STLC Requirement Analysis and Planning.
- SDLC implementation/deployment feeds STLC Environment Readiness and Execution.
- SDLC fix cycles feed STLC Retest/Regression.
- SDLC release readiness consumes STLC Closure evidence.

## 8. Repository Governance

All project documentation will use canonical identifiers and controlled cross-references. Test subsets will reference master functional cases rather than creating disconnected copies. Execution metrics will derive from canonical case records. Defect reports will reference the exact failed test and requirement. Closure metrics will reconcile to the same execution source.

This governance is the core mechanism that makes the repository behave like a software-company QA evidence set rather than a static portfolio sample.

## 9. Related Documents

- [Project Overview](./Project_Overview.md)
- [Requirement Analysis](./Requirement_Analysis.md)
- [Application Scope](./Application_Scope.md)
- [STLC](./STLC.md)
- [Test Objectives](./Test_Objectives.md)
- Planned: `../02_Test_Planning/Test_Strategy.md`
- Planned: `../06_Test_Closure/Test_Summary_Report.md`

## 10. Revision History

| Version | Date | Change | Owner |
|---|---|---|---|
| 1.0 | 10 September 2026 | Defined QA integration with an iterative SDLC while separating portfolio controls from OrangeHRM vendor process claims. | Quality Assurance |

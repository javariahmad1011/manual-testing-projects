# Lessons Learned

## Overview

The OrangeHRM manual QA portfolio was built as a traceable test lifecycle rather than as a collection of disconnected spreadsheets. The strongest outcome of the exercise is the consistent linkage between requirements, canonical test cases, execution results, defects, and closure reporting.

## Key Lessons

### 1. Traceability must be established before reporting

Requirement IDs, scenario IDs, and canonical test case IDs were standardized before suite creation and reporting. This prevented the Smoke, Regression, Sanity, Critical Path, RTM, Defect Log, and Execution Report from becoming separate sources of truth.

### 2. Test suites should reference canonical cases, not duplicate them

Smoke, regression, sanity, and critical-path coverage were created by selecting canonical test cases from the functional baseline. This keeps maintenance controlled and prevents conflicting versions of the same scenario.

### 3. Failed status is not the same as a fully evidenced defect

The supplied execution baseline contained four failed test cases but did not retain sufficient detailed Actual Results, screenshots, browser information, or build metadata. Instead of inventing evidence, the failures were converted into defects with the status **Open - Needs Reproduction**.

This improves portfolio credibility and reflects real QA governance.

### 4. Critical-path failures require different treatment

`TC-MYI-004 / BUG-004` appears in the Critical Path suite and concerns ESS authorization. A failure affecting access control and a business-critical path requires stronger closure controls than a cosmetic or low-impact issue.

### 5. Shared demo environments create test-data risk

OrangeHRM Demo is a shared environment. Records, users, leave requests, candidates, and other mutable data may be changed by other users. Test data therefore needs to be recreated or validated before each execution cycle.

### 6. Evidence quality is part of test quality

Execution status without supporting metadata is weaker than a reproducible result with:

- environment identifier,
- browser/version,
- build/version,
- timestamp,
- screenshot,
- exact Actual Result,
- linked defect.

Future cycles should treat evidence capture as part of the Definition of Done for failed tests.

### 7. Closure decisions must separate execution completion from release readiness

The baseline reached 100% execution completion, but unresolved defects and incomplete reproduction evidence mean formal QA closure remains conditional. Completion metrics alone should not be used as a release decision.

## Process Improvements Carried Forward

For future test cycles:

- capture browser/build metadata at execution time;
- record specific Actual Results instead of status-only outcomes;
- attach evidence immediately for failures;
- maintain test data reset/recreation instructions;
- keep sanity scope impact-based;
- review critical-path coverage before every release candidate;
- close defects only after verified retest and RTM update.

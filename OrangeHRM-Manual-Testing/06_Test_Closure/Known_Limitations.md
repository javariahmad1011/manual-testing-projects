# Known Limitations

## Purpose

This document records limitations that affect interpretation of the OrangeHRM manual QA portfolio and prevents unsupported assumptions from being presented as verified product facts.

## Current Limitations

### 1. Formal product requirements were not supplied

No official OrangeHRM PRD, SRS, acceptance-criteria set, or client-approved business requirements were included with the source test workbook.

The requirement baseline in this repository is therefore **QA-derived from the supplied test cases** and is used for traceability rather than presented as vendor-owned contractual requirements.

### 2. Historical failure evidence is incomplete

The four failed source cases did not include complete:

- browser/version,
- application build/version,
- screenshots,
- timestamps,
- detailed UI-level Actual Results.

Because of this, `BUG-001` through `BUG-004` remain **Open - Needs Reproduction**.

### 3. Demo environment behavior may change

The application under test is an OrangeHRM demo environment. Shared/demo data and configuration may change independently of this portfolio.

Results should therefore be understood as a retained QA baseline, not as a guarantee of current vendor production behavior.

### 4. Shared test data may be unstable

Other demo users may create, edit, or remove employees, users, leave requests, timesheets, candidates, and related records.

Data-dependent cases may require recreation of test data before reliable re-execution.

### 5. Cross-browser coverage was not evidenced in the source

The original source did not provide verified browser/version execution metadata for the 96-case baseline.

The repository does not claim browser compatibility testing that cannot be evidenced.

### 6. Non-functional testing is limited

The portfolio primarily covers manual functional QA. It does not claim comprehensive:

- performance/load testing,
- penetration testing,
- accessibility certification,
- API contract testing,
- database validation,
- mobile compatibility,
- disaster recovery,
- production monitoring.

Security-oriented manual checks are included where they existed in the functional baseline, but they do not replace a dedicated security assessment.

### 7. No production data or production access was used

The portfolio is based on demo/synthetic test data. It does not validate production integrations, production permissions, production data quality, or production infrastructure.

### 8. No release build was formally signed off

A formal release-candidate build identifier was not available in the historical source. The closure report therefore does not state that a specific production build was approved for release.

## Impact on Closure

These limitations do not invalidate the portfolio. They define the boundary of what has actually been verified.

The appropriate closure status is:

**Conditional — Pending reproduction and final disposition of BUG-001 through BUG-004.**

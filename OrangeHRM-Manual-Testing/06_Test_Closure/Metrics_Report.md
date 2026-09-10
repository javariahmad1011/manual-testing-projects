# Metrics Report

## Executive Metrics

| Metric | Result |
|---|---:|
| Total Canonical Test Cases | 96 |
| Requirements | 91 |
| Modules Covered | 13 |
| Executed | 96 |
| Passed | 92 |
| Failed | 4 |
| Blocked | 0 |
| Not Executed | 0 |
| Execution Completion | 100.00% |
| Pass Rate | 95.83% |
| Defects Logged | 4 |
| Open Defects | 4 |
| High-Severity Defects | 2 |
| Medium-Severity Defects | 2 |
| High-Priority Defects | 1 |
| Medium-Priority Defects | 3 |
| Unmapped Canonical Test Cases | 0 |

---

## Suite Metrics

| Test Suite | Cases | Share of Canonical Baseline |
|---|---:|---:|
| Smoke | 27 | 28.13% |
| Regression | 96 | 100.00% |
| Sanity | 20 | 20.83% |
| Critical Path | 20 | 20.83% |

Suite percentages are selection metrics and are not additive because the same canonical case may belong to multiple suites.

---

## Module Metrics

| Module | Total | Passed | Failed | Pass Rate | Defects |
|---|---:|---:|---:|---:|---:|
| Login | 12 | 11 | 1 | 91.67% | 1 |
| Forgot Password | 5 | 4 | 1 | 80.00% | 1 |
| Dashboard | 5 | 5 | 0 | 100.00% | 0 |
| Admin | 10 | 10 | 0 | 100.00% | 0 |
| PIM | 16 | 16 | 0 | 100.00% | 0 |
| Leave | 10 | 10 | 0 | 100.00% | 0 |
| Time | 8 | 8 | 0 | 100.00% | 0 |
| Recruitment | 8 | 7 | 1 | 87.50% | 1 |
| My Info | 6 | 5 | 1 | 83.33% | 1 |
| Performance | 5 | 5 | 0 | 100.00% | 0 |
| Directory | 4 | 4 | 0 | 100.00% | 0 |
| Buzz | 3 | 3 | 0 | 100.00% | 0 |
| Session | 4 | 4 | 0 | 100.00% | 0 |

---

## Defect Metrics

| Bug ID | Module | Severity | Priority | Status |
|---|---|---|---|---|
| BUG-001 | Login | Medium | Medium | Open - Needs Reproduction |
| BUG-002 | Forgot Password | High | Medium | Open - Needs Reproduction |
| BUG-003 | Recruitment | Medium | Medium | Open - Needs Reproduction |
| BUG-004 | My Info | High | High | Open - Needs Reproduction |

### Severity Distribution

| Severity | Count | Share |
|---|---:|---:|
| Critical | 0 | 0.00% |
| High | 2 | 50.00% |
| Medium | 2 | 50.00% |
| Low | 0 | 0.00% |

### Priority Distribution

| Priority | Count | Share |
|---|---:|---:|
| High | 1 | 25.00% |
| Medium | 3 | 75.00% |
| Low | 0 | 0.00% |

---

## Traceability Metrics

| Metric | Result |
|---|---:|
| Canonical Cases Mapped to Requirements | 96 |
| Canonical Cases Unmapped | 0 |
| Requirement-to-Test Coverage | 100% of canonical baseline |
| Failed Cases Linked to Defects | 4/4 |
| Defects Linked Back to Test Cases | 4/4 |
| Defects Linked Back to Requirements | 4/4 |

---

## Quality Interpretation

The 95.83% pass rate indicates a strong functional baseline, but pass rate alone is not sufficient for closure.

Two High-severity items remain open, including one High-priority authorization issue on the Critical Path suite. The execution baseline therefore supports **conditional closure only** until the failed scenarios are reproduced and dispositioned.

---

## Metric Governance Notes

- Metrics are calculated from the retained 96-case canonical execution baseline.
- No blocked or not-executed cases were recorded.
- No additional defects were created beyond the four evidence-backed failed cases.
- Historical browser/build/screenshot evidence was not available and is not represented as complete.
- Suite membership may overlap; suite totals must not be summed to infer unique coverage.

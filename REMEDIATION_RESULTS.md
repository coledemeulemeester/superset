# Vulnerability Remediation Results

Automated scan and remediation performed by the [Event-Driven Vulnerability Remediation System](https://github.com/coledemeulemeester/Cognition-Event-Driven-Vulnerability-Remediation-System).

## Scan Summary

- **Target**: [coledemeulemeester/superset](https://github.com/coledemeulemeester/superset) (fork of [apache/superset](https://github.com/apache/superset))
- **Scanner**: `pip-audit` with severity enrichment from the [OSV API](https://osv.dev/)
- **Vulnerabilities Found**: 14
- **Severity Breakdown**: 2 high, 10 medium, 2 unknown
- **Remediation Engine**: [Devin API](https://docs.devin.ai/api-reference/overview) (hybrid auth mode — v1 personal key for session creation, v3 service key for polling)

## Remediation Status

### Fully Remediated (PR Merged)

| CVE | Package | Version | Fix | Severity | Issue | PR |
|-----|---------|---------|-----|----------|-------|-----|
| CVE-2026-23949 | jaraco-context | 6.0.1 | 6.1.0 | high | [#26](https://github.com/coledemeulemeester/superset/issues/26) | [#33](https://github.com/coledemeulemeester/superset/pull/33) |
| CVE-2026-24486 | python-multipart | 0.0.20 | 0.0.22 | high | [#27](https://github.com/coledemeulemeester/superset/issues/27) | [#35](https://github.com/coledemeulemeester/superset/pull/35) |

### PR Open (Awaiting Review/Merge)

| CVE | Package | Version | Fix | Severity | Issue | PR |
|-----|---------|---------|-----|----------|-------|-----|
| CVE-2026-27205 | flask | 2.3.3 | 3.1.3 | medium | [#18](https://github.com/coledemeulemeester/superset/issues/18) | [#20](https://github.com/coledemeulemeester/superset/pull/20) |
| GHSA-jj8c-mmj3-mmgv | authlib | 1.6.9 | 1.6.11 | medium | [#17](https://github.com/coledemeulemeester/superset/issues/17) | [#19](https://github.com/coledemeulemeester/superset/pull/19) |
| CVE-2025-61911 | python-ldap | 3.4.4 | 3.4.5 | medium | [#25](https://github.com/coledemeulemeester/superset/issues/25) | [#34](https://github.com/coledemeulemeester/superset/pull/34) |
| CVE-2025-61912 | python-ldap | 3.4.4 | 3.4.5 | medium | [#23](https://github.com/coledemeulemeester/superset/issues/23) | [#36](https://github.com/coledemeulemeester/superset/pull/36) |
| CVE-2026-1703 | pip | 25.1.1 | 26.0 | medium | [#29](https://github.com/coledemeulemeester/superset/issues/29) | [#37](https://github.com/coledemeulemeester/superset/pull/37) |

### Issue Created (Queued for Next Batch)

These vulnerabilities have GitHub issues created but have not yet been assigned a Devin session. The system dispatches sessions in batches of 3, sorted by severity. These will be picked up on subsequent scan cycles.

| CVE | Package | Version | Fix | Severity | Issue |
|-----|---------|---------|-----|----------|-------|
| CVE-2026-22702 | virtualenv | 20.29.2 | — | medium | [#21](https://github.com/coledemeulemeester/superset/issues/21) |
| CVE-2026-3219 | pip | 25.1.1 | — | unknown | [#22](https://github.com/coledemeulemeester/superset/issues/22) |
| CVE-2026-40347 | python-multipart | 0.0.20 | — | unknown | [#24](https://github.com/coledemeulemeester/superset/issues/24) |
| CVE-2025-61911 | python-ldap | 3.4.4 | 3.4.5 | medium | [#25](https://github.com/coledemeulemeester/superset/issues/25) |
| CVE-2025-66034 | fonttools | 4.55.0 | — | medium | [#28](https://github.com/coledemeulemeester/superset/issues/28) |
| CVE-2025-71176 | pytest | 7.4.4 | — | medium | [#30](https://github.com/coledemeulemeester/superset/issues/30) |
| CVE-2026-0994 | protobuf | 4.25.8 | — | medium | [#31](https://github.com/coledemeulemeester/superset/issues/31) |
| CVE-2025-8869 | pip | 25.1.1 | — | medium | [#32](https://github.com/coledemeulemeester/superset/issues/32) |

### Superseded PRs

These PRs were created during earlier scan runs and superseded by newer PRs for the same vulnerability.

| CVE | PR | Superseded By |
|-----|-----|---------------|
| CVE-2026-27205 | [#15](https://github.com/coledemeulemeester/superset/pull/15) (closed) | [#20](https://github.com/coledemeulemeester/superset/pull/20) |
| GHSA-jj8c-mmj3-mmgv | [#16](https://github.com/coledemeulemeester/superset/pull/16) (closed) | [#19](https://github.com/coledemeulemeester/superset/pull/19) |

## How This Was Generated

1. The remediation system cloned this repository and ran `pip-audit` against all Python requirements files
2. Each vulnerability was enriched with severity data from the [OSV API](https://osv.dev/) using CVSS v3 scoring
3. GitHub issues were created automatically for all 14 vulnerabilities (Phase 1 — parallel)
4. Devin API sessions were dispatched for the highest-severity vulnerabilities first, in batches of 3 (Phase 2 — severity-ordered)
5. A background polling job monitored Devin's progress via the messages API and updated the dashboard when PRs were created
6. The two high-severity PRs (#33 and #35) were reviewed and merged manually

## System Repository

The remediation system source code, architecture documentation, and full test suite are available at:

**[coledemeulemeester/Cognition-Event-Driven-Vulnerability-Remediation-System](https://github.com/coledemeulemeester/Cognition-Event-Driven-Vulnerability-Remediation-System)**

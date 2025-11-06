# Azimuth Guardrails Governance Operating Manual
Generated: 2025-11-06 00:30:16

## Purpose
Define the repeatable process that keeps Azimuth’s repos and AI agents aligned, self-improving, and safe as the platform scales.

## 1. Loop Overview
Each month we:
1. **Collect** guardrail issues from every repo (via issue template).
2. **Reconcile** them centrally—deduplicate, rank by priority.
3. **Reinforce** by converting accepted findings into code tests, lint rules, doc updates, or monitoring alerts.

This forms an ongoing “collect → reconcile → reinforce” loop.

## 2. Roles
- **Repo Maintainer:** Files or triages guardrail issues locally.
- **Agents:** Submit intake forms automatically when encountering known pitfalls.
- **Coordinator (you):** Consolidates across repos, prioritizes, and assigns fixes.
- **Governance Bot (optional):** Automates scoring and routing to project boards.

## 3. Cadence
| Activity | Frequency | Output |
|-----------|------------|--------|
| Guardrail intake | Continuous | Issues labeled and triaged |
| Consolidation | Monthly | Unified CSV/JSON summary |
| Reinforcement | Monthly | Updated guardrails, new automation |
| Review meeting | Quarterly | Trend analysis, deprecation of stale rules |

## 4. Scoring Rubric
Severity: S1–S4, Frequency: F1–F3.  
Priority = (S1=8, S2=5, S3=3, S4=1) + (F1=3, F2=2, F3=1).

## 5. Consolidation Format
When exporting feedback:
- `repo`, `issue_number`, `area`, `severity`, `frequency`, `priority_score`
- `summary`, `repro_steps`, `proposed_fix`, `guardrail_section_ref`
- `automation_type` (doc | lint | test | assertion | monitor)
- `status`, `owner`, `eta`, `example_links`

## 6. Automation Hooks
- **GitHub Actions:** Auto-score issues, apply labels, assign owners.
- **Pre-commit:** Ban `SELECT *`, enforce peer filters.
- **CI:** Validate JSON schemas, AI contract versions.
- **Dataform tests:** Dedupe OPEID, null guards.
- **Monitoring:** Cost alerts + latency SLO dashboards.

## 7. Artifacts Required in Every Repo
- `/GUARDRAILS.md`
- `/agent_context/ai_contract.json`
- `.github/ISSUE_TEMPLATE/azimuth-guardrails-intake.yml`
- `.github/pull_request_template.md`

## 8. Definition of Done (Cycle)
- All open guardrail issues triaged.
- Updated guardrails merged and tagged with new `ai_contract_version`.
- Validation checks green across repos.
- Summary report generated (CSV/JSON) and archived in governance repo.

## 9. Long-Term Vision
A self-healing, continuously aligned AI‑assisted development ecosystem:
- Each agent learns from systemwide feedback.
- Governance becomes lightweight but ever-present.
- Guardrails evolve from static rules to dynamic, testable contracts.


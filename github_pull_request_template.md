### Guardrails compliance
- [ ] No `SELECT *`; peer filters present (cip4 + degree_level + sector) where applicable
- [ ] API queries are parameterized and bounded (LIMIT/authorized views)
- [ ] AI outputs use strict JSON schema; no placeholders leak to UI
- [ ] GUARDRAILS.md/ai_contract.json updated if contracts changed
- [ ] `AI_CONTRACT_VERSION` bumped if shape changed

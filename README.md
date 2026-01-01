# Evasive AI Lab

Open-source red-teaming lab aligned with **NIST AI 100-2e2025** (Adversarial Machine Learning Taxonomy).

## Charter
- Defensive research only
- Isolated testing on open models
- Results mapped to NISTAML IDs
- Apache 2.0 — full reproduction encouraged

## Baselines

**Overall**: High vulnerability to prompt injection. Long-context and hate-related injections most effective.  
**NIST Mapping**: NISTAML.015 (Indirect Prompt Injection) / .018 (Direct Prompt Injection)

## 📊 Evasive Baselines
*Open reproductions of attacks mapped to NIST AI 100-2e2025*

| Date | Model | Probe Type | NISTAML ID | Success Rate (ASR) | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2025-12-26 | Phi-3-mini-4k-instruct | promptinject | .033 / .041 | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) | Evidence of 3.5x Safety Resistance Gap. |
| 2025-12-26 | Qwen-2-7b-instruct | promptinject | .033 / .041 | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) | Quantifying non-Western alignment resilience. |
| 2025-12-26 | Llama-3.2-3B-Instruct | promptinject | .033 / .041 |HijackHateHumans **54.53%** KillHumans  **26.48%** AttackRogueString **64.77%**| Benchmarking Meta's latest small-language model. |
| 2025-12-26 | Llama-3.2-3B-Instruct | promptinject | .033 / .041 |dan.DAN 100.00% , MitigationBypass 80.00%| Benchmarking Meta's latest small-language model. |


## Roadmap
- Reproduce all major NIST attack classes
- Test more open models (Llama-3.2, Mistral)
- Publish defenses and mitigations
- Extend to IAM integration (IdentityJail)

## Research Note
This work is defensive research in isolated environments. No production systems targeted. Aligns with EU AI Act transparency requirements and NIST encouragement of robustness testing.

Reference:
- NIST AI 100-2e2025: https://doi.org/10.6028/NIST.AI.100-2e2025
- EU AI Act (2024/1689): https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R1689

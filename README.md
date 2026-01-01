# Evasive AI Lab

Open-source red-teaming lab aligned with **NIST AI 100-2e2025** (Adversarial Machine Learning Taxonomy).

## Charter
- Defensive research only
- All baselines mapped to NISTAML IDs
- Apache 2.0 — full reproduction encouraged


## 📊 Evasive Baselines
*Open reproductions of attacks mapped to NIST AI 100-2e2025*

| Date | Model | Probe Type | NISTAML ID | Success Rate (ASR) | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2025-12-26 | Phi-3-mini-4k-instruct | promptinject | .033 / .041 | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) | Evidence of 3.5x Safety Resistance Gap. |
| 2025-12-26 | Qwen-2-7b-instruct | promptinject | .033 / .041 | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) | Quantifying non-Western alignment resilience. |
| 2025-12-26 | Llama-3.2-3B-Instruct | promptinject | .033 / .041 |HijackHateHumans **54.53%** KillHumans  **26.48%** AttackRogueString **64.77%**| Benchmarking Meta's latest small-language model. |


## Research Note

This project implements open-source red-teaming aligned with **NIST AI 100-2e2025** ("Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations", March 2025) and operates within the framework of the **EU AI Act (Regulation (EU) 2024/1689)**.

### Key Alignment Points

- **Defensive Purpose Only**: All testing is conducted in isolated environments on open models. No production systems are targeted. This aligns with the EU AI Act's encouragement of transparency and robustness testing for high-risk AI systems (Article 15, Recital 61).

- **Transparency & Reproducibility**: All baselines are publicly documented with exact probe configurations, success rates, and NISTAML ID mapping. This supports the EU AI Act's requirements for technical documentation and conformity assessment of high-risk AI (Annex IV).

- **Risk Assessment Focus**: Prompt injection results (NISTAML.015 / .018) contribute to identifying "manipulation" risks as defined in both the NIST taxonomy and EU AI Act prohibited practices (Article 5) when applicable.

- **No Prohibited Practices**: No testing involves deception, exploitation of vulnerabilities in vulnerable groups, or subliminal techniques (EU AI Act Article 5).

This work is purely defensive research to improve AI safety through open measurement and comparison.

Reference Documents:
- NIST AI 100-2e2025: https://doi.org/10.6028/NIST.AI.100-2e2025
- EU AI Act (2024/1689): https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R1689|

## Roadmap
- Reproduce all major attack classes
- Publish ghost LoRAs and defenses
- Extend to IAM integration (IdentityJail repo coming)

Reference: NIST AI 100-2e2025 (images below)
## Roadmap[
[roadmap.md](roadmap.md)](https://github.com/Aswinbalaji14/evasive-lab-charter/edit/main/README.md)
## Lab Home
Charter & overview: https://github.com/Aswinbalaji14/evasive-lab-charter

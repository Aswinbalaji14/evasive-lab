# Evasive AI Lab

Open-source red-teaming lab aligned with **NIST AI 100-2e2025** (Adversarial Machine Learning Taxonomy).

## Charter
- Defensive research only
- All baselines mapped to NISTAML IDs
- Apache 2.0 — full reproduction encouraged

| Date       | Model              | Probe Type     | NISTAML ID     | Success Rate |
|------------|--------------------|----------------|----------------|--------------|
| 2025-12-17 | Phi-3-mini         | promptinject   | .015 / .018    | 57.51%      |
| 2025-12-26 | Qwen2-7B-Instruct  | promptinject   | .015 / .018    | 71.95% (Hate) / 20.16% (Kill) — partial |

## Roadmap
- Reproduce all major attack classes
- Publish ghost LoRAs and defenses
- Extend to IAM integration (IdentityJail repo coming)

Reference: NIST AI 100-2e2025 (images below)
## Roadmap[
[roadmap.md](roadmap.md)](https://github.com/Aswinbalaji14/evasive-lab-charter/edit/main/README.md)
## Lab Home
Charter & overview: https://github.com/Aswinbalaji14/evasive-lab-charter

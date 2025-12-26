# Evasive AI Lab

Open-source red-teaming lab aligned with **NIST AI 100-2e2025** (Adversarial Machine Learning Taxonomy).

## Charter
- Defensive research only
- All baselines mapped to NISTAML IDs
- Apache 2.0 — full reproduction encouraged


Model: Phi-3-mini-4k-instruct
Date: 2025-12-17
Tool: Garak v0.13.3
Results:

HijackHateHumans + AttackRogueString: 57.51% attack success (939/2210)
HijackKillHumans + AttackRogueString: 29.16% attack success (624/2140)
HijackLongPrompt + AttackRogueString: 63.96% attack success (1356/2120)

Overall: High vulnerability to prompt injection. Long-context and hate-related injections most effective.
NIST Mapping: NISTAML.015 (Indirect Prompt Injection) / .018 (Direct Prompt Injection)

| Date       | Model              | Probe Type     | NISTAML ID     | Success Rate |
|------------|--------------------|----------------|----------------|--------------|
| 2025-12-17 | Phi-3-mini         | promptinject   | .015 / .018    | 57.51%      |
| 2025-12-26 | Qwen2-7B-Instruct  | promptinject   | .015 / .018    | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) |

## Roadmap
- Reproduce all major attack classes
- Publish ghost LoRAs and defenses
- Extend to IAM integration (IdentityJail repo coming)

Reference: NIST AI 100-2e2025 (images below)
## Roadmap[
[roadmap.md](roadmap.md)](https://github.com/Aswinbalaji14/evasive-lab-charter/edit/main/README.md)
## Lab Home
Charter & overview: https://github.com/Aswinbalaji14/evasive-lab-charter

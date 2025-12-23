# Evasive AI Lab

Open-source red-teaming lab aligned with **NIST AI 100-2e2025** (Adversarial Machine Learning Taxonomy).

## Charter
- Defensive research only
- All baselines mapped to NISTAML IDs
- Apache 2.0 — full reproduction encouraged

## First Baseline (2025-12-17)
Model: Phi-3-mini-4k-instruct  
Probe: promptinject (Garak v0.13.3)  
Results:
- AttackRogueString: **57.51%** success
- HijackKillHumans: **29.16%**
- HijackLongPrompt: **63.96%**
- NISTAML.015 (Indirect Prompt Injection) / .018 (Direct Prompt Injection)

High vulnerability confirmed on open 3.8B model.

Full report coming in /baselines folder.

## Second Baseline (2025-12-20)
# Qwen/Qwen2-7B-Instruct Prompt Injection (Partial – GPU limit hit)
Date: 2025-12-23  
Tool: Garak v0.13.3 (HF Inference API)

## Partial Results
- AttackRogueString: 68.14% success (one variant)
- AttackRogueString: 21.45% success (another variant)
- Run interrupted by GPU quota — full rerun pending

Shows high variation in injection effectiveness.
NISTAML.015 / .018

## Roadmap
- Reproduce all major attack classes
- Publish ghost LoRAs and defenses
- Extend to IAM integration (IdentityJail repo coming)

Reference: NIST AI 100-2e2025 (images below)
## Roadmap[
[roadmap.md](roadmap.md)](https://github.com/Aswinbalaji14/evasive-lab-charter/edit/main/README.md)
## Lab Home
Charter & overview: https://github.com/Aswinbalaji14/evasive-lab-charter

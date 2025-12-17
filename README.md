# evasive-lab
# Evasive AI Lab
Open red-teaming lab aligned with NIST AI 100-2e2025.

## Charter
[[charter.md](charter.md)](https://github.com/Aswinbalaji14/evasive-lab-charter/blob/main/Charter)

## Baselines
# Evasive Baselines
Open reproductions of attacks from NIST AI 100-2e2025

First baseline: Prompt injection on Phi-3-mini-4k-instruct (Garak v0.13.3, Colab T4)

| Probe Variant       | Success Rate | NISTAML ID     |
|---------------------|--------------|----------------|
| AttackRogueString   | 57.51%      | .015 / .018    |
| HijackKillHumans    | 29.16%      | .015 / .018    |
| HijackLongPrompt    | 63.96%      | .015 / .018    |

High vulnerability to prompt injection confirmed on 3.8B open model.

## Roadmap[
[roadmap.md](roadmap.md)](https://github.com/Aswinbalaji14/evasive-lab-charter/edit/main/README.md)
## Lab Home
Charter & overview: https://github.com/Aswinbalaji14/evasive-lab-charter

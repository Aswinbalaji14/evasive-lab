# Evasive AI Lab

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20363724.svg)](https://doi.org/10.5281/zenodo.20363724)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()

📄 **Published Paper:** [The Summarization Trap — Zenodo](https://doi.org/10.5281/zenodo.20363724)

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

| Date | Model | Probe Type | NISTAML ID | ATLAS ID | OWASP ID | ASR | Notes |
|------|--------|-------------|-------------|-----------|-----------|------|--------|
| 2025-12-26 | Phi-3-mini-4k-instruct | promptinject | .033 / .041 | - | - | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) | Evidence of 3.5x Safety Resistance Gap |
| 2025-12-26 | Qwen-2-7b-instruct | promptinject | .033 / .041 | - | - | 71.95% (Hate) / 20.16% (Kill) / 51.95% (Long) | Quantifying non-Western alignment resilience |
| 2025-12-26 | Llama-3.2-3B-Instruct | promptinject | .033 / .041 | - | - | HijackHateHumans 54.53% / KillHumans 26.48% / AttackRogueString 64.77% | Benchmarking Meta's latest small-language model |
| 2025-12-26 | Llama-3.2-3B-Instruct | promptinject | .033 / .041 | - | - | dan.DAN 100% / MitigationBypass 80% | Benchmarking Meta's latest small-language model |
| 2026-01-05 | Llama-3.2-3B-Instruct | dan.Dan_11_0 | .017 | - | - | dan.DAN 100% / MitigationBypass 80% | Hardened Run: System prompt defense failed |
| 2026-01-13 | Llama-3.2-3B-Instruct (4-bit) | dan.Dan_11_0 | .017 | - | - | dan.DAN 100% / MitigationBypass 80% | Quantization Audit: No safety delta |
| 2026-01-13 | Phi-3.5-mini-instruct | dan.Dan_11_0 | 0.17 | - | - | dan.DAN 0% / MitigationBypass 0% | Audit Success: resisted jailbreak |
| 2026-03-01 | Phi-3.5-mini-instruct | latentinject | 037 | - | - | TriggerList 28.52% / Toxic 1.17% | Baseline RAG Failure |
| 2026-03-07 | Phi-3.5-mini-instruct | latentinject | 037 | - | - | TriggerList 26.95% / Toxic 1.17% | Mitigation Audit failed |
| 2026-03-07 | Llama-3.2-3B-Instruct | latentinject | 037 | - | - | TriggerList 34.38% / Toxic 0% | Critical vulnerability |
| 2026-03-30 | Llama-3.2-3B-Instruct (float16) | agentic-indirect-inject | NISTAML.037 | AML.T0051 | LLM01 | Resume 5% / Support 0% / ResearchDoc 15% | - |
| 2026-04-04 | Llama-3.2-3B-Instruct (float16) | 5A-trigger-isolation | .037 / .015 | AML.T0051 | LLM01 | TriggerList **65.00%** (13/20) | Phase 5A: Trigger changed from CONFIRMED → XRAY7 (unnatural). ASR rose +50%. Genuine injection confirmed as separate mechanism |
| 2026-04-04 | Llama-3.2-3B-Instruct (float16) | 5B-role-isolation | .037 | AML.T0051 | LLM01 | TriggerList **0.00%** (0/20) | Phase 5B: Role changed from open summariser → constrained classifier. ASR dropped to zero. Lexical bleed mechanism confirmed and eliminated |
| 2026-04-04 | Phi-3.5-mini-instruct (float16) | 5A-trigger-isolation | NISTAML.037 | AML.T0051 | LLM01 | TriggerList 60.00% | Multi-model Phase 5A. Delta vs Llama 5A (65.0%): -5.00% |
| 2026-04-04 | Phi-3.5-mini-instruct (float16) | 5B-role-isolation | NISTAML.037 | AML.T0051 | LLM01 | TriggerList 0.00% | Multi-model Phase 5B. Delta vs Llama 5B (0.0%): +0.00% |
| 2026-04-05 | Mistral-7B-Instruct-v0.3 (float16) | 5A-trigger-isolation | NISTAML.037 | AML.T0051 | LLM01 | TriggerList 75.00% | Multi-model Phase 5A. Delta vs Llama 5A (65.00%): +10.00% |
| 2026-04-05 | Mistral-7B-Instruct-v0.3 (float16) | 5B-role-isolation | NISTAML.037 | AML.T0051 | LLM01 | TriggerList 0.00% | Multi-model Phase 5B. Delta vs Llama 5B (0.00%): +0.00% |
| 2026-04-18 | MLP(128,64,32)-wine | model-extraction | NISTAML.031 | AML.T0030 | LLM10 | Best fidelity 100.00% at budget 100 (logistic_regression) | CRITICAL extraction risk. Target acc 96.30%. |
| 2026-04-22 | MLP(128,64,32)-wine | evasivebench-v0.1 | NISTAML.031/.033 | AML.T0024/T0030 | LLM06/LLM10 | MI AUC 0.5273 / ME Fidelity 100.00% | Overall: CRITICAL. 2/4 attacks CRITICAL. |
| 2026-05-26 | PromptGuard-86M | guard-eval-phase9 | NISTAML.015 | AML.T0054 | LLM07 | Detection Rate **100%** / Bypass 0% / FPR 0% / Latency 128ms | Best guard tested. Detected all 10 payloads with confidence 0.986–0.9999 |
| 2026-05-26 | LlamaGuard-3-1B | guard-eval-phase9 | NISTAML.015 | AML.T0054 | LLM07 | Detection Rate **0%** / Bypass **100%** / FPR 0% / Latency 135ms | CRITICAL: Called all 10 injection payloads safe. Not trained for injection patterns — only harmful content categories |
| 2026-05-26 | Keyword Baseline (regex) | guard-eval-phase9 | NISTAML.015 | AML.T0054 | LLM07 | Detection Rate 40% / Bypass 60% / FPR 0% / Latency 1ms | Missed multilingual, unicode, compliance-framed, few-shot, whitespace payloads |
| 2026-05-26 | Llama/Phi/Mistral | trigger-transferability-phase10 | NISTAML.015 | AML.T0051 | LLM01 | TBD — experiment in progress | Phase 10: Testing if payloads crafted on Llama transfer unchanged to Phi and Mistral |


## ⚠️ Security Advisory: Llama-3.2-3B Jailbreak
**Date:** 2026-01-01  
**Vulnerability:** Adversarial Evasion (Jailbreak)  
**NIST ID:** NISTAML.017  
**Finding:** Llama-3.2-3B demonstrated a **100% Attack Success Rate (ASR)** against the `dan.Dan_11_0` roleplay probe. This indicates that the model's instruction-tuned safety layers can be completely bypassed using established adversarial personas.



## ⚠️ Security Advisory: LlamaGuard-3-1B Injection Blind Spot
**Date:** 2026-05-26
**Vulnerability:** Guard Model Failure — Injection Detection Gap
**NIST ID:** NISTAML.015
**Finding:** LlamaGuard-3-1B achieved a **0% Detection Rate** against all 10 RAG injection payloads tested — including XRAY7 triggers, unicode-encoded attacks, multilingual injections, compliance-framed instructions, and few-shot hijacks. LlamaGuard is trained on harmful **content categories** (violence, hate, illegal activity) and is not trained to detect **prompt injection patterns**. Deploying LlamaGuard as a RAG injection filter provides zero protection while adding 135ms latency overhead. **PromptGuard-86M** (86M params) outperformed LlamaGuard-3-1B (1B params) with 100% detection rate and 0.986–0.9999 confidence scores.



## ⚠️ Research Finding: Two Vulnerability Classes in RAG Summariser Pipelines

**Date:** 2026-04-05 (confirmed across 3 models)
**NIST:** NISTAML.037 / NISTAML.015 | **ATLAS:** AML.T0051 | **OWASP:** LLM01

### Cross-model results

| Model | 5A Genuine Injection ASR | 5B Role Fix ASR |
|---|---|---|
| Llama-3.2-3B (Phase 5 baseline) | 65.00% | **0.00%** |
| Phi-3.5-mini-instruct | 60.00% | **0.00%** |
| Mistral-7B-Instruct-v0.3 | **75.00%** | **0.00%** |

### Key findings
- **Role fix is universal:** Constraining victim to a binary classifier drops ASR to exactly 0% on all three models. This is a pipeline architecture fix, not a model fix.
- **Genuine injection is architectural:** 60–75% ASR across three models from different companies with different training. Not a Llama bug — a general vulnerability of the RAG summariser pattern.
- **Safety training does not transfer:** Phi-3.5-mini resisted DAN jailbreaks at 0% (Phase 1) but scored 60% on genuine RAG injection. Different attack surfaces require different defences.
- **Mistral-7B is most vulnerable:** The most widely deployed open RAG model in enterprise showed the highest genuine injection ASR (75%).

---

## ⚠️ Research Finding: Guard Model Evaluation — LlamaGuard vs PromptGuard

**Date:** 2026-05-26
**NIST:** NISTAML.015 | **ATLAS:** AML.T0054 | **OWASP:** LLM07

### Guard model results across 10 injection payloads

| Guard | Detection Rate | Bypass Rate | False Positive Rate | Latency | Verdict |
|---|---|---|---|---|---|
| Keyword Baseline | 40% | 60% | 0% | 1ms | Insufficient |
| PromptGuard-86M | **100%** | **0%** | 0% | 128ms | **Recommended** |
| LlamaGuard-3-1B | **0%** | **100%** | 0% | 135ms | **Do not use for injection** |

### Key findings
- **LlamaGuard is blind to injection patterns:** Trained on harmful content categories, not adversarial instruction structure. Called all 10 payloads — including XRAY7, multilingual, authority impersonation — `safe`.
- **PromptGuard detects what LlamaGuard misses:** Specifically trained for injection/jailbreak detection. 100% DR with confidence 0.986–0.9999 across all 10 payload categories.
- **Task-specific beats general-purpose:** 86M parameter PromptGuard outperformed 1B parameter LlamaGuard because task alignment matters more than model size.
- **Best defence remains architectural:** Role constraint (Phase 5B) — 0% ASR, 0ms overhead, zero cost — outperforms all guards tested.

### Recommended defence stack
1. **Role Constraint (Phase 5B)** → 0% ASR, 0ms overhead — use for classification/routing RAG tasks
2. **PromptGuard-86M** → 100% DR, 128ms overhead — use as pre-RAG input filter
3. **Do not use LlamaGuard alone** for RAG injection detection

---

## Prior Work and Attribution

- **NVIDIA Garak:** Phases 1–3 probes (promptinject, latentinject, dan) adapted from Garak's probe library.
- **MITRE ATLAS:** Technique mapping for all experiments.
- **NIST AI 100-2e2025:** Formal AML taxonomy for all NISTAML ID mappings.
- **OWASP LLM Top 10:** Practitioner-facing vulnerability classification.

---

## Ethical Use

Defensive security research only. All experiments on open-source models in isolated environments. No production systems targeted. Use responsibly with human oversight only.

---

## Roadmap

- [x] Phases 1–3: Garak-based baselines (promptinject, DAN, latentinject)
- [x] Phase 4: Agentic attack loop — 70B attacker vs 3B victim
- [x] Phase 5: Mechanistic isolation — lexical bleed vs genuine injection
- [x] Phase 5 Multi-Model: Cross-model validation (Llama, Phi, Mistral)
- [x] Phase 6: Membership inference (NISTAML.033) — AUC 0.52–0.57 LOW risk
- [x] Phase 7: Model extraction (NISTAML.031) — 100% fidelity at 100 queries CRITICAL
- [x] Phase 8: EvasiveBench v0.1 — 2/4 attack vectors CRITICAL
- [x] Phase 9: Guard model evaluation — LlamaGuard 0% DR, PromptGuard 100% DR
- [ ] Phase 10: Trigger transferability — universal RAG injection triggers (in progress)
- [ ] arXiv cs.CR submission

---

## References

- NIST AI 100-2e2025: <https://doi.org/10.6028/NIST.AI.100-2e2025>
- MITRE ATLAS: <https://atlas.mitre.org>
- NVIDIA Garak: <https://github.com/NVIDIA/garak>
- OWASP LLM Top 10: <https://owasp.org/www-project-top-10-for-large-language-model-applications>
- EU AI Act (2024/1689): <https://eur-lex.europa.eu/l



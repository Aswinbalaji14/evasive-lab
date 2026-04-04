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

## ⚠️ Security Advisory: Llama-3.2-3B Jailbreak
**Date:** 2026-01-01  
**Vulnerability:** Adversarial Evasion (Jailbreak)  
**NIST ID:** NISTAML.017  
**Finding:** Llama-3.2-3B demonstrated a **100% Attack Success Rate (ASR)** against the `dan.Dan_11_0` roleplay probe. This indicates that the model's instruction-tuned safety layers can be completely bypassed using established adversarial personas.


## ⚠️ Research Finding: Lexical Bleed in RAG Summarizers
 
**Date:** 2026-03-30
**Vulnerability:** Lexical Bleed in RAG Pipeline Summarization
**NIST ID:** NISTAML.037
**ATLAS ID:** AML.T0051
**OWASP ID:** LLM01
 
**Finding:** Phase 4 identified that Llama-3.2-3B-Instruct in research
summarization role reproduces trigger vocabulary from adversarial source
documents without following injected instructions. This lexical bleed
mechanism achieves 15% Trigger List ASR and is distinct from traditional
prompt injection — standard instruction-hierarchy defenses do not address it.
 
**Affected deployment pattern:** Any LLM summarizer that reads and echoes
external document content without output sanitization.
**Mitigation:** Output filtering layer, paraphrasing output, or constrained
classification roles rather than open summarization.

## ⚠️ Research Finding: Two Vulnerability Classes in RAG Summarisers

**Date:** 2026-04-04 (confirmed across Phases 4 and 5)  
**NIST ID:** NISTAML.037 / NISTAML.015 | **ATLAS ID:** AML.T0051 | **OWASP:** LLM01  

Phase 5 mechanistically separated two distinct attack types that current ASR metrics conflate:

| Vulnerability | Mechanism | ASR | Defence |
|---------------|------------|------|----------|
| **Lexical Bleed** | Summariser echoes natural vocabulary from source document | ~15% | Constrain the output role — use classifier instead of free summariser |
| **Genuine Injection** | Attacker embeds explicit hidden instruction — model follows it | **65%** | Instruction hierarchy enforcement + output filtering |

**Key findings:**
- **5B (role isolation):** Changing victim from open summariser to constrained binary classifier dropped ASR from 15% to **0.00%** across all 20 trials. Lexical bleed is a role architecture problem, not a model problem.  
- **5A (trigger isolation):** Changing trigger from natural word (CONFIRMED) to impossible word (XRAY7) caused ASR to rise from 15% to **65.00%**. When forced to write explicit injections, the 70B attacker is significantly more effective — revealing genuine injection as a separate, more severe vulnerability.  

**Implication:**  
RAG pipelines using open-ended summarisation are structurally more vulnerable than those using constrained output formats. These two vulnerability classes require different defences and should be measured separately.
===========================================================================================================================================================================
## Roadmap
- [x] Phases 1–3: Establish baselines using Garak probes (promptinject, DAN, latentinject)
- [x] Phase 4: Agentic attack loop — 70B attacker vs 3B victim in RAG context
- [x] Phase 5: Mechanistic isolation — prove lexical bleed vs genuine injection are separate classes
- [ ] Phase 5 multi-model: Run same experiments on Phi-3.5-mini, Qwen-2-7B, Mistral-7B
- [ ] Phase 6: Membership inference baselines (NISTAML.033)
- [ ] Phase 7: Model extraction (NISTAML.031)
- [ ] Phase 8: EvasiveBench v0.1 + arXiv preprint

## References

- NIST AI 100-2e2025: <https://doi.org/10.6028/NIST.AI.100-2e2025>
- MITRE ATLAS: <https://atlas.mitre.org>
- NVIDIA Garak: <https://github.com/NVIDIA/garak>
- OWASP LLM Top 10: <https://owasp.org/www-project-top-10-for-large-language-model-applications>
- EU AI Act (2024/1689): <https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R1689>

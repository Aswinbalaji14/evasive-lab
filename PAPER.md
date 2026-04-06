# The Summarization Trap

**Full Title:** The Summarization Trap: Quantifying Role-Based Vulnerabilities and Lexical Hijacking in RAG Pipelines

**Author:** Aswinbalaji14 — Independent Researcher

**Status:** Preprint — submission pending

**arXiv link:** *(will be added once live)*

---

## Abstract

Retrieval-Augmented Generation (RAG) pipelines are increasingly deployed in enterprise AI applications, enabling language models to read and respond based on external documents. This paper presents a systematic experimental study of two distinct vulnerability classes in RAG summariser pipelines: **lexical bleed**, in which a model reproduces attacker-chosen vocabulary naturally present in a source document, and **genuine injection**, in which a model follows explicit adversarial instructions embedded within document content.

We demonstrate that these classes are mechanistically separable, require different defences, and have been conflated by existing Attack Success Rate (ASR) metrics. Results across three models (Llama-3.2-3B, Phi-3.5-mini, Mistral-7B) show that a constrained output role eliminates lexical bleed entirely (0% ASR on all models) while genuine injection persists at 60–75% ASR regardless of model or safety training.

---

## Key Finding

| Vulnerability | ASR | Fix |
|---|---|---|
| Lexical Bleed | ~15% | Constrain output role |
| Genuine Injection | 60–75% across 3 models | Instruction hierarchy + output filtering |

---

## Citation

*(arXiv citation will appear here once submitted)*

---

## Related Files

- `Reports/` — per-phase research reports
- `Evidences/` — raw JSON trial data
- `Methodology/attack_loop.md` — experimental setup description

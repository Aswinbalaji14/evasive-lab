# Contributing to Evasive AI Lab

Thank you for your interest in reproducing or extending this research.

---

## How to Reproduce Phase 5 Results

### What you need

- Google Colab account (free tier works — T4 GPU)
- Groq API key (free tier — groq.com)
- Hugging Face account (free — for gated models like Llama)

### Step by step

**1. Get API keys**
- Groq: sign up at groq.com → API Keys → Create key
- Hugging Face: sign up at huggingface.co → Settings → Access Tokens

**2. Open the notebook**
- Download `phase5_multimodel.ipynb` from this repo
- Upload to Google Colab

**3. Add secrets in Colab**
- Click the key icon (🔑) on the left sidebar
- Add `GROQ_API_KEY` → your Groq key
- Add `Meta` → your Hugging Face token

**4. Set your victim model in Cell 2**
```python
VICTIM_MODEL_ID = "microsoft/Phi-3.5-mini-instruct"   # or
VICTIM_MODEL_ID = "mistralai/Mistral-7B-Instruct-v0.3" # or
VICTIM_MODEL_ID = "meta-llama/Llama-3.2-3B-Instruct"
```

**5. Run all cells in order (1 → 9)**

Cell 9 will auto-download your results as a JSON file.

---

## Expected Results

| Model | 5A ASR (genuine injection) | 5B ASR (role isolation) |
|---|---|---|
| Llama-3.2-3B | ~65% | 0% |
| Phi-3.5-mini | ~60% | 0% |
| Mistral-7B | ~75% | 0% |

Small variance (±10%) is expected due to attacker model temperature.

---

## How to Contribute

**New victim models** — run the Phase 5 multi-model notebook on a model not yet tested and open an issue with your Cell 8 output. We will add it to the baselines table.

**New scenarios** — Phase 4 used three RAG scenarios (resume, support ticket, research doc). New scenarios representing different enterprise RAG deployments are welcome.

**Mitigations** — if you test a defence (output filtering, spotlighting, etc.) against genuine injection and measure the ASR delta, open an issue with your methodology and results.

**Bug reports** — if you cannot reproduce a result, open an issue with your environment details (GPU, CUDA version, model version).

---

## Code of Conduct

- Defensive research only
- No testing on production systems
- No distribution of exploit payloads outside research context
- Credit prior work appropriately

---

## Taxonomy Reference

All contributions should map findings to at minimum one NISTAML ID from NIST AI 100-2e2025.

- NISTAML.015 — Indirect Prompt Injection
- NISTAML.017 — Direct Prompt Injection / Jailbreak
- NISTAML.037 — Training Data Attacks (applied here to inference-time injection)
- NISTAML.033 — Membership Inference (Phase 6 target)
- NISTAML.031 — Model Extraction (Phase 7 target)

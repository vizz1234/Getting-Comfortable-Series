# Track: LLM Fine-Tuning, PEFT & Alignment

> **"Don't simplify the topic. Simplify the path to understanding it."**

This track takes you from the raw linear algebra of weight matrices and low-rank factorization to production-grade parameter-efficient fine-tuning (LoRA / QLoRA) and preference alignment (DPO)—not by treating libraries as black boxes, but by understanding the exact mathematical and architectural problems each technique solves.

---

## 🧭 The Learning Progression

Every topic in this track follows the signature 6-stage progression designed for genuine engineering intuition:

$$\text{Understand} \longrightarrow \text{Build} \longrightarrow \text{Break} \longrightarrow \text{Introduce Tools} \longrightarrow \text{Apply} \longrightarrow \text{Revisit}$$

1. **Understand:** What is the mathematical and architectural bottleneck? (e.g., $16\text{ GB}$ base weights vs. $64\text{ GB}$ optimizer states).
2. **Build:** Implement the core mechanics from first principles (e.g., write a pure PyTorch `LoRALinear` layer from scratch using $3 \times 3$ toy matrices before touching any library).
3. **Break:** Test failure modes—catastrophic forgetting, loss masking bugs (prompt unmasked vs. masked), and rank misconfigurations.
4. **Introduce Tools:** Introduce Hugging Face `peft`, `trl` (`SFTTrainer`), and 4-bit `bitsandbytes` (QLoRA)—understanding *why* they abstract what they do.
5. **Apply:** Fine-tune modern small language models (SLMs like `Qwen2.5-0.5B` and `SmolLM2-360M`) on realistic production tasks with strict schema adherence.
6. **Revisit:** Jump into [`comfort-refresh.md`](./comfort-refresh.md) months later for a zero-friction 3-minute recap.

---

## ⚡ Zero-Friction Refresher: `comfort-refresh.md`

When returning to this track after weeks or months, you don't need to re-run training loops or wait for models to download. Open the standalone reference:

👉 **[comfort-refresh.md](./comfort-refresh.md)**
* 30-second mental models & matrix factorization diagrams
* Copy-paste production code recipes for PyTorch, `peft`, and `trl`
* The "Break" diagnostic cheat sheet (e.g., how to diagnose prompt regurgitation in 30 seconds)
* Hardware memory rule-of-thumb estimators ($16\text{ bytes/param}$ vs. $2\text{ bytes/param}$ vs. $0.6\text{ bytes/param}$)

---

## 📚 Curriculum & Notebooks

| Episode | Title & Focus | Hands-on Progression | Notebook | Est. Time |
|---|---|---|:---:|:---:|
| **01** | **Foundations: Matrix Rank & LoRA From Scratch** | Matrix multiplication refresher ➔ visual rank intuition ($3 \times 3$ matrices) ➔ build pure PyTorch `LoRALinear` ➔ why $B=0$ and $A \sim \mathcal{N}(0, \sigma^2)$ ➔ parameter parity check with Hugging Face `peft`. | [01_lora_foundations_and_math.ipynb](./01_lora_foundations_and_math.ipynb) | ~1.5h |
| **02** | **Data Engineering, Chat Templates & Loss Masking** | Inspect raw conversational datasets ➔ Jinja2 chat templates ➔ **The Prompt Parrot Bug** (training without masking) ➔ enforce completion-only loss masking (`-100` tokens) with `DataCollatorForCompletionOnlyLM`. | [02_data_prep_masking_and_sft.ipynb](./02_data_prep_masking_and_sft.ipynb) | ~2.0h |
| **03** | **Production SFT, QLoRA & Hyperparameter Sweeps** | Train `Qwen2.5-0.5B` on an SRE incident dispatch task using `trl.SFTTrainer` ➔ 4-bit NF4 quantization mechanics (QLoRA) ➔ rank ($r$) and learning rate sweeps ➔ probe catastrophic forgetting on unrelated logic. | [03_production_sft_and_qlora.ipynb](./03_production_sft_and_qlora.ipynb) | ~2.5h |
| **04** | **Preference Alignment (DPO) & Local Serving (GGUF)** | Why SFT is not enough ➔ Direct Preference Optimization (DPO) vs. RLHF/GRPO ➔ train with chosen/rejected pairs ➔ fuse adapters (`merge_and_unload`) ➔ export to GGUF format for local serving via Ollama. | [04_preference_dpo_and_serving.ipynb](./04_preference_dpo_and_serving.ipynb) | ~2.0h |

---

## 🎯 What "Comfort" Looks Like in this Track

When you finish this track, you will be able to:
* **Explain** the linear algebra behind rank decomposition and why fine-tuning an SLM is fundamentally different from RAG or system prompting.
* **Calculate** exact GPU memory requirements before launching a training run using the memory rules of thumb.
* **Implement** parameter-efficient adapters from scratch in pure PyTorch and verify parity against production libraries.
* **Diagnose and Fix** the #1 failure mode in fine-tuning: prompt loss contamination and special token mismatches.
* **Train** a small model to achieve $99.5\%+$ deterministic schema compliance at sub-$50\text{ms}$ latency.
* **Serve** your fine-tuned model locally using GGUF and Ollama without vendor lock-in.

---

## 🛠️ Quickstart & Hardware Requirements

### Compute Philosophy: Zero Expensive Hardware Required
All notebooks are engineered to run **locally in 2–8 minutes** on:
- **Apple Silicon (M1/M2/M3/M4):** native acceleration via PyTorch `mps`.
- **Standard Laptop / Desktop CPU:** using lightweight base models (`SmolLM2-135M` and `Qwen2.5-0.5B`).
- **Free Google Colab (Optional):** 1-click Colab badges are included for users who want to scale up to 7B/8B models on a free T4 GPU.

### 1. Install Dependencies
From the track folder:
```bash
pip install -r requirements.txt
```

### 2. Launch
```bash
jupyter lab
```
Start with [`01_lora_foundations_and_math.ipynb`](./01_lora_foundations_and_math.ipynb)!


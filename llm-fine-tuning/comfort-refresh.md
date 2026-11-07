# ⚡ Fine-Tuning & PEFT — 3-Minute Refresher (`comfort-refresh.md`)

> **For returning engineers:** When you need to recall how LoRA works, calculate GPU memory requirements, or fix a fine-tuning bug in production, use this sheet instead of re-reading entire notebooks.

---

## 🧭 The 30-Second Mental Models

### 1. The Core LoRA Equation
In standard fine-tuning, we update all weights: $W = W_0 + \Delta W$.
In LoRA (Low-Rank Adaptation), we freeze the original weight matrix $W_0 \in \mathbb{R}^{d \times k}$ and factorize the update $\Delta W$ into two low-rank matrices:

$$W = W_0 + \frac{\alpha}{r} (B \cdot A)$$

where:
* $W_0 \in \mathbb{R}^{d \times k}$ is frozen (zero gradients computed).
* $A \in \mathbb{R}^{r \times k}$ is initialized with Gaussian noise $\mathcal{N}(0, \sigma^2)$.
* $B \in \mathbb{R}^{d \times r}$ is initialized with **exact zeros**.
* $r \ll \min(d, k)$ is the **Rank** (e.g. $r=8$ or $r=16$).
* $\frac{\alpha}{r}$ is the fixed scaling factor (keeps gradient scale stable when experimenting with different values of $r$).

> **Why $B = 0$ at step 0?**
> Because $B \cdot A = 0 \cdot A = 0$. At step 0, $\Delta W = 0$, guaranteeing the initial model behaves **100% identically to the pre-trained model** with zero drift.

---

### 2. The Rank Intuition (Visual $3 \times 3$ Matrix)

$$\underbrace{\begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix}}_{B \ (3 \times 1)} \times \underbrace{\begin{bmatrix} 4 & 5 & 6 \end{bmatrix}}_{A \ (1 \times 3)} = \underbrace{\begin{bmatrix} 4 & 5 & 6 \\ 8 & 10 & 12 \\ 12 & 15 & 18 \end{bmatrix}}_{\Delta W \ (3 \times 3, \ \text{Rank } 1)}$$

* **Full matrix:** Requires $3 \times 3 = 9$ parameters.
* **Low-rank factorization:** Requires $3 + 3 = 6$ parameters.
* **Scaling to an 8B LLM ($d = 4096$):**
  * Full matrix: $4096 \times 4096 = 16,777,216$ parameters ($67\text{ MB}$).
  * LoRA with $r=8$: $2 \times (4096 \times 8) = 65,536$ parameters ($0.26\text{ MB}$ — **$99.6\%$ reduction!**).

---

### 3. GPU Memory Rule-of-Thumb

To estimate whether a training run fits your hardware:

| Training Mode | Bytes per Parameter | Formula ($P$ = Model Param Count) | Example (0.5B Model) | Example (8B Model) |
|---|:---:|---|:---:|:---:|
| **Full Fine-Tuning** | $\sim 16\text{ bytes}$ | Weights (4B) + Gradients (4B) + Adam States (8B) + Activations | $\approx 10\text{ GB}$ | $\approx 130\text{ GB}+$ |
| **LoRA (16-bit)** | $\sim 2\text{ bytes}$ | Frozen base (2B) + small adapter gradients/states + Activations | $\approx 1.5\text{–}3\text{ GB}$ | $\approx 18\text{–}24\text{ GB}$ |
| **QLoRA (4-bit)** | $\sim 0.6\text{ bytes}$ | 4-bit frozen base (0.5B) + 16-bit adapters + Activations | $\approx 1\text{–}2\text{ GB}$ | $\approx 6\text{–}8\text{ GB}$ |

---

## 🛠️ Canonical Code Recipes

### Recipe 1: Pure PyTorch LoRALinear Layer
```python
import torch
import torch.nn as nn

class LoRALinear(nn.Module):
    def __init__(self, in_features: int, out_features: int, r: int = 8, alpha: int = 16):
        super().__init__()
        # 1. Base linear layer (frozen)
        self.base = nn.Linear(in_features, out_features, bias=False)
        self.base.weight.requires_grad = False
        
        # 2. Low-rank decomposition matrices
        self.r = r
        self.scaling = alpha / r
        self.A = nn.Parameter(torch.randn(r, in_features) * (1 / r**0.5))
        self.B = nn.Parameter(torch.zeros(out_features, r))
        
    def forward(self, x: torch.Tensor) -> torch.Tensor:
        # y = W0*x + (alpha/r) * (x @ A.T @ B.T)
        base_out = self.base(x)
        lora_out = (x @ self.A.T @ self.B.T) * self.scaling
        return base_out + lora_out
```

---

### Recipe 2: Hugging Face `peft` Production Setup
```python
from peft import LoraConfig, get_peft_model, TaskType
from transformers import AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained(
    "Qwen/Qwen2.5-0.5B-Instruct",
    torch_dtype=torch.float32,
    device_map="auto"
)

peft_config = LoraConfig(
    task_type=TaskType.CAUSAL_LM,
    r=8,
    lora_alpha=16,
    lora_dropout=0.05,
    target_modules=["q_proj", "v_proj"]  # Apply to attention projections
)

peft_model = get_peft_model(model, peft_config)
peft_model.print_trainable_parameters()
# Output: trainable params: 294,912 || all params: 494,327,552 || trainable%: 0.059%
```

---

### Recipe 3: Completion-Only Loss Masking (The #1 Bug Fix)
```python
from trl import DataCollatorForCompletionOnlyLM

# Response template marks where the prompt ends and completion begins
response_template = "<|im_start|>assistant\n"
collator = DataCollatorForCompletionOnlyLM(
    response_template=response_template, 
    tokenizer=tokenizer
)
# Prompt tokens are automatically replaced with -100 (ignored by PyTorch CrossEntropyLoss)
```

---

## 🚨 Diagnostic Cheat Sheet: Common Failure Modes

| Symptom | Root Cause | 60-Second Diagnostic & Fix |
|---|---|---|
| **The Prompt Parrot** (Model echoes the question or instructions instead of answering) | Training loss was computed over the prompt tokens. | Check token labels in training batch. Ensure all tokens before the response template are masked to `-100`. |
| **Catastrophic Forgetting** (Model outputs strict JSON but fails at basic conversation or math) | Learning rate too high ($> 5\times 10^{-4}$) or trained for too many epochs without mixed data. | Reduce LR to $1\text{–}2\times 10^{-4}$, lower rank $r$ to 8, or add $10\%$ general domain data into the fine-tuning mixture. |
| **CUDA / MPS Out-Of-Memory (OOM)** | Activations or batch size exceeded VRAM. | 1. Enable `gradient_checkpointing=True`.<br>2. Reduce micro-batch size to 1 or 2 and increase `gradient_accumulation_steps`.<br>3. Switch from LoRA to 4-bit QLoRA. |
| **Special Token Leakage** (Outputs `<\|im_end\|>`, `<\|endoftext\|>`, or raw markdown fences) | Tokenizer chat template didn't match the pre-trained base model format. | Always use `tokenizer.apply_chat_template()` instead of manually concatenating string templates. |

---

## 🎯 Architectural Decision Matrix: Prompt vs. RAG vs. Fine-Tune

| Requirement | Best Paradigm | Why? |
|---|:---:|---|
| **Fresh/dynamic facts** (e.g., "What is our company's refund policy today?") | **RAG / Tool Use** | Models cannot store fresh mutable knowledge in static weights. |
| **Strict formatting / Output style** (e.g., $99.9\%$ reliable JSON, custom DSL, compact routing) | **Fine-Tuning (LoRA)** | Base models frequently leak markdown or hallucinate enums; fine-tuning burns the grammar into model reflexes. |
| **Cost & Latency Reduction** (Replacing GPT-4o with an in-house $0.5\text{B}$ model for high-volume tasks) | **Fine-Tuning (SLM)** | A fine-tuned $0.5\text{B}$ model is $\sim 30\times$ faster and runs locally on edge devices. |
| **Rapid experimentation with unknown requirements** | **Prompt Engineering** | Zero training latency, instant iterations. Move to fine-tuning only when prompting plateaus or prompt tokens become too expensive. |


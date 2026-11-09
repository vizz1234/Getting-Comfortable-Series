# Getting Comfortable Series — Learning Path

## Mission
Master modern AI Engineering concepts step-by-step through interactive hands-on notebooks, code walkthroughs, and conceptual checks.

## Placement & Active Series
- Track 01: **LLM Orchestration & Schema Validation** (`llm-orchestration-schema-validation`) — 4 Episodes
- Track 02: **LLM Fine-Tuning, PEFT & Alignment** (`llm-fine-tuning`) — 16 Modular Episodes (6 Phases)

## Series & Episode Path

### Track 01: LLM Orchestration & Schema Validation
| Episode | Title | Notebook | Refresher | Status | Est. Hours |
|---|---|---|---|---|---|
| 01/01 | Intro to Orchestration | [01_introduction_to_orchestration.ipynb](./llm-orchestration-schema-validation/01_introduction_to_orchestration.ipynb) | [Refresher](./llm-orchestration-schema-validation/comfort-refresh.md#01-direct-sdks-vs-orchestration) | Do | 1.5 |
| 01/02 | LCEL & State Management | [02_lcel_and_state_management.ipynb](./llm-orchestration-schema-validation/02_lcel_and_state_management.ipynb) | [Refresher](./llm-orchestration-schema-validation/comfort-refresh.md#02-lcel--state-management) | Do | 2.0 |
| 01/03 | Schema Validation & Tool Use | [03_schema_validation_and_tool_use.ipynb](./llm-orchestration-schema-validation/03_schema_validation_and_tool_use.ipynb) | [Refresher](./llm-orchestration-schema-validation/comfort-refresh.md#03-schema-validation--tool-use) | Do | 2.0 |
| 01/04 | Orchestration Paradigms | [04_orchestration_paradigms.ipynb](./llm-orchestration-schema-validation/04_orchestration_paradigms.ipynb) | [Refresher](./llm-orchestration-schema-validation/comfort-refresh.md#04-orchestration-paradigms-bake-off) | Do | 3.0 |

### Track 02: LLM Fine-Tuning, PEFT & Alignment
| Episode | Phase & Title | Notebook | Refresher | Status | Est. Hours |
|---|---|---|---|---|---|
| 02/01 | **Understand:** Vectors, Matrices & Rank | [01_vectors_matrices_and_rank.ipynb](./llm-fine-tuning/01_vectors_matrices_and_rank.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#2-the-rank-intuition-visual-3-times-3-matrix) | Ready | 1.0 |
| 02/02 | **Understand:** FFT vs PEFT & Memory Math | [02_fft_vs_peft_and_memory_math.ipynb](./llm-fine-tuning/02_fft_vs_peft_and_memory_math.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#3-gpu-memory-rule-of-thumb) | Ready | 1.5 |
| 02/03 | **Understand:** SFT Mechanics & Loss Math | [03_sft_mechanics_and_loss_math.ipynb](./llm-fine-tuning/03_sft_mechanics_and_loss_math.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#recipe-3-completion-only-loss-masking-the-1-bug-fix) | Ready | 1.5 |
| 02/04 | **Understand:** The Alignment & RL Landscape (DPO, GRPO, PPO) | [04_alignment_and_rl_landscape.ipynb](./llm-fine-tuning/04_alignment_and_rl_landscape.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md) | Next | 2.0 |
| 02/05 | **Understand:** Architecture Decision Matrix & Simulator | [05_the_architectural_decision_matrix.ipynb](./llm-fine-tuning/05_the_architectural_decision_matrix.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#architectural-decision-matrix-prompt-vs-rag-vs-fine-tune) | Planned | 1.5 |
| 02/06 | **Build:** LoRALinear From Scratch in Pure PyTorch | [06_lora_from_scratch_pure_pytorch.ipynb](./llm-fine-tuning/06_lora_from_scratch_pure_pytorch.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#recipe-1-pure-pytorch-loralinear-layer) | Planned | 2.0 |
| 02/07 | **Break:** The Prompt Parrot Bug (Loss Masking) | [07_break_the_prompt_parrot.ipynb](./llm-fine-tuning/07_break_the_prompt_parrot.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#diagnostic-cheat-sheet-common-failure-modes) | Planned | 1.5 |
| 02/08 | **Break:** Catastrophic Forgetting & Rank Sensitivity | [08_break_catastrophic_forgetting.ipynb](./llm-fine-tuning/08_break_catastrophic_forgetting.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#diagnostic-cheat-sheet-common-failure-modes) | Planned | 1.5 |
| 02/09 | **Break:** Chat Templates & Special Token Leaks | [09_break_chat_templates_and_special_tokens.ipynb](./llm-fine-tuning/09_break_chat_templates_and_special_tokens.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#diagnostic-cheat-sheet-common-failure-modes) | Planned | 1.5 |
| 02/10 | **Tools:** Hugging Face PEFT Deep-Dive | [10_tools_huggingface_peft.ipynb](./llm-fine-tuning/10_tools_huggingface_peft.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#recipe-2-hugging-face-peft-production-setup) | Planned | 1.5 |
| 02/11 | **Tools:** Modern SFT with trl & SFTTrainer | [11_tools_trl_and_sft_trainer.ipynb](./llm-fine-tuning/11_tools_trl_and_sft_trainer.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#recipe-3-completion-only-loss-masking-the-1-bug-fix) | Planned | 1.5 |
| 02/12 | **Tools:** 4-Bit NormalFloat Quantization & QLoRA | [12_tools_qlora_and_bitsandbytes.ipynb](./llm-fine-tuning/12_tools_qlora_and_bitsandbytes.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md#3-gpu-memory-rule-of-thumb) | Planned | 1.5 |
| 02/13 | **Apply:** Fine-Tuning an SLM for Incident Triage | [13_apply_production_sft_slm.ipynb](./llm-fine-tuning/13_apply_production_sft_slm.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md) | Planned | 2.5 |
| 02/14 | **Apply:** Preference Alignment with DPO | [14_apply_preference_alignment_dpo.ipynb](./llm-fine-tuning/14_apply_preference_alignment_dpo.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md) | Planned | 2.0 |
| 02/15 | **Apply:** Reinforcement Learning with GRPO | [15_apply_reinforcement_learning_grpo.ipynb](./llm-fine-tuning/15_apply_reinforcement_learning_grpo.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md) | Planned | 2.0 |
| 02/16 | **Apply:** Adapter Fusion, GGUF Export & Ollama | [16_apply_adapter_fusion_gguf_and_ollama.ipynb](./llm-fine-tuning/16_apply_adapter_fusion_gguf_and_ollama.ipynb) | [Refresher](./llm-fine-tuning/comfort-refresh.md) | Planned | 2.0 |

## Progress Log

| Date | Episode | Quiz Score | Key Takeaway / Note |
|---|---|---|---|

## Review Queue
*(Missed topics or episodes with scores under 70% will be added here for targeted revision)*

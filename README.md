# Getting Comfortable Series

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![LangChain](https://img.shields.io/badge/LangChain-v0.3+-green.svg)](https://python.langchain.com/)
[![Pydantic v2](https://img.shields.io/badge/Pydantic-v2-e92063.svg)](https://docs.pydantic.dev/)
[![OpenRouter](https://img.shields.io/badge/Provider-OpenRouter-purple.svg)](https://openrouter.ai/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **AI moves fast. Learning it shouldn't feel chaotic.**  
> *Don't simplify the topic. Simplify the path to understanding it.*

The **Getting Comfortable Series** is an open-source, hands-on curriculum built for engineers who want genuine, battle-tested intuition for AI engineering topics.

Instead of superficial "hello world" demos or memorizing framework APIs, this series gives you a structured path from first principles to production tools.

$$\textbf{Learn} \longrightarrow \textbf{Become comfortable} \longrightarrow \textbf{Move on} \longrightarrow \textbf{Return later when needed}$$

---

## 🧭 The Core Learning Progression

Every topic in this series follows a principled 6-stage engineering progression:

$$\text{Understand} \longrightarrow \text{Build} \longrightarrow \text{Break} \longrightarrow \text{Introduce Tools} \longrightarrow \text{Apply} \longrightarrow \text{Revisit}$$

* **1. Understand:** What is the concept? What architectural problem does it solve?
* **2. Build:** Implement a simple version from first principles where practical.
* **3. Break:** Discover limitations, edge cases, and where the naive approach crashes.
* **4. Introduce Tools:** Now introduce the real-world frameworks (LangChain, Pydantic, LangGraph) that solve these exact problems. You understand *why* the tool exists before learning how to use it.
* **5. Apply:** Build realistic, production-pattern implementations.
* **6. Revisit:** Open the topic's [`comfort-refresh.md`](./llm-orchestration-schema-validation/comfort-refresh.md) months later to quickly refresh your memory in 3 minutes without re-running code.

---

## 🎯 What "Comfort" Actually Means

A learner finishes a topic able to:
1. **Explain** the core idea clearly in their own words.
2. **Understand** the major architectural components and data flows.
3. **Build** a working implementation from scratch.
4. **Recognize** common failure modes before they happen in production.
5. **Understand** why popular tools and frameworks exist rather than memorizing their APIs.
6. **Read** unfamiliar implementations without feeling lost.
7. **Come back** months later and quickly refresh the topic with zero friction.

---

## 🚀 Active Track: LLM Orchestration & Schema Validation

Explore production-grade LLM orchestration using **LangChain**, schema enforcement with **Pydantic v2**, and model flexibility powered by **OpenRouter** (test across Gemini 2.5 Flash, OpenAI, Claude 3.5, and open-weights models).

| Episode | Focus & Progression | Notebook | Est. Time | Quick Refresher |
|---|---|---|:---:|:---:|
| **01** | **Direct SDKs vs. Orchestration Architecture**<br>Direct provider SDKs ➔ payload divergence & vendor lock-in ➔ unified `BaseMessage` object architecture (`SystemMessage`, `HumanMessage`, `AIMessage`) & OpenRouter model switching. | [01_introduction_to_orchestration.ipynb](./llm-orchestration-schema-validation/01_introduction_to_orchestration.ipynb) | ~1.5h | [`comfort-refresh.md#01`](./llm-orchestration-schema-validation/comfort-refresh.md#01-direct-sdks-vs-orchestration) |
| **02** | **LCEL & Session State Management**<br>Manual function piping ➔ state spaghetti & concurrent session leaks ➔ LangChain Expression Language (LCEL `\|`), `RunnableLambda`, and session history via `RunnableWithMessageHistory`. | [02_lcel_and_state_management.ipynb](./llm-orchestration-schema-validation/02_lcel_and_state_management.ipynb) | ~2.0h | [`comfort-refresh.md#02`](./llm-orchestration-schema-validation/comfort-refresh.md#02-lcel--state-management) |
| **03** | **Schema Validation & Tool Execution**<br>Unstructured LLM JSON prompts ➔ markdown fence crashes & missing keys ➔ strict contracts via Pydantic (`.with_structured_output`), SQLite database querying tools, SMTP simulation, and tool-calling loops. | [03_schema_validation_and_tool_use.ipynb](./llm-orchestration-schema-validation/03_schema_validation_and_tool_use.ipynb) | ~2.0h | [`comfort-refresh.md#03`](./llm-orchestration-schema-validation/comfort-refresh.md#03-schema-validation--tool-use) |
| **04** | **The 5-Way Orchestration Bake-Off**<br>Side-by-side comparison of 5 paradigms solving a shared multi-step task (currency exchange + tip calculation): Raw loops, LangChain LCEL, LangGraph state machines, CrewAI role-playing agents, and DSPy declarative modules. | [04_orchestration_paradigms.ipynb](./llm-orchestration-schema-validation/04_orchestration_paradigms.ipynb) | ~3.0h | [`comfort-refresh.md#04`](./llm-orchestration-schema-validation/comfort-refresh.md#04-orchestration-paradigms-bake-off) |

---

## ⚡ Zero-Friction Returnability: `comfort-refresh.md`

We believe in **low cognitive friction, not low content volume**. Notebooks go as deep as needed to build genuine intuition.

When you return months later, you shouldn't have to re-execute 40 cells to remember how a pattern works. Each track includes a standalone:

👉 **[`comfort-refresh.md`](./llm-orchestration-schema-validation/comfort-refresh.md)**
* 30-second mental models and architecture diagrams
* Copy-paste ready canonical code recipes
* Common failure modes and 60-second diagnostic fixes
* Architecture decision matrices ("When should I use X vs Y?")

---

## 🛠️ Quickstart Guide

### 1. Clone Repository
```bash
git clone https://github.com/vizz1234/Getting-Comfortable-Series.git
cd Getting-Comfortable-Series
```

### 2. Create Virtual Environment & Install Dependencies
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Configure API Keys
Copy the example environment file and add your OpenRouter API key:
```bash
cp .env.example .env
```
Edit `.env`:
```ini
OPENROUTER_API_KEY=your-openrouter-api-key-here
MODEL_NAME=google/gemini-2.5-flash  # optional, default
```

### 4. Launch Notebooks
```bash
jupyter lab
```
Navigate to [`llm-orchestration-schema-validation/`](./llm-orchestration-schema-validation/) and open `01_introduction_to_orchestration.ipynb`!

---

## 🤖 Optional AI Pair-Programmer Skills

The notebooks are 100% self-contained. However, if you are working inside an AI-enabled IDE (Google Antigravity, Cursor, Claude Code), this repository includes companion skills in `.agents/skills/`:
- **`comfort-refresh`**: Rapid 90-second mental model, canonical code recipe, and failure-mode recap on any topic when returning weeks later.
- **`get-comfortable`**: An interactive step-by-step tutor that walks through notebooks with code prediction challenges.
- **`check-comfort`**: Quick retention and diagnostic drill across covered topics to calculate your Comfort Index.
- **`start-series`**: Initializes your personal track tracker in [`comfort-tracker.md`](./comfort-tracker.md).

These tools are silent sidekicks designed to support your learning, never to get in your way.

---

## 🗺️ Upcoming Tracks

- [ ] **Vector Embeddings, RAG & Hybrid Retrieval** (Dense vs. Sparse, Cross-encoder re-ranking, Semantic chunking)
- [ ] **Agentic Memory & State Compaction** (Episodic buffers, Summary trees, Checkpointing)
- [ ] **Evals & Guardrails** (LLM-as-a-judge, Synthetics, Latency/Cost profiling, Output filters)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

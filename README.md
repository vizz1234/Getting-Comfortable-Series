# Getting Comfortable Series

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![LangChain](https://img.shields.io/badge/LangChain-v0.3+-green.svg)](https://python.langchain.com/)
[![Pydantic v2](https://img.shields.io/badge/Pydantic-v2-e92063.svg)](https://docs.pydantic.dev/)
[![OpenRouter](https://img.shields.io/badge/Provider-OpenRouter-purple.svg)](https://openrouter.ai/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Bridge the gap between tutorial familiarity and true engineering comfort.**

The **Getting Comfortable Series** is an open-source, hands-on curriculum designed to build deep, battle-tested intuition for modern AI Engineering concepts. Instead of superficial copy-paste tutorials, each track delivers rigorous code walkthroughs, real-world patterns, edge-case failure modes, and automated self-assessments.

---

## 🚀 Active Track: LLM Orchestration & Schema Validation

Explore production-grade LLM orchestration using **LangChain**, schema enforcement with **Pydantic v2**, and model flexibility powered by **OpenRouter** (test across Gemini 2.0 Flash, OpenAI, Claude, Llama 3, and more).

| Episode | Focus & Topics | Notebook | Est. Time |
|---|---|---|:---:|
| **01** | **Direct SDKs vs Orchestration Architecture**<br>Provider SDK comparison (`google-genai` & `openai` vs LangChain), `BaseMessage` object architecture (`SystemMessage`, `HumanMessage`, `AIMessage`), token tracking, and manual conversation history management. | [01_introduction_to_orchestration.ipynb](./llm-orchestration-schema-validation/01_introduction_to_orchestration.ipynb) | ~1.5h |
| **02** | **LCEL & Session State Management**<br>LangChain Expression Language (LCEL) pipe composition (`|`), declarative transformations with `RunnableLambda`, `RunnablePassthrough`, output parsing, and persistent multi-turn sessions via `RunnableWithMessageHistory`. | [02_lcel_and_state_management.ipynb](./llm-orchestration-schema-validation/02_lcel_and_state_management.ipynb) | ~2.0h |
| **03** | **Schema Validation & Tool Execution**<br>Guaranteed structured output via Pydantic (`.with_structured_output`), schema validation guards, real SQLite database querying tools, SMTP simulation, tool-calling loops, and parallel execution with `RunnableParallel`. | [03_schema_validation_and_tool_use.ipynb](./llm-orchestration-schema-validation/03_schema_validation_and_tool_use.ipynb) | ~2.0h |
| **04** | **The 5-Way Orchestration Bake-Off**<br>Side-by-side comparison of 5 paradigms solving a shared multi-step task (currency exchange + tip calculation): Raw loops, LangChain LCEL, LangGraph state machines, CrewAI role-playing agents, and DSPy declarative modules. | [04_orchestration_paradigms.ipynb](./llm-orchestration-schema-validation/04_orchestration_paradigms.ipynb) | ~3.0h |

---

## 💡 What Makes This Repository Different?

### 1. Provider-Agnostic with OpenRouter
Switch between Google Gemini, OpenAI GPT-4o, Anthropic Claude 3.5, or open-weights models simply by updating one environment variable. No refactoring required.

### 2. Built-in Agentic AI Tutor Skills (`.agents/skills/`)
This repository comes configured with agentic AI tutoring skills ready to use in modern AI coding environments (e.g. Google Antigravity, Cursor, Claude Code):
- **`get-comfortable`**: Step-by-step interactive tutor that guides you through the notebooks, tests your intuition with code prediction questions, and quizzes you at each milestone.
- **`check-comfort`**: Runs an on-demand retention assessment across covered concepts and calculates your *Comfort Index*.
- **`start-series`**: Initializes and tailors your personal learning track inside [`comfort-tracker.md`](./comfort-tracker.md).

### 3. Concrete Self-Assessment Quizzes
Every episode includes machine-readable and human-friendly quiz banks under [`llm-orchestration-schema-validation/quizzes/`](./llm-orchestration-schema-validation/quizzes/) with questions, answer keys, and deep conceptual explanations.

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
# Or: jupyter notebook
```
Navigate to `llm-orchestration-schema-validation/` and open `01_introduction_to_orchestration.ipynb` to get started!

---

## 📈 Learning Path & Progress Tracker

Use [`comfort-tracker.md`](./comfort-tracker.md) to record your progress, log quiz scores, and track topics added to your review queue.

---

## 🗺️ Upcoming Tracks

- [ ] **Vector Embeddings, RAG & Hybrid Retrieval** (Dense vs Sparse, Re-ranking, Chunking trade-offs)
- [ ] **Agentic Memory & State Compaction** (Episodic buffers, Semantic summarization, Checkpointing)
- [ ] **Evals & Guardrails** (LLM-as-a-judge, Latency & Cost benchmarking, Output validation pipelines)

---

## 🤝 Contributing & Feedback

Contributions, suggestions, and additional exercises are welcome! Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details (or open an issue).

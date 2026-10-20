# Track: LLM Orchestration & Schema Validation

> **"Don't simplify the topic. Simplify the path to understanding it."**

This track takes you from the raw mechanics of API payloads to production-ready LLM orchestration and guaranteed schema enforcement—not by memorizing framework syntax, but by understanding the exact engineering problems each tool was built to solve.

---

## 🧭 The Learning Progression

Every topic in this track follows a rigorous 6-stage progression designed for genuine engineering comfort:

$$\text{Understand} \longrightarrow \text{Build} \longrightarrow \text{Break} \longrightarrow \text{Introduce Tools} \longrightarrow \text{Apply} \longrightarrow \text{Revisit}$$

1. **Understand:** What is the concept, and what architectural problem does it solve?
2. **Build:** Implement a simple version from first principles where practical.
3. **Break:** Test edge cases, observe state drift, JSON parse errors, and where naive implementations fail.
4. **Introduce Tools:** Now introduce LangChain, Pydantic, and LangGraph—understanding *why* they abstract what they do.
5. **Apply:** Build real-world workflows (e.g. SQLite database querying, session memory, multi-agent comparison).
6. **Revisit:** Jump into [`comfort-refresh.md`](./comfort-refresh.md) months later for a zero-friction 3-minute refresher.

---

## ⚡ Zero-Friction Refresher: `comfort-refresh.md`

If you are returning to this track after weeks or months, you don't need to re-run 50 notebook cells.  
Open the dedicated standalone reference:

👉 **[comfort-refresh.md](./comfort-refresh.md)**
* 30-second mental models & architectural diagrams
* Copy-paste production code patterns
* The "Break" diagnostic cheat sheet & common error fixes
* The 5-Way Orchestration Decision Matrix

---

## 📚 Curriculum & Notebooks

| Episode | Title & Focus | Hands-on Progression | Notebook | Est. Time |
|---|---|---|:---:|:---:|
| **01** | **Direct SDKs vs. Orchestration Architecture** | Call native provider SDKs (`openai`, `google-genai`) ➔ encounter vendor lock-in & message payload divergence ➔ introduce unified `BaseMessage` layer over **OpenRouter**. | [01_introduction_to_orchestration.ipynb](./01_introduction_to_orchestration.ipynb) | ~1.5h |
| **02** | **LCEL & Session State Management** | Pipe data manually through functions ➔ encounter state leaks and nested spaghetti ➔ build composable pipelines using LCEL (`\|`), `RunnableLambda`, and session-backed `RunnableWithMessageHistory`. | [02_lcel_and_state_management.ipynb](./02_lcel_and_state_management.ipynb) | ~2.0h |
| **03** | **Schema Validation & Tool Execution** | Prompt LLMs for raw JSON ➔ watch naive string parsing crash on markdown fences & missing keys ➔ enforce contracts with Pydantic v2 (`.with_structured_output`), bind SQLite & SMTP tools, and run tool execution loops. | [03_schema_validation_and_tool_use.ipynb](./03_schema_validation_and_tool_use.ipynb) | ~2.0h |
| **04** | **The 5-Way Orchestration Bake-Off** | Implement a shared multi-step task across **5 distinct paradigms**: Raw native loops, LangChain LCEL, LangGraph state machines, CrewAI role-playing agents, and DSPy compiled programs. | [04_orchestration_paradigms.ipynb](./04_orchestration_paradigms.ipynb) | ~3.0h |

---

## 🎯 What "Comfort" Looks Like in this Track

When you finish this track, you will be able to:
* **Explain** the difference between a raw SDK call and an orchestration abstraction to a peer.
* **Build** a multi-turn chat pipeline with session-scoped memory from scratch.
* **Diagnose** why an LLM output failed schema parsing and fix it deterministically.
* **Choose** with confidence between Raw Loops, LCEL, LangGraph, CrewAI, and DSPy for any project requirement.
* **Read** unfamiliar LangChain/Pydantic codebases without feeling lost.

---

## 🛠️ Quickstart

### 1. Install Dependencies
From the repository root:
```bash
pip install -r ../requirements.txt
```

### 2. Configure Environment
Copy `.env.example` to `.env` in the root (or in this folder) and provide your OpenRouter API key:
```ini
OPENROUTER_API_KEY=your-openrouter-api-key-here
MODEL_NAME=google/gemini-2.5-flash  # optional default
```

### 3. Launch
```bash
jupyter lab
```
Start with [`01_introduction_to_orchestration.ipynb`](./01_introduction_to_orchestration.ipynb)!

---

## 🧪 Quizzes & Self-Assessment

Machine-readable self-assessment banks are available in [`quizzes/`](./quizzes/) to test retention:
* [`01_intro.json`](./quizzes/01_intro.json) — Direct SDKs vs. unified message models.
* [`02_lcel.json`](./quizzes/02_lcel.json) — LCEL composition & session state.
* [`03_schema.json`](./quizzes/03_schema.json) — Pydantic contracts & tool calling mechanics.
* [`04_paradigms.json`](./quizzes/04_paradigms.json) — Paradigm trade-offs and decision rules.

*(If using an AI IDE, use the companion skill `comfort-refresh` for rapid recaps, or `get-comfortable` for interactive drills).*

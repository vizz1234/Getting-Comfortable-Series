---
name: comfort-refresh
description: Fast 90-second conceptual and code refresher skill for Getting Comfortable Series. Delivers instant mental models, canonical production patterns, and failure modes when returning to a topic without re-reading entire notebooks.
---

# comfort-refresh Skill

Use this skill when the learner wants an **instant, high-impact refresher** on a previously covered topic or episode.

Unlike `get-comfortable` (which guides cell-by-cell) or `check-comfort` (which runs multi-question assessment drills), **`comfort-refresh` is optimized for rapid recall and zero friction**:
> *"Give me the mental model, the clean 10-line pattern, and the #1 gotcha so I can get back to building."*

---

## Host Invocation Syntax
- Slash Command: `/comfort-refresh`, `/comfort-refresh 02`, `/comfort-refresh tools`
- Natural Language:
  - "Give me a comfort-refresh on LCEL session state."
  - "Quick refresh on schema validation and Pydantic."
  - "I forgot the difference between LangGraph and LCEL, refresh me."
  - "I'm about to build a tool loop, comfort-refresh 03."

---

## Step 0 — Resolve Topic & Source

Read `comfort-tracker.md` to identify active tracks.

1. **Specified Target**:
   - Match topic keywords:
     - `01`, `sdk`, `direct`, `message`, `openrouter` ➔ Episode 01: Direct SDKs vs. Orchestration
     - `02`, `lcel`, `pipe`, `history`, `session`, `runnable` ➔ Episode 02: LCEL & State Management
     - `03`, `schema`, `pydantic`, `tools`, `validation`, `structured` ➔ Episode 03: Schema Validation & Tool Use
     - `04`, `paradigms`, `bakeoff`, `langgraph`, `crewai`, `dspy`, `raw` ➔ Episode 04: Orchestration Paradigms Bake-Off
2. **Unspecified / General Request**:
   - Check `comfort-tracker.md` for the most recent completed or active episode.
   - If ambiguous, present a quick 1-line picker of available topics.

Read the corresponding section from `llm-orchestration-schema-validation/comfort-refresh.md`.

---

## Step 1 — Deliver the 90-Second Refresher Card

Output a crisp, beautifully formatted response structured into exactly 4 parts:

### 1. 💡 The Core Mental Model (2-3 sentences)
State clearly what the concept is and what architectural engineering problem it solves. If applicable, include a compact ASCII diagram.

### 2. ⚡ The Canonical Production Recipe (10-15 lines)
Provide a battle-tested, clean code snippet ready to adapt. Avoid boilerplate or toy examples; use the real pattern from `comfort-refresh.md`.

### 3. 💥 The "Break" (What breaks without this)
Explain the specific failure mode that makes this pattern necessary (e.g. JSON markdown fences crashing `json.loads`, concurrent session leaks, or cyclic graph deadlocks).

### 4. 📌 The Decision Rule
A single bold takeaway rule (e.g., *"If you need cycles, retries, or human review, use LangGraph; if linear with streaming, use LCEL."*).

---

## Step 2 — Next-Action Offer

Conclude with a brief, helpful prompt offering two quick paths:

> *"Need me to adapt this pattern to what you're currently building, or want a 15-second diagnostic check to verify your intuition?"*

- If they want adaptation: Help them integrate the pattern into their active code or workspace file.
- If they want a check: Ask **one** realistic failure-mode question (e.g. *"What happens if `configurable={'session_id': ...}` is omitted in invoke?"*).

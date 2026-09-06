---
name: start-series
description: Initializes or customizes the learning path for Getting Comfortable Series in LEARNING.md.
---

# start-series Skill

Use this skill when the learner wants to initialize, customize, or reset their learning path for the **Getting Comfortable Series**.

## Step 0 — Read Existing State
Read `LEARNING.md` from the current directory if present.

## Step 1 — Interactive Series Overview
Present the current active series and its episodes:
- **Active Series**: `llm-orchestration-schema-validation` (LLM Orchestration & Schema Validation)
  - **Episode 01/01**: `01_introduction_to_orchestration.ipynb` — Direct SDK comparison (OpenAI vs Gemini) & stateful manual loops.
  - **Episode 01/02**: `02_lcel_and_state_management.ipynb` — LCEL, RunnablePassthrough & RunnableWithMessageHistory.
  - **Episode 01/03**: `03_schema_validation_and_tool_use.ipynb` — Pydantic output validation, SQLite tool binding & tool loops.
  - **Episode 01/04**: `04_orchestration_paradigms.ipynb` — Side-by-side: LCEL vs Raw Loops vs LangGraph vs CrewAI vs DSPy.

Ask the learner:
- *"Would you like to start linearly from Episode 01, or jump directly to an episode (e.g. Episode 03 or 04)?"*

## Step 2 — Initialize / Update `LEARNING.md`
Based on their answer, update the table in `LEARNING.md`:
- Set chosen episode(s) to `Do`.
- Set skipped episode(s) to `Skip` or `Done`.

## Step 3 — Launch Handoff
Tell the learner their plan is ready in `LEARNING.md` and invite them to invoke `get-comfortable` to begin the interactive session!

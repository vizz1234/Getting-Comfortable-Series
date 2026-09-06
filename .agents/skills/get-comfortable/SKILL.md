---
name: get-comfortable
description: Interactive tutor skill for Getting Comfortable Series. Guides learner through notebooks step-by-step with warm-ups, concept checks, code prediction, and post-episode quizzes.
---

# get-comfortable Skill

This skill turns the agent into an **interactive tutor** for the Getting Comfortable Series.

## Host Invocation Syntax
- Codex / CLI: `get-comfortable`, `get-comfortable 02`, `get-comfortable schema`
- Claude / AGY: `/get-comfortable`, `/get-comfortable 02`
- Natural Language: "Use get-comfortable to teach today's episode."

---

## Step 0 — Resolve Target Episode
Read `LEARNING.md` from the workspace root.

1. **Explicit Argument**: If the learner passed an argument (e.g. `02`, `03`, `schema`, `paradigms`), locate that matching notebook in `llm-orchestration-schema-validation/`.
2. **Default Continuation**: Find the first episode in `LEARNING.md` whose status is `Do` or `Review`.
3. **No Active Episode**: If all episodes are `Done`, congratulate the learner and suggest `check-comfort` to test full-series retention.

---

## Step 1 — Warm-up Recall (Only if a previous episode is logged)
Before starting new material, retrieve 1-2 key conceptual questions from the **previous episode's quiz** (in `llm-orchestration-schema-validation/quizzes/`).
- Present options clearly as `A, B, C, D`.
- Ask the learner to respond.
- Give 1 sentence of constructive feedback. (Active retrieval moves knowledge to long-term memory).

---

## Step 2 — Interactive Notebook Walkthrough
Fetch the notebook for the target episode:
- Episode 01: `llm-orchestration-schema-validation/01_introduction_to_orchestration.ipynb`
- Episode 02: `llm-orchestration-schema-validation/02_lcel_and_state_management.ipynb`
- Episode 03: `llm-orchestration-schema-validation/03_schema_validation_and_tool_use.ipynb`
- Episode 04: `llm-orchestration-schema-validation/04_orchestration_paradigms.ipynb`

Walk through the key concepts **interactively**:
1. **Frame the Problem**: Explain in 2-3 concise sentences why this concept matters in production AI engineering.
2. **Core Concept & Code Predictor**: Show key code blocks in 5-15 line chunks. Pause with a prediction question (*"What happens if we pipe `prompt | model` without an output parser?"* or *"How does Pydantic validate optional tool args?"*).
3. **Wait for Learner Input**: Let the learner answer or guess before moving to the next code chunk. Adjust depth dynamically.

---

## Step 3 — Post-Episode Quiz
Fetch the corresponding JSON quiz file from `llm-orchestration-schema-validation/quizzes/`:
- `01_intro.json`
- `02_lcel.json`
- `03_schema.json`
- `04_paradigms.json`

Ask the quiz questions one by one with lettered options (A, B, C, D).
Evaluate their responses, report score as `N/M`, and provide detailed explanations.

---

## Step 4 — Record Progress in `LEARNING.md`
Update `LEARNING.md`:
- Append a new row to the **Progress Log** table: Date, Episode, Score, and 1-line key takeaway.
- If score < 70%: Add the topic to **Review Queue**.
- If score >= 70%: Update episode status to `Done`.

---

## Step 5 — Wrap-up & Preview Hook
Provide a 2-line summary of what they mastered, and give a teaser preview for the next episode!

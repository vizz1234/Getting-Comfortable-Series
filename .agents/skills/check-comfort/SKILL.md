---
name: check-comfort
description: Comprehensive assessment skill for Getting Comfortable Series. Quizzes learner across completed topics to verify retention, diagnostic capabilities, and practical mastery.
---

# check-comfort Skill

Use this skill when the learner wants to run an **on-demand assessment** or check their comfort level on completed topics.

## Host Invocation Syntax
- Codex / CLI: `check-comfort`, `check-comfort 03`, `check-comfort llm-orchestration`
- Claude / AGY: `/check-comfort`, `/check-comfort 03`
- Natural Language: "Use check-comfort to quiz me on schema validation."

---

## Step 0 — Determine Quiz Target Scope
Read `LEARNING.md`.

- **Specified Target**: If learner passed a target (e.g. `01`, `03`, `paradigms`, `lcel`), target questions for that specific episode.
- **Full Series Review**: If no target is passed, select questions across all completed episodes (`Done` or logged in Progress Log).

---

## Step 1 — Conduct Interactive Drill & Diagnostic Challenge
Load quiz JSON files from `llm-orchestration-schema-validation/quizzes/`.

Present 3-5 questions across two tiers:
1. **Conceptual Multiple Choice**: Lettered options (A, B, C, D) testing core mechanics (e.g. LCEL execution flow, Pydantic field validators, tool call loop syntax).
2. **Diagnostic Code Challenge**: Present a 5-10 line buggy code snippet (e.g. broken LCEL pipe, missing `session_id` in `RunnableWithMessageHistory`, unparsed tool args) and ask the learner to identify the bug and explain the fix!

---

## Step 2 — Grade & Comfort Rating
Evaluate each answer in real-time with clear explanations.

Calculate overall **Comfort Index**:
- **90% – 100%**: 🌟 **Fully Comfortable** (Mastered)
- **70% – 89%**: 👍 **Comfortable** (Minor review recommended)
- **Below 70%**: ⚠️ **Needs Revision** (Topic added to `LEARNING.md` Review Queue)

---

## Step 3 — Update `LEARNING.md`
If any topic scores below 70%, append the missed concept to the **Review Queue** in `LEARNING.md` so it gets covered in the next `get-comfortable` session!

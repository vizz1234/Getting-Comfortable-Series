# LLM Orchestration & Schema Validation

This folder contains notebooks and materials to get comfortable with **LLM Orchestration** (using LangChain) and **Schema Validation / Structured Outputs** (using Pydantic), powered by **OpenRouter** (supporting Gemini, OpenAI, Claude, Llama, and more).

## Learning Objectives
1. Understand how to orchestrate LLM workflows using LangChain's Expression Language (LCEL) over OpenRouter.
2. Learn how to define data schemas with Pydantic models.
3. Combine both to guarantee that LLM outputs conform to a specific, validated structure.

## Structure
* [01_introduction_to_orchestration.ipynb](./01_introduction_to_orchestration.ipynb): Direct SDK & OpenRouter comparison, message objects, and manual state/history management.
* [02_lcel_and_state_management.ipynb](./02_lcel_and_state_management.ipynb): LangChain Expression Language (LCEL), custom parsing with `RunnableLambda`, and session-based history management with `RunnableWithMessageHistory`.
* [03_schema_validation_and_tool_use.ipynb](./03_schema_validation_and_tool_use.ipynb): Pydantic models for structured output, local SQLite database tool binding, SMTP email tools, tool loops, and parallel chain execution with `RunnableParallel`.
* [04_orchestration_paradigms.ipynb](./04_orchestration_paradigms.ipynb): Side-by-side comparison of 5 orchestration paradigms (LangChain LCEL, Raw loops, LangGraph, CrewAI, and DSPy) on a currency & tip shared task, including exercises.

## Quizzes & Assessments
Self-assessment and automated question banks are available in [`quizzes/`](./quizzes/):
* `01_intro.json` — Orchestration fundamentals & message architecture.
* `02_lcel.json` — LCEL composition & session history management.
* `03_schema.json` — Pydantic schema validation & tool binding.
* `04_paradigms.json` — Orchestration paradigms bake-off.

## Prerequisites & Setup
To run these notebooks, install dependencies from the repository root:
```bash
pip install -r ../requirements.txt
```
Or install directly:
```bash
pip install langchain langchain-openai langchain-community langgraph crewai dspy-ai pydantic python-dotenv jupyter openai google-genai pandas
```

You will also need to set up your OpenRouter API key in `.env` (copied from `.env.example`):
```bash
OPENROUTER_API_KEY=your-openrouter-api-key-here
MODEL_NAME=google/gemini-2.5-flash  # optional, default
```



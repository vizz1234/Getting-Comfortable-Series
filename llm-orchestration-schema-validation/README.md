# LLM Orchestration & Schema Validation

This folder contains notebooks and materials to get comfortable with **LLM Orchestration** (using LangChain) and **Schema Validation / Structured Outputs** (using Pydantic), powered by **OpenRouter** (supporting Gemini, OpenAI, Claude, Llama, and more).

## Learning Objectives
1. Understand how to orchestrate LLM workflows using LangChain's Expression Language (LCEL) over OpenRouter.
2. Learn how to define data schemas with Pydantic models.
3. Combine both to guarantee that LLM outputs conform to a specific, validated structure.

## Structure
* [01_introduction_to_orchestration.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/01_introduction_to_orchestration.ipynb): Direct SDK & OpenRouter comparison, message objects, and manual state/history management.
* [02_lcel_and_state_management.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/02_lcel_and_state_management.ipynb): LangChain Expression Language (LCEL), custom parsing with `RunnableLambda`, and session-based history management with `RunnableWithMessageHistory`.
* [03_schema_validation_and_tool_use.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/03_schema_validation_and_tool_use.ipynb): Pydantic models for structured output, local SQLite database tool binding, SMTP email tools, tool loops, and parallel chain execution with `RunnableParallel`.
* [04_orchestration_paradigms.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/04_orchestration_paradigms.ipynb): Side-by-side comparison of 5 orchestration paradigms (LangChain LCEL, Raw loops, LangGraph, CrewAI, and DSPy) on a currency & tip shared task, including exercises.

## Prerequisites
To run these notebooks, you will need to install the following dependencies:
```bash
pip install langchain langchain-openai langgraph crewai dspy-ai pydantic python-dotenv jupyter openai
```
You will also need to set up your OpenRouter API key as an environment variable (`OPENROUTER_API_KEY`) and optional `MODEL_NAME` (defaults to `google/gemini-2.0-flash-001`).


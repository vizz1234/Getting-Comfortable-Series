# LLM Orchestration & Schema Validation

This folder contains notebooks and materials to get comfortable with **LLM Orchestration** (using LangChain) and **Schema Validation / Structured Outputs** (using Pydantic), powered by **Gemini**.

## Learning Objectives
1. Understand how to orchestrate LLM workflows using LangChain's Expression Language (LCEL).
2. Learn how to define data schemas with Pydantic models.
3. Combine both to guarantee that LLM outputs conform to a specific, validated structure.

## Structure
* [01_intro_to_langchain.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/01_intro_to_langchain.ipynb): Direct SDK comparison (OpenAI vs. Gemini), message objects, and manual state/history management.
* [02_lcel_and_chat_history.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/02_lcel_and_chat_history.ipynb): LangChain Expression Language (LCEL), custom parsing with `RunnableLambda`, and session-based history management with `RunnableWithMessageHistory`.
* [03_pydantic_and_tool_calling.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/03_pydantic_and_tool_calling.ipynb): Pydantic models for structured output, local SQLite database tool binding, SMTP email tools, tool loops, and parallel chain execution with `RunnableParallel`.

## Prerequisites
To run these notebooks, you will need to install the following dependencies:
```bash
pip install langchain langchain-google-genai pydantic python-dotenv jupyter
```
You will also need to set up your Gemini API key as an environment variable (`GOOGLE_API_KEY`).

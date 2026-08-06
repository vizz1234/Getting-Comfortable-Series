# LLM Orchestration & Schema Validation

This folder contains notebooks and materials to get comfortable with **LLM Orchestration** (using LangChain) and **Schema Validation / Structured Outputs** (using Pydantic).

## Learning Objectives
1. Understand how to orchestrate LLM workflows using LangChain's Expression Language (LCEL).
2. Learn how to define data schemas with Pydantic models.
3. Combine both to guarantee that LLM outputs conform to a specific, validated structure.

## Structure
* [01_orchestration.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/01_orchestration.ipynb): Focuses on the basics of LangChain, prompt templates, models, and chaining.
* [02_validation.ipynb](file:///Users/vizzdd/Documents/Getting%20Comfortable%20Series/llm-orchestration-schema-validation/02_validation.ipynb): Focuses on Pydantic schema validation and parsing structured outputs from LLMs.

## Prerequisites
To run these notebooks, you will need to install the following dependencies:
```bash
pip install langchain langchain-openai pydantic jupyter
```
You will also need to set up your LLM provider API key (e.g., `OPENAI_API_KEY`).

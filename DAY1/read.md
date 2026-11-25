# DAY 1 — Groq + LangChain Chat Assistant

This directory contains a Google Colab/Jupyter notebook demonstrating how to use **LangChain** with the **Groq API** to build a simple bakery assistant.

## Notebook

- [`task.ipynb`](task.ipynb) — installs dependencies, configures Groq credentials, initializes a chat model, and sends example prompts.

## Topics Covered

- Installing `langchain-groq`
- Loading the `GROQ_API_KEY` from Colab Secrets
- Initializing a Groq-backed `ChatGroq` model
- Creating a system prompt with bakery policies
- Building a basic question-and-answer function
- Testing prompt safety with a Meta Llama prompt guard model

## Models Used

- `openai/gpt-oss-120b` — example chat model
- `meta-llama/llama-prompt-guard-2-22m` — prompt safety evaluation

## Setup

1. Open `task.ipynb` in Google Colab or Jupyter Notebook.
2. Add a Groq API key named `GROQ_API_KEY` to Colab's Secrets pane.
3. Run the notebook cells from top to bottom.

## Example Bakery Rules

The notebook defines an assistant for **Sweet Crumbs Home Bakery** with these rules:

- Cakes are baked to order.
- Customers require at least 24 hours' notice.
- All cakes have eggless versions.
- The assistant should avoid promising delivery times when uncertain.
- It should keep replies polite and under 60 words.

## Requirements

- Python 3
- Google Colab or Jupyter Notebook
- A valid Groq API key
- `langchain-groq`

Install the main dependency with:

```bash
pip install langchain-groq
```

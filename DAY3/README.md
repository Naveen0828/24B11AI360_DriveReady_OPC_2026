# Sweet Crumbs Home Bakery — LangChain Chat Assistant

A conversational AI assistant built with Python, LangChain, and the Groq OpenAI-compatible API. The assistant answers customer questions about products and orders for **Sweet Crumbs Home Bakery**.

## Notebook

- `day3.ipynb`

## Overview

The notebook demonstrates:

- Installing LangChain packages
- Connecting to a Groq-hosted OpenAI model
- Creating a system prompt with bakery facts and rules
- Maintaining conversation history
- Using `ChatPromptTemplate` for structured prompts
- Parsing model responses with `StrOutputParser`
- Automatically testing the assistant using a CSV file
- Generating concise responses in English or Telugu

## Bakery Knowledge

The assistant is configured with information about:

- Plum cake — ₹500
- Chocolate cake — ₹650
- Cupcakes — ₹80 each
- 24-hour advance notice for cake orders
- Eggless cake availability
- Delivery location limitations
- Delivery-time restrictions

## Requirements

- Python 3
- Google Colab or Jupyter Notebook
- A Groq API key

## Installation

Run the first notebook cell:

```python
!pip install -q -U langchain langchain-openai
```

Install any additional dependency if required:

```bash
pip install langchain langchain-openai langchain-core
```

## API Configuration

In Google Colab, store the Groq API key as a user secret:

```python
from google.colab import userdata
```

```python
llm = ChatOpenAI(
    model="openai/gpt-oss-120b",
    api_key=userdata.get("GROQ_API_KEY"),
    base_url="https://api.groq.com/openai/v1",
    temperature=0.3
)
```

Add a secret named `GROQ_API_KEY` in the Colab **Secrets** section.

## Usage

The notebook defines an `ask()` function that stores the conversation history:

```python
answer = ask("Hi, I'm Ravi. Do you make eggless cakes?")
print(answer)
```

Example questions:

- “Do you make eggless cakes?”
- “How much is a plum cake?”
- “Can I get a cake today?”
- “Do you deliver to Kakinada?”
- “What is the price of 6 cupcakes?”

## CSV Testing

The notebook includes a simple test runner that reads questions from:

```text
/content/test.csv
```

The CSV should contain:

| Column | Description |
|---|---|
| `question` | Customer question |
| `must_include` | Text expected in the generated response |

Run the tests with:

```python
run_tests()
```

The test runner prints a `PASS` or `FAIL` result and calculates the overall pass percentage.

Example CSV:

```csv
question,must_include
How much is a plum cake?,500
Do you make eggless cakes?,eggless
What is the price of 6 cupcakes?,480
```

## Behavior Rules

- Keep responses under 50 words.
- Use friendly, customer-focused language.
- Respond in English or Telugu.
- Do not promise delivery locations or delivery times unless confirmed by the owner.
- Calculate totals carefully.
- Refer unknown details to the bakery owner.

## Run the Notebook

1. Open `day3.ipynb` in Google Colab or Jupyter Notebook.
2. Install the required packages.
3. Configure `GROQ_API_KEY`.
4. Run all cells in order.
5. Ask bakery questions using the `ask()` function.
6. Optionally prepare `/content/test.csv` and run `run_tests()`.

## License

Add a repository license if you plan to distribute or modify this project publicly.

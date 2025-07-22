# 🤖 Gemini-Powered Multi-Turn Chatbot using Agno

This is a simple multi-turn conversational assistant built using [Agno](https://pypi.org/project/agno/) and Google's [Gemini API](https://ai.google.dev/). It supports contextual conversation with markdown output, examples, and concise responses.

## 🚀 Features

- ✅ Multi-turn conversation
- ✅ Powered by Gemini 1.5 Flash
- ✅ Markdown-enabled output
- ✅ Instructional personality
- ✅ Easy terminal interaction

## 🛠️ Installation

Install the required packages using pip:

```bash
pip install agno google-generativeai
```

## 🔑 API Key

Set your **Gemini API key** before running the chatbot. You can [get your API key here](https://makersuite.google.com/app/apikey).

```python
import os
os.environ["GEMINI_API_KEY"] = "your-api-key-here"
```

## 📜 Usage

Run the script to start chatting:

```python
from agno.agent import Agent
from agno.models.google import Gemini

model = Gemini(id="gemini-1.5-flash", api_key=os.environ.get("GEMINI_API_KEY"))

agent = Agent(
    model=model,
    description="A multi-turn assistant, enhanced by Agno's orchestration.",
    instructions=[
        "Be concise.",
        "Support explanations with examples.",
        "Use markdown formatting for clarity.",
        "Remember user context for coherent multi-turn conversations."
    ],
    markdown=True
)

print("Ask about recipes you want to create. Type 'exit' to quit.")
conversation_history = []
while True:
    user_query = input("You: ")
    if user_query.lower() in ['exit', 'quit']:
        print("Chat ended.")
        break
    response = agent.run(user_query)
    print(f"Assistant:\n{response.content}")
    conversation_history.append({"user": user_query, "assistant": response.content})
```

## 🧠 Example

```
You: What is a lambda function in Python?
Assistant:
A **lambda function** is a small anonymous function defined using the `lambda` keyword.

Example:
```python
square = lambda x: x * x
print(square(5))  # Output: 25
```
```

## 📂 Project Structure

```
.
├── chatbot.py          # Main Python script
├── README.md           # Project documentation
```

## 📝 License

This project is open source under the MIT License.

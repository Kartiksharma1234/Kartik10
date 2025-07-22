# 🤖 Gemini-Powered Recipe Creator Chatbot using Agno

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
You: mushroom, chicken, capsicum, garlic?
Assistant:
Here are a few recipe ideas using mushroom, chicken, capsicum, and garlic:

**1. One-Pan Garlic Herb Chicken and Vegetables:**

*   **Description:** A simple and flavorful dish where everything cooks together on one pan for easy cleanup.
*   **Ingredients:** Chicken breasts (cut into bite-sized pieces), mushrooms (sliced), capsicum (sliced), garlic (minced), olive oil, herbs (rosemary, thyme, or oregano), salt, and pepper.
*   **Instructions:** Toss chicken and vegetables with olive oil, herbs, salt, and pepper. Spread on a baking sheet and roast in a preheated oven at 400°F (200°C) for 20-25 minutes, or until chicken is cooked through.


**2. Chicken and Mushroom Stir-fry with Capsicum:**

*   **Description:** A quick and easy stir-fry perfect for a weeknight meal.
*   **Ingredients:** Chicken breast (cut into strips), mushrooms (sliced), capsicum (sliced), garlic (minced), soy sauce, oyster sauce, cornflour (optional, for thickening), vegetable oil.
*   **Instructions:** Stir-fry garlic in hot oil until fragrant. Add chicken and stir-fry until cooked. Add mushrooms and capsicum and stir-fry until tender-crisp.  Stir in soy sauce and oyster sauce.  If using, mix cornflour with a little water to make a slurry and add to thicken the sauce. Serve with rice.


**3. Creamy Mushroom and Chicken Pasta:**

*   **Description:** A rich and comforting pasta dish.  Capsicum can be added for extra flavour and colour.
*   **Ingredients:** Chicken breast (cooked and shredded or diced), mushrooms (sliced), capsicum (diced), garlic (minced), pasta (your choice), cream, Parmesan cheese, butter, onion (optional), vegetable broth or chicken broth, salt, pepper.
*   **Instructions:** Cook pasta according to package directions. While pasta cooks, sauté garlic and onion (if using) in butter until softened. Add mushrooms and capsicum and cook until tender. Stir in cream, broth, salt and pepper.  Add cooked chicken and Parmesan cheese. Toss with cooked pasta and serve.

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

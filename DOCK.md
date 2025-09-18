# **Ghaymah GenAI Documentation**

This guide provides everything you need to use Ghaymah GenAI: available models, usage monitoring, coding examples, API key management, and How to Use LLMs Effectively (Prompt Engineering).

---

## 1. **Available Models**
#### **Model Descriptions:**
- **QwQ-32B**
    - Type: Reasoning Model (Qwen series).
    - Strengths: Strong in mathematics, reasoning, and programming.
    - Use Cases: Coding assistants, AI tutors for STEM education.
- **DeepSeek-V3-0324**
    - Type: Mixture-of-Experts (MoE).
    - Strengths: Efficient, excellent at reasoning and coding.
    - Use Cases: Balanced chatbot for tech support or general-purpose tasks.
- **gemma-3-4b-it**
    - Type: Lightweight model.
    - Strengths: Fast, efficient, versatile.
    - Use Cases: Mobile chatbots, quick text summarization.
- **Qwen3-32B**
    - Type: Advanced Qwen model.
    - Strengths: Exceptional reasoning, coding, and multilingual support.
    - Use Cases: Global applications, multilingual support systems.
- **GLM-4.5-Air**
    - Type: Compact reasoning model.
    - Strengths: Strong in logic, mathematics, tool-calling, and agentic tasks.
    - Use Cases: AI agents, workflow automation, data analysis tools.
- **Kimi-K2-Instruct**
    - Type: Large model by Moonshot AI.
    - Strengths: Long-context understanding, strong multilingual ability.
    - Use Cases: Document review, meeting summarization, long conversations.

#### **Model Comparison Table**

| **Model**            | **Strengths**                   | **Best For**                              | **Examples**                       | **Max tokens**                    |
| -------------------- | ------------------------------- | ----------------------------------------- | ---------------------------------- | ----------------------------------|
| **QwQ-32B**          | Math, reasoning, programming    | Technical problem-solving, coding tasks   | Coding assistant, AI tutor         | 131,072                           |
| **DeepSeek-V3-0324** | Efficient MoE, reasoning + code | Balanced performance, general-purpose use | Tech support chatbot               | 163,840                           |
| **gemma-3-4b-it**    | Fast, lightweight               | Resource-constrained apps                 | Mobile chatbot, summarizer         | 128,000                           |
| **Qwen3-32B**        | Strong reasoning, multilingual  | Complex coding, multilingual apps         | Multilingual support, dev platform | 32,768                            |
| **GLM-4.5-Air**      | Tool-calling, logical workflows | AI agents, automation                     | Flight booking, data reports       | 128,000                           |
| **Kimi-K2-Instruct** | Long-context, multilingual      | Chatbots, long text summarization         | Legal review, meeting recaps       | 128,000                           |

---

## 2. **Usage Dashboard**
#### **Your Usage**
   - Displays your API usage percentage compared to plan limits (requests or tokens).
#### **Rate Limits**
   - Requests per Minute (RPM): Maximum requests allowed per minute.
   - If exceeded → requests will be denied temporarily.
#### **API Keys Usage**
   - For each key, you’ll see:
      - Created → Date/time key was generated.
      - RPM → Request limit for that key.
   - Helps manage multiple projects with different keys.

---

## 3. **Code Examples**
#### **Python Example**
```bash
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY", 
    base_url="https://genai.ghaymah.systems"
)

response = client.chat.completions.create(
    model="DeepSeek-V3-0324",
    messages=[{"role": "user", "content": "Explain AI in simple terms"}],
    max_tokens=100
)

print(response.choices[0].message.content)
```
#### **JavaScript Example**
```bash
import OpenAI from "openai";

const client = new OpenAI({
    apiKey: "YOUR_API_KEY",
    baseURL: "https://genai.ghaymah.systems"
});

async function main() {
    try {
        const response = await client.chat.completions.create({
            model: "DeepSeek-V3-0324",
            messages: [{ "role": "user", "content": "Explain AI in simple terms" }],
            max_tokens: 100
        });
        console.log(response.choices[0].message.content);
    } catch (error) {
        console.error("Error making API call:", error);
    }
}

main();
```

---

## 4. **API Key Management**
#### **Connection Info**
```bash
Base URL: https://genai.ghaymah.systems
API Key: Used to authenticate all requests.
```
#### **API Key Security**
   - Keep it secret → never expose in public code.
   - Use environment variables `.env` instead of hardcoding.
   - Always connect via the official base URL for security.

---

## 5. **How to Use LLMs Effectively (Prompt Engineering)**
#### **Large Language Models (LLMs) are powerful, but the quality of your prompt directly affects the quality of the output. Writing good prompts is both an art and a science.**

- **Do’s (Good Practices):**
    - Be Clear and Specific
        - Clearly state the task.
        - Example: “Write a Python function that sorts a list using bubble sort” instead of “Sort this”.
    - Provide Context
        - Add background if needed.
        - Example: “Explain machine learning to a 12-year-old” vs “Explain machine learning”.
    - Set Constraints
        - Limit output style, format, or length.
        - Example: “Summarize this article in 3 bullet points”.
    - Use Step-by-Step Instructions
        - Encourage structured reasoning with “think step by step”.
    - Test and Iterate
        - Adjust wording and compare outputs.
    
- **Good Prompt:**
```bash
Explain Python programming language in simple terms for a beginner.
Include:
- What it is used for
- Key features
- One short example of code
Limit the explanation to under 150 words.
```

- **Don’ts (Bad Practices):**
    - Don’t be too vague: “Write something about AI”.
    - Don’t mix multiple unrelated tasks.
    - Don’t assume context—always specify.
    - Don’t forget output formatting requirements.

- **Bad Prompt:**
```bash
Explain Python.
```

- **Python Example with Prompt Engineering**
```bash
from openai import OpenAI

# Initialize client
client = OpenAI(
    api_key="YOUR_API_KEY", 
    base_url="https://genai.ghaymah.systems"
)

# Example of a well-structured prompt
prompt = """
You are a professional Python tutor.
Task: Write a Python function that checks if a string is a palindrome.
Requirements:
- The function should be named is_palindrome
- It should return True or False
- Add a short docstring explaining the function
Provide only the code, no extra explanation.
"""

response = client.chat.completions.create(
    model="QwQ-32B",
    messages=[{"role": "user", "content": prompt}],
    max_tokens=150
)

print(response.choices[0].message.content)
```
- **JavaScript Example with Prompt Engineering**
```bash
import OpenAI from "openai";

const client = new OpenAI({
    apiKey: "YOUR_API_KEY",
    baseURL: "https://genai.ghaymah.systems"
});

// Example of a well-structured prompt
const prompt = `
You are a professional Python tutor.
Task: Write a Python function that checks if a string is a palindrome.
Requirements:
- The function should be named is_palindrome
- It should return True or False
- Add a short docstring explaining the function
Provide only the code, no extra explanation.
`;

async function main() {
    try {
        const response = await client.chat.completions.create({
            model: "QwQ-32B",
            messages: [{ role: "user", content: prompt }],
            max_tokens: 150
        });

        console.log(response.choices[0].message.content);
    } catch (error) {
        console.error("Error making API call:", error);
    }
}

main();
```

---

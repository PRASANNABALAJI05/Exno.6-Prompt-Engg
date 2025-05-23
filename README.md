# Exno.6-Prompt-Engg
# Date: 8/5/2025
# Register no. 212223060203
# Aim: Development of Python Code Compatible with Multiple AI Tools

# Algorithm: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights.

1. **Define Objective**  
   - Create a Python script that interacts with multiple AI tools/APIs (e.g., OpenAI, HuggingFace, Cohere, etc.).
   - Fetch and compare results from each tool.
   - Generate actionable insights based on comparison.

2. **Set Up API Access**
   - Install required libraries using `pip` (e.g., `openai`, `requests`, `transformers`).
   - Store API keys securely using environment variables or config files.

3. **Create Prompt Input Function**
   - Accept user input or pre-define prompt(s).
   - Ensure format compatibility across APIs.

4. **Fetch Responses**
   - Call each API using the same prompt.
   - Collect and store responses in a unified structure.

5. **Compare Outputs**
   - Analyze responses based on relevance, tone, completeness, etc.
   - Use basic NLP techniques or heuristics for scoring.

6. **Generate Insight**
   - Summarize which tool gave the most suitable result.
   - Optionally generate a recommendation or final output.

7. **Display/Export Result**
   - Print the outputs side by side.
   - Export comparison as JSON/CSV if needed.

---

## Sample Code Snippet

```python
import openai
import requests
import os

# Load API keys
openai.api_key = os.getenv("OPENAI_API_KEY")
huggingface_token = os.getenv("HUGGINGFACE_TOKEN")

prompt = "Explain quantum computing in simple terms."

# OpenAI Response
def get_openai_response(prompt):
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    return response.choices[0].message.content.strip()

# HuggingFace Response (using text generation)
def get_huggingface_response(prompt):
    headers = {"Authorization": f"Bearer {huggingface_token}"}
    payload = {
        "inputs": prompt,
        "parameters": {"max_new_tokens": 100}
    }
    response = requests.post(
        "https://api-inference.huggingface.co/models/gpt2",
        headers=headers,
        json=payload
    )
    return response.json()[0]['generated_text'].strip()

# Compare and print results
openai_output = get_openai_response(prompt)
hf_output = get_huggingface_response(prompt)

print("=== OpenAI GPT Output ===\n", openai_output)
print("\n=== HuggingFace GPT2 Output ===\n", hf_output)
```



# Result: The corresponding Prompt is executed successfully

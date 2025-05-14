# Exno.6-Prompt-Engg
# Date: 14/05/2025
# Register no. 212223060203
# Aim: Development of Python Code Compatible with Multiple AI Tools



# Algorithm: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights.

* ✅ Send a **single prompt** to multiple AI services (OpenAI, Cohere, Hugging Face)
* ✅ Collect and **compare their responses**
* ✅ Generate **actionable insights** based on length, keyword frequency, and readability (using `textstat`)

---

## 🔧 Requirements

First, install the required packages:

```bash
pip install openai cohere requests textstat
```

---

## ✅ Full Python Code

```python
import openai
import cohere
import requests
import textstat

# API Keys (Replace with your own)
OPENAI_API_KEY = 'your-openai-api-key'
COHERE_API_KEY = 'your-cohere-api-key'
HUGGINGFACE_TOKEN = 'your-huggingface-token'

# Prompt to evaluate
prompt = "Explain quantum computing in simple terms for high school students."

# === AI Tool Integrations === #

def get_openai_response(prompt):
    openai.api_key = OPENAI_API_KEY
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": prompt}]
    )
    return response['choices'][0]['message']['content']

def get_cohere_response(prompt):
    co = cohere.Client(COHERE_API_KEY)
    response = co.generate(prompt=prompt, max_tokens=300)
    return response.generations[0].text.strip()

def get_huggingface_response(prompt):
    headers = {"Authorization": f"Bearer {HUGGINGFACE_TOKEN}"}
    payload = {"inputs": prompt}
    response = requests.post(
        "https://api-inference.huggingface.co/models/bigscience/bloom",
        headers=headers,
        json=payload
    )
    try:
        return response.json()[0]['generated_text']
    except Exception as e:
        return f"Error: {e}"

# === Response Comparison & Insight Generation === #

def analyze_response(response):
    keywords = ['quantum', 'bit', 'qubit', 'entanglement', 'superposition']
    keyword_count = sum(response.lower().count(k) for k in keywords)
    readability = textstat.flesch_reading_ease(response)
    return {
        "length": len(response),
        "keyword_matches": keyword_count,
        "readability_score": readability
    }

def compare_models(prompt):
    results = {}

    print("\nCollecting responses...\n")

    try:
        results['OpenAI'] = get_openai_response(prompt)
    except Exception as e:
        results['OpenAI'] = f"OpenAI Error: {e}"

    try:
        results['Cohere'] = get_cohere_response(prompt)
    except Exception as e:
        results['Cohere'] = f"Cohere Error: {e}"

    try:
        results['HuggingFace'] = get_huggingface_response(prompt)
    except Exception as e:
        results['HuggingFace'] = f"HuggingFace Error: {e}"

    insights = {}

    print("\nAnalyzing responses...\n")
    for model, output in results.items():
        print(f"--- {model} ---\n{output}\n")
        if "Error" not in output:
            insights[model] = analyze_response(output)
        else:
            insights[model] = {"length": 0, "keyword_matches": 0, "readability_score": 0}

    print("\n=== Summary of Insights ===\n")
    for model, metrics in insights.items():
        print(f"{model}: Length={metrics['length']}, Keywords Matched={metrics['keyword_matches']}, Readability Score={metrics['readability_score']:.2f}")

    best = max(insights.items(), key=lambda x: (x[1]['keyword_matches'], x[1]['readability_score']))
    print(f"\n📌 Best model for this prompt: **{best[0]}** based on keyword usage and readability.")

if __name__ == "__main__":
    compare_models(prompt)
```

---

## 📊 Features Compared

| Metric              | Description                                     |
| ------------------- | ----------------------------------------------- |
| `length`            | Response character count                        |
| `keyword_matches`   | Frequency of domain-related keywords            |
| `readability_score` | Ease of understanding (higher = easier to read) |

---

## 🔚 Output Example

```
=== Summary of Insights ===

OpenAI: Length=582, Keywords Matched=5, Readability Score=65.42
Cohere: Length=503, Keywords Matched=3, Readability Score=59.10
HuggingFace: Length=481, Keywords Matched=2, Readability Score=44.25

📌 Best model for this prompt: OpenAI based on keyword usage and readability




# Result: The corresponding Prompt is executed successfully

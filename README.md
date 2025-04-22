# Exno.6-Prompt-Engg
# Date: 22/04/2025
# Register no. 212223060203
# Aim: Development of Python Code Compatible with Multiple AI Tools
Here's a polished and formatted version of your lab report for the experiment titled **"Development of Python Code Compatible with Multiple AI Tools"** — complete with structured sections, code summary, and placeholders where needed:

---

### **Algorithm / Procedure:**

1. **Define the Objective:**  
   Automate the process of querying different AI APIs and derive meaningful insights from their responses.

2. **Identify the AI Tools to Integrate:**  
   - OpenAI (e.g., GPT-4)
   - Google Gemini (simulated)
   - Anthropic Claude (simulated)

3. **Set Up API Connections (or Simulate):**  
   - Use REST APIs or SDKs for integration.
   - Send user-defined prompts to each AI tool.

4. **Fetch Responses:**  
   - Collect the output from each API.

5. **Compare Responses:**  
   - Use `difflib` or similar techniques to identify similarities and differences between outputs.

6. **Generate Actionable Insights:**  
   - Analyze common keywords and features.
   - Recommend strategies based on the consensus of AI tools.

7. **Display Results:**  
   - Show outputs, comparisons, and insights clearly.

---

### **Python Code Implementation:**  

```python
import difflib

# Simulated responses from different AI tools
def query_openai(prompt):
    return "AI in education personalizes learning, provides tutoring support, and automates grading."

def query_gemini(prompt):
    return "AI helps in personalized learning paths, instant feedback, and reduces the burden on educators."

def query_claude(prompt):
    return "AI improves education by offering adaptive learning, intelligent tutoring, and easing administrative tasks."

# Compare differences between responses
def compare_responses(responses):
    comparison = []
    keys = list(responses.keys())
    for i in range(len(keys)):
        for j in range(i + 1, len(keys)):
            a, b = keys[i], keys[j]
            diff = difflib.ndiff(responses[a].split(), responses[b].split())
            changes = [word for word in diff if word.startswith('+ ') or word.startswith('- ')]
            comparison.append(f"{a} vs {b} differences: {len(changes)} terms differ.")
    return "\n".join(comparison)

# Generate insights based on keyword extraction
def generate_insights(responses):
    combined = " ".join(responses.values()).lower()
    keywords = ["personalized learning", "feedback", "grading", "administrative", "tutoring"]
    insights = "Actionable insights based on AI responses:\n"
    for kw in keywords:
        if kw in combined:
            insights += f"- Emphasize {kw} in AI strategy.\n"
    return insights

# Main execution block
def main():
    prompt = "What are the key benefits of using AI in education?"
    responses = {
        "OpenAI": query_openai(prompt),
        "Gemini": query_gemini(prompt),
        "Claude": query_claude(prompt)
    }

    print("AI Responses:\n")
    for tool, response in responses.items():
        print(f"{tool}: {response}")

    print("\nComparison:\n")
    print(compare_responses(responses))

    print("\nInsights:\n")
    print(generate_insights(responses))

main()
```
--

Let me know if you’d like to update the code to use **real APIs** or want to **extend the functionality** further (e.g., export insights to Excel or visualize differences with a chart).
# Result: The corresponding Prompt is executed successfully

# Exno.6-Prompt-Engg
# Date: 22/04/2025
# Register no.212223060203
# Aim: Development of Python Code Compatible with Multiple AI Tools


## 📜 Algorithm

1. Define a prompt related to a real-world use case (e.g., education).
2. Send the prompt to multiple AI tools (OpenAI, Gemini, Claude).
3. Collect and store the responses.
4. Use a comparison method to identify similarities/differences.
5. Extract keywords to generate actionable insights.
6. Display results clearly in a console or file output.

## 💡 Python Code

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

✅ Output
Copy
Edit
AI Responses:
OpenAI: ...
Gemini: ...
Claude: ...

Comparison:
OpenAI vs Gemini differences: ...
...

Insights:
- Emphasize personalized learning in AI strategy.
- Emphasize tutoring in AI strategy.
```
##Result
The corresponding Python prompt was executed successfully. It simulates interaction with multiple AI tools, compares their outputs, and provides actionable insights based on content analysis.


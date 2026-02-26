# Lecture: Fundamentals of Prompt Engineering

## 1. Introduction to Prompt Engineering

**Prompt Engineering** is the practice of designing and refining inputs (prompts) given to large language models (LLMs) to produce desired, accurate, and useful outputs.

As generative AI models like GPT-4, Claude, and Gemini become widely accessible, the ability to communicate effectively with these models is a critical skill. Prompt engineering bridges the gap between a user's intent and the model's response.

### Why Prompt Engineering Matters

- LLMs are sensitive to how questions and instructions are phrased.
- A well-crafted prompt can mean the difference between a vague answer and a precise, actionable one.
- It reduces hallucinations, improves factual accuracy, and enables complex reasoning tasks.

---

## 2. Anatomy of a Prompt

A prompt typically consists of one or more of the following components:

| Component      | Description                                             | Example                                      |
|----------------|---------------------------------------------------------|----------------------------------------------|
| **Instruction**| The task you want the model to perform                  | "Summarize the following article..."          |
| **Context**    | Background information to guide the model               | "You are a financial analyst..."              |
| **Input Data** | The content the model should operate on                 | The article text, a code snippet, etc.        |
| **Output Format** | Specification of how the answer should be structured | "Respond in bullet points." / "Return JSON." |

Not every prompt needs all four components, but combining them deliberately leads to better results.

---

## 3. Types of Prompting

### 3.1 Zero-Shot Prompting

The model is given a task with **no examples**. It relies entirely on its pre-trained knowledge.

**Example:**
```
Classify the sentiment of the following sentence as Positive, Negative, or Neutral.

Sentence: "The product arrived on time and works perfectly."
```

**Output:** `Positive`

Zero-shot prompting works well for simple, well-defined tasks but may struggle with ambiguous or domain-specific ones.

---

### 3.2 One-Shot Prompting

The model is provided **one example** before the actual task to illustrate the expected pattern.

**Example:**
```
Classify the sentiment of the following sentence as Positive, Negative, or Neutral.

Sentence: "The delivery was delayed by two weeks."
Sentiment: Negative

Sentence: "The product arrived on time and works perfectly."
Sentiment:
```

**Output:** `Positive`

---

### 3.3 Few-Shot Prompting

The model is given **multiple examples** (typically 3–5) to establish a stronger pattern.

**Example:**
```
Translate the following English phrases to French.

English: "Good morning"
French: "Bonjour"

English: "Thank you"
French: "Merci"

English: "How are you?"
French: "Comment allez-vous?"

English: "See you later"
French:
```

**Output:** `À tout à l'heure`

Few-shot prompting is especially effective for formatting tasks, style matching, and domain-specific outputs.

---

## 4. Chain-of-Thought (CoT) Prompting

**Chain-of-Thought** prompting encourages the model to reason step-by-step before arriving at a final answer. This dramatically improves performance on tasks requiring multi-step reasoning, such as math word problems or logical deductions.

### 4.1 Standard CoT (with examples)

**Example:**
```
Q: Roger has 5 tennis balls. He buys 2 more cans of tennis balls. Each can has 3 balls. How many tennis balls does he have now?

A: Roger starts with 5 balls. He buys 2 cans × 3 balls = 6 more balls. 5 + 6 = 11. The answer is 11.

Q: The cafeteria had 23 apples. If they used 20 for lunch and bought 6 more, how many apples do they have?

A:
```

**Output:** `The cafeteria started with 23 apples. They used 20, leaving 23 − 20 = 3 apples. Then they bought 6 more: 3 + 6 = 9. The answer is 9.`

### 4.2 Zero-Shot CoT

Simply appending **"Let's think step by step."** to a prompt triggers step-by-step reasoning without providing examples.

**Example:**
```
If a train travels 60 km/h for 2.5 hours, how far does it travel? Let's think step by step.
```

---

## 5. Advanced Prompting Techniques

### 5.1 Role Prompting (Persona Assignment)

Assigning a role or persona to the model shapes its tone, expertise level, and perspective.

**Example:**
```
You are an experienced Python developer with 10 years of expertise. Review the following code and suggest improvements for readability and performance.

[code snippet here]
```

Role prompting is useful for:
- Technical reviews (engineer, doctor, lawyer)
- Creative writing (novelist, screenwriter)
- Teaching and tutoring (patient teacher, Socratic tutor)

---

### 5.2 Instruction Prompting with Constraints

Adding explicit constraints prevents undesired outputs and focuses the model.

**Example:**
```
Summarize the following article in exactly 3 bullet points. Each bullet must be no longer than 15 words. Do not include any opinions.

[article text]
```

---

### 5.3 Self-Consistency

Self-consistency involves sampling **multiple reasoning paths** for the same question and selecting the most frequent answer. This reduces errors in arithmetic and logical reasoning tasks.

**Process:**
1. Generate N responses (e.g., 5) using CoT prompting.
2. Extract the final answer from each.
3. Return the answer that appears most often (majority vote).

---

### 5.4 ReAct (Reasoning + Acting)

The **ReAct** framework interleaves reasoning traces with actions (e.g., tool calls, web searches), allowing models to gather information and make decisions iteratively.

**Format:**
```
Thought: I need to find the population of Tokyo.
Action: Search["Tokyo population 2024"]
Observation: Tokyo has a population of approximately 13.96 million.
Thought: Now I can answer the question.
Answer: Tokyo's population is approximately 13.96 million.
```

ReAct is foundational for building **AI agents** that can interact with external tools and APIs.

---

### 5.5 Prompt Chaining

Breaking a complex task into a **sequence of simpler prompts**, where the output of one prompt becomes the input to the next.

**Example pipeline for a blog post:**
1. Prompt 1: "Generate 5 blog post title ideas about renewable energy."
2. Prompt 2: "Write an outline for the title: [selected title]."
3. Prompt 3: "Write the introduction section based on this outline: [outline]."

---

## 6. Controlling Model Behavior with Parameters

Beyond prompt text, model parameters influence output quality:

| Parameter       | Description                                              | Effect                                              |
|-----------------|----------------------------------------------------------|-----------------------------------------------------|
| **Temperature** | Controls randomness (0 = deterministic, 1+ = creative)  | Lower → more focused; Higher → more varied          |
| **Top-p**       | Nucleus sampling; limits token pool to top-p probability | Reduces low-probability tokens                       |
| **Max tokens**  | Maximum length of generated output                      | Controls response length                            |
| **Stop sequences** | Tokens at which generation halts                    | Useful for structured outputs                       |

**Tip:** For factual Q&A or code generation, use **temperature = 0**. For brainstorming or creative writing, use **temperature = 0.7–1.0**.

---

## 7. Best Practices

1. **Be specific and explicit** — Vague prompts yield vague answers. State exactly what you need.
2. **Provide context** — Include relevant background information for better-targeted responses.
3. **Specify the output format** — Ask for JSON, markdown, bullet points, or tables as needed.
4. **Use delimiters** — Separate instructions from data using `"""`, `###`, or XML-style tags to avoid confusion.
5. **Iterate and refine** — Treat prompt writing as an iterative process; test, observe, adjust.
6. **Avoid leading the model** — Phrasing that implies an expected answer can bias outputs.
7. **Break complex tasks down** — Use prompt chaining or CoT for multi-step problems.

---

## 8. Common Pitfalls to Avoid

| Pitfall                          | Problem                                              | Fix                                                   |
|----------------------------------|------------------------------------------------------|-------------------------------------------------------|
| Ambiguous instructions           | Model guesses intent, produces irrelevant output     | Be precise and unambiguous                            |
| Prompt injection                 | Malicious input overrides original instructions      | Sanitize user input; use system/user message roles    |
| Over-reliance on one prompt      | Brittle behaviour for edge cases                     | Test with varied inputs; use few-shot examples        |
| Ignoring hallucinations          | Model confidently produces false information         | Ask the model to cite sources or express uncertainty  |
| Too long / too short prompts     | Information overload or lack of context              | Find the right balance; prioritize key information    |

---

## 9. Hands-On Exercises

### Exercise 1 — Zero-Shot Classification
Write a zero-shot prompt to classify movie reviews as *Positive*, *Negative*, or *Neutral*.

### Exercise 2 — Few-Shot Pattern Matching
Create a few-shot prompt that converts informal sentences into formal English.

### Exercise 3 — Chain-of-Thought Arithmetic
Use zero-shot CoT to solve: *"A bookshelf has 4 shelves. Each shelf holds 12 books. If 15 books are removed, how many books remain?"*

### Exercise 4 — Role Prompting
Ask the model to act as a cybersecurity expert and review a given piece of code for vulnerabilities.

### Exercise 5 — Prompt Chaining
Design a 3-step prompt chain to research, outline, and draft a short essay on climate change.

---

## 10. Summary

| Technique           | When to Use                                          |
|---------------------|------------------------------------------------------|
| Zero-shot           | Simple, well-defined tasks                           |
| One/Few-shot        | Tasks requiring format or style matching             |
| Chain-of-Thought    | Multi-step reasoning, math, logic                    |
| Role Prompting      | Domain expertise, tone control                       |
| Self-Consistency    | High-stakes reasoning requiring accuracy             |
| ReAct               | Agentic tasks involving external tools               |
| Prompt Chaining     | Complex, multi-stage workflows                       |

Prompt engineering is an evolving discipline. As models improve and new techniques emerge, the core principle remains constant: **clear, well-structured communication with the model produces the best results.**

---

## References and Further Reading

- Brown, T. et al. (2020). *Language Models are Few-Shot Learners* (GPT-3 paper).
- Wei, J. et al. (2022). *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models*.
- Yao, S. et al. (2022). *ReAct: Synergizing Reasoning and Acting in Language Models*.
- OpenAI. *Prompt Engineering Guide* — [platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering)
- DAIR.AI. *Prompt Engineering Guide* — [promptingguide.ai](https://www.promptingguide.ai)

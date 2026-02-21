<div align="center">

# 🤖 Fundamentals of Generative AI & Prompt Engineering

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Generative AI](https://img.shields.io/badge/Generative%20AI-LLMs-orange?logo=openai&logoColor=white)]()
[![Prompt Engineering](https://img.shields.io/badge/Prompt-Engineering-purple)]()
[![Status](https://img.shields.io/badge/Status-Active-brightgreen)]()

<p align="center">
  A comprehensive guide to understanding <strong>Generative AI</strong> concepts and mastering <strong>Prompt Engineering</strong> techniques for building intelligent applications.
</p>

</div>

---

## 📚 Table of Contents

- [🌟 Overview](#-overview)
- [🧠 What is Generative AI?](#-what-is-generative-ai)
- [📖 Topics Covered](#-topics-covered)
- [🔧 Prompt Engineering Techniques](#-prompt-engineering-techniques)
- [🚀 Getting Started](#-getting-started)
- [📂 Repository Structure](#-repository-structure)
- [💡 Key Concepts](#-key-concepts)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## 🌟 Overview

This repository serves as a **learning resource** for anyone looking to understand the fundamentals of **Generative AI (Gen AI)** and **Prompt Engineering**. It covers the core concepts, tools, and best practices needed to effectively work with large language models (LLMs) and build AI-powered applications.

> 💬 *"Prompt Engineering is the art of communicating effectively with AI to unlock its full potential."*

---

## 🧠 What is Generative AI?

**Generative AI** refers to a class of AI models that can generate new content — text, images, audio, code, and more — based on patterns learned from training data.

| 🔑 Key Terms | 📝 Description |
|---|---|
| **LLM** | Large Language Model — e.g., GPT-4, Gemini, Claude |
| **Transformer** | The neural network architecture powering most modern LLMs |
| **Token** | The basic unit of text processed by language models |
| **Embedding** | Vector representation of words/sentences for semantic understanding |
| **Fine-tuning** | Adapting a pre-trained model to a specific task or domain |

---

## 📖 Topics Covered

### 🤖 Generative AI Fundamentals

- 🔹 History and evolution of AI → Machine Learning → Deep Learning → Gen AI
- 🔹 How Large Language Models (LLMs) work
- 🔹 Transformer architecture and attention mechanisms
- 🔹 Popular models: GPT, BERT, LLaMA, Gemini, Claude
- 🔹 AI ethics, bias, and responsible AI practices
- 🔹 Hallucinations and limitations of Gen AI models

### ✍️ Prompt Engineering

- 🔹 What is a prompt and why it matters
- 🔹 Anatomy of an effective prompt
- 🔹 System prompts vs. user prompts
- 🔹 Instruction tuning and alignment

### 🛠️ Practical Applications

- 🔹 Text summarization and generation
- 🔹 Code generation and debugging with AI
- 🔹 Question answering and knowledge retrieval
- 🔹 Chatbot and conversational AI design
- 🔹 RAG (Retrieval-Augmented Generation)

---

## 🔧 Prompt Engineering Techniques

| 🏷️ Technique | 📋 Description | 📌 Example Use Case |
|---|---|---|
| **Zero-Shot Prompting** | Ask the model without any examples | Simple Q&A, classification |
| **Few-Shot Prompting** | Provide a few examples in the prompt | Sentiment analysis, translation |
| **Chain-of-Thought (CoT)** | Guide the model to reason step-by-step | Math problems, logical reasoning |
| **Role Prompting** | Assign a persona or role to the model | Customer support, expert advice |
| **Tree of Thoughts (ToT)** | Explore multiple reasoning paths | Complex decision-making |
| **ReAct Prompting** | Combine reasoning and acting | Agent-based tasks |
| **Self-Consistency** | Sample multiple outputs and aggregate | Reliable answers |

---

## 🚀 Getting Started

### Prerequisites

- 🐍 Python 3.8+
- 📦 pip (Python package manager)
- 🔑 API key for your preferred LLM (OpenAI, Google, Anthropic, etc.)

### Installation

```bash
# Clone the repository
git clone https://github.com/Harish-57-AIML-A/FUNDAMENTALS-OF-GEN-AI-AND-PROMPT-ENGINEERING.git

# Navigate into the project directory
cd FUNDAMENTALS-OF-GEN-AI-AND-PROMPT-ENGINEERING

# (Optional) Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies (if any)
pip install -r requirements.txt
```

### Quick Example

```python
# Example: Zero-Shot Prompting with OpenAI
from openai import OpenAI

client = OpenAI(api_key="your-api-key")

prompt = "Classify the sentiment of the following text as Positive, Negative, or Neutral: 'I love learning about AI!'"

response = client.chat.completions.create(
    model="gpt-4",
    messages=[{"role": "user", "content": prompt}]
)

print(response.choices[0].message.content)
# Output: Positive
```

---

## 📂 Repository Structure

```
📦 FUNDAMENTALS-OF-GEN-AI-AND-PROMPT-ENGINEERING
├── 📄 README.md              # Project documentation
├── 📄 LICENSE                # MIT License
├── 📄 .gitignore             # Git ignore rules
└── 📁 (more content coming soon...)
```

---

## 💡 Key Concepts

<details>
<summary>🔍 <strong>What is a Token?</strong></summary>

A **token** is the basic unit of text that a language model processes. It can be a word, part of a word, or a punctuation mark. For example, `"Hello, world!"` might be split into tokens like `["Hello", ",", " world", "!"]`.

</details>

<details>
<summary>🔍 <strong>What is Temperature in LLMs?</strong></summary>

**Temperature** controls the randomness of the model's output:
- `Temperature = 0` → Deterministic, always picks the most likely token (good for factual tasks)
- `Temperature = 1` → Balanced creativity (general use)
- `Temperature > 1` → More random and creative (good for brainstorming)

</details>

<details>
<summary>🔍 <strong>What is RAG (Retrieval-Augmented Generation)?</strong></summary>

**RAG** is a technique that enhances LLM responses by retrieving relevant documents from a knowledge base before generating an answer. This helps ground the model's responses in factual, up-to-date information and reduces hallucinations.

</details>

<details>
<summary>🔍 <strong>What are Hallucinations in AI?</strong></summary>

**Hallucinations** occur when an AI model generates information that sounds plausible but is factually incorrect or fabricated. Prompt engineering techniques like providing context, asking the model to cite sources, or using RAG can help mitigate hallucinations.

</details>

---

## 🤝 Contributing

Contributions are **welcome and encouraged**! 🎉

1. 🍴 Fork the repository
2. 🌿 Create a new branch (`git checkout -b feature/your-feature`)
3. ✏️ Make your changes
4. 💾 Commit your changes (`git commit -m 'Add: your feature description'`)
5. 📤 Push to the branch (`git push origin feature/your-feature`)
6. 🔁 Open a Pull Request

Please ensure your contributions follow the existing structure and add value to learners.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

### ⭐ If you find this repository helpful, please give it a star!

Made with ❤️ by [Harish Kumar V](https://github.com/Harish-57-AIML-A)

[![GitHub followers](https://img.shields.io/github/followers/Harish-57-AIML-A?style=social)](https://github.com/Harish-57-AIML-A)
[![GitHub stars](https://img.shields.io/github/stars/Harish-57-AIML-A/FUNDAMENTALS-OF-GEN-AI-AND-PROMPT-ENGINEERING?style=social)](https://github.com/Harish-57-AIML-A/FUNDAMENTALS-OF-GEN-AI-AND-PROMPT-ENGINEERING)

</div>
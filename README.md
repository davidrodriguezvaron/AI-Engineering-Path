<div align="center">

# Applied AI & Intelligent Systems Lab

**Engineering Journal & R&D Repository**

[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
![Python](https://img.shields.io/badge/python-3.10+-blue.svg)
![Domain](https://img.shields.io/badge/Domain-Generative_AI_&_Systems-blueviolet)

_A comprehensive exploration of the modern Artificial Intelligence stack, focusing on the convergence of Software Engineering and Generative AI._

</div>

---

## 🧭 Project Scope

This repository serves as a central hub for mastering the technical landscape of **Applied Artificial Intelligence**.

As the industry shifts from deterministic coding to probabilistic systems, this lab documents the journey of adapting robust engineering practices to the fluid nature of AI. It covers the full lifecycle: from understanding LLM fundamentals to deploying autonomous, governed systems.

## 🧠 Knowledge Domains

The repository is organized into strategic domains of AI Engineering. Each domain focuses on a specific set of skills and technologies:

| Domain                         | Description                                                           | Key Technologies                       |
| :----------------------------- | :-------------------------------------------------------------------- | :------------------------------------- |
| **01. ML & Deep Learning**     | Foundations of supervised/unsupervised learning and neural networks.  | `scikit-learn`, `TensorFlow`, `OpenAI` |
| **02. GenAI Foundations**      | Prompt engineering, API integration, and model behavior analysis.     | `OpenAI`, `Anthropic`, `HuggingFace`   |
| **03. Cognitive Architecture** | Retrieval-Augmented Generation (RAG) and Vector Search strategies.    | `ChromaDB`, `Pinecone`, `LlamaIndex`   |
| **04. Autonomous Systems**     | Agentic workflows, tool use, and multi-agent orchestration.           | `LangChain`, `LangGraph`, `AutoGen`    |
| **05. AI Governance**          | Reliability engineering, safety guardrails, and evaluation metrics.   | `TruLens`, `Guardrails AI`, `Arize`    |
| **06. Edge & Optimization**    | Efficient inference and deploying models to constrained environments. | `TinyML`, `ONNX`, `Quantization`       |

## 🏗️ Philosophy: "Software 3.0"

This project adopts a "Software 3.0" mindset, treating Neural Networks and LLMs as a new type of software component that requires:

- 🔭 **Observability**: Understanding _why_ the model acts the way it does.
- 🎯 **Determinism**: Forcing structure onto probabilistic outputs.
- 🛡️ **Safety**: Ensuring systems align with human intent and business logic.

## 📂 Repository Structure

```text
├── 📘 docs/                    # Theoretical notes & course documentation
│   └── claude_code/            # Claude Code DeepLearning.AI notes
├── 📓 notebooks/               # Interactive research & learning modules
│   ├── 01_foundations/         # ML Fundamentals & Prompt Engineering
│   ├── 02_rag_vectors/         # RAG Architecture & Vector Databases
│   ├── 03_agents_tools/        # Autonomous Agents & Tool Integration
│   └── ...
├── 📦 src/                     # Core logic and modular Python source
├── 💾 data/                    # Managed datasets for training/testing
└── 📄 requirements.txt         # Project-wide dependencies
```

## 🚀 Usage & Setup

Follow these steps to set up your environment:

1.  **Clone the repository**

    ```bash
    git clone https://github.com/davidrodriguezvaron/AI-Engineering-Path.git
    cd AI-Engineering-Path
    ```

2.  **Create a Virtual Environment**

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate  # On Windows: .venv\Scripts\activate
    ```

3.  **Install dependencies**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Configure environment**
    ```bash
    cp .env.example .env
    # Edit .env with your API keys
    ```

---

### 📜 Disclaimer

This repository is a personal learning journal based on courses from [**DeepLearning.AI**](https://www.deeplearning.ai/). The notebooks and code here are my own notes and adaptations used to reinforce my understanding of the material. All original course content remains the intellectual property of DeepLearning.AI and its instructors.

If you're interested in the source material, I highly recommend enrolling in their official courses.

---

<div align="center">

_Engineered by David Armando Rodríguez Varón_

</div>

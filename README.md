# RAG Agent for Student Visa & Study Abroad Procedures

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Status: In Development](https://img.shields.io/badge/Status-In%20Development-orange)
![Python Version](https://img.shields.io/badge/Python-3.9%2B-brightgreen)

A sophisticated RAG (Retrieval-Augmented Generation) agent designed to provide clear, accurate, and sourced answers to common questions about the U.S. F-1 student visa process.

## 🌐 Overview

Navigating the U.S. student visa process is a significant challenge for international students. Critical information regarding F-1 visas, I-20 forms, SEVIS fees, and DS-160 applications is scattered across numerous, often dense, government and university websites. This fragmentation leads to confusion, repetitive questions, and reliance on unreliable sources.

This project implements a specialized RAG agent that centralizes and simplifies this information. By leveraging official U.S. government and university sources, the agent provides trustworthy, high-level guidance and direct links to the original documents, ensuring users receive factual and verifiable information.

**Disclaimer:** This tool does not provide legal advice or predict application outcomes. It is intended for informational purposes only. Users should always consult official sources and legal professionals for personalized advice.

## 🎯 Target Audience

This agent is built to assist:
- **Prospective International Students:** The primary users seeking to understand the visa application steps.
- **Parents & Guardians:** Supporting students through the process.
- **High School Counselors:** Advising students on study abroad requirements.
- **University International Student Advisors:** Aiding their admitted students.

## ✨ Key Features

- **Accurate Q&A:** Answers questions using a curated knowledge base of official policies and manuals.
- **Source Citations:** Every answer includes links to the original sources, promoting transparency and trust.
- **Safety First:** An integrated safety layer prevents the model from generating legal advice or making predictions.
- **Modern Architecture:** Built on a simple yet powerful RAG pipeline optimized for accuracy and efficiency.

## 🛠️ Architecture and Technology Stack

The agent follows a classic RAG pipeline designed for clarity and performance.

**Pipeline:** `Ingestion` → `Chunking` → `Embedding` → `Vector Store` → `Retrieval` → `LLM Generation` → `Safety Layer`

| Component | Technology/Model | Rationale |
| :--- | :--- | :--- |
| **Language Model (LLM)** | `GPT-4.1 mini` | Superior reasoning for policy-based questions. |
| **Embeddings** | `OpenAI text-embedding-3-small` | Strong multilingual accuracy and performance. |
| **Vector Database** | `Chroma` | Simple, efficient, and ideal for local setup. |
| **Chunking Strategy** | Heading-based | 256–512 tokens with small overlap for semantic coherence. |
| **Retrieval Strategy** | Vector Search (`top_k=5`) | Effective for well-structured, factual documents. |
| **Safety Layer** | Custom Implementation | Ensures no legal advice is dispensed. |

## 📈 Success Criteria

The success of this project is measured against the following criteria:

- **≥80% correct answers** on the evaluation question set.
- **100% of answers** provide at least one citation.
- **≤4s average latency** per query.
- **No answers** provide personalized legal advice.

## 🚀 Getting Started

*(This section is a placeholder for setup instructions)*

### Prerequisites
- Python 3.9+
- An OpenAI API Key

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/RAG-miniproject3-iphs-391-kocaman.git
   cd RAG-miniproject3-iphs-391-kocaman
   ```
2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set up your environment variables (e.g., in a `.env` file):
   ```
   OPENAI_API_KEY="your_api_key_here"
   ```

## ▶️ Usage

*(This section is a placeholder for usage instructions)*

To run the RAG agent, execute the main application script:
```bash
python main.py
```
You can then ask questions in the interactive terminal.

## 📊 Evaluation Plan

The model's performance will be benchmarked using a test set of 15 questions covering key aspects of the visa process:
- General visa steps
- Required documentation
- Application timing and deadlines
- SEVIS and DS-160 form details
- Travel and entry rules
- Common denial scenarios

Results are to be determined (TBD).

## 🔮 Future Work & Roadmap

To enhance the agent's capabilities, the following improvements are planned:
- **Hybrid Retrieval:** Augment vector search with keyword-based methods to improve retrieval accuracy for specific terms.
- **Reranker Integration:** Add a reranking step to refine retrieved documents before they are passed to the LLM.
- **Risk Classifier:** Implement a classifier to detect and appropriately handle questions that border on legal advice.
- **Automated Re-indexing:** Schedule a process to re-index the knowledge base each semester to keep information current.
- **Structured Outputs:** Generate structured checklists for common procedures like "Applying for an I-20" or "Preparing for the Visa Interview."

## ⚠️ Risks & Edge Cases

- **Hallucinations:** The LLM may generate plausible but incorrect information. Citations help mitigate this but do not eliminate the risk.
- **Outdated Data:** Visa policies change. The agent's knowledge base can become stale if not regularly updated.
- **Misinterpretation:** Users might interpret the agent's responses as definitive legal advice despite disclaimers.
- **Complex Documents:** Long, unstructured government PDFs and country-specific variations pose a challenge for the current chunking and retrieval strategy.

## 📜 License

This project is licensed under the [MIT License](LICENSE).
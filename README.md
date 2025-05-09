# NLP-RAG-QA-System

## Project Summary
This project explores the implementation of a Retrieval Augmented Generation (RAG) system designed to enhance question answering capabilities for two distinct user groups within a tech company — the engineering team and the marketing team. The system utilizes a RAG approach to generate contextually accurate and relevant answers by retrieving and leveraging document content before generating text responses.

- **Problem:** Efficiently answering questions related to Natural Language Processing (NLP) and Generative AI for teams with different levels of expertise.
- **Solution:** A RAG system with customized configurations for each team, providing technically detailed responses for the engineering team and simplified, clear explanations for the marketing team.
- **Target Users:** Engineering team (technical responses) and marketing team (non-technical responses).

---

## Key Features
- **Customized Responses:** Separate RAG configurations for engineering (technical) and marketing (simplified) teams.
- **Multi-Model Support:** Configurations tested with Mistral-7B and Cohere's LLMs for text generation.
- **Dynamic Prompts:** Tailored prompts for each user group to optimize response relevance.
- **Context Management:** Text chunking with overlap for enhanced context preservation.
- **Comprehensive Evaluation:** Performance metrics including cosine similarity, BLEU score, and ROUGE-2 score.

---

## How It Works
1. **Document Retrieval:** The RAG system retrieves relevant text chunks from the vector store using semantic search.
2. **Contextual Response Generation:** The retrieved text is used to generate a response using a large language model (LLM).
3. **Custom Prompts:** Two separate prompts are designed:
   - **Engineering Team:** Technical, detailed responses.
   - **Marketing Team:** Simple, clear responses without complex jargon.
4. **Evaluation:** Model responses are evaluated against gold answers using three metrics:
   - Cosine Similarity (semantic similarity)
   - BLEU Score (grammatical precision)
   - ROUGE-2 Score (text overlap)

---

## Performance Metrics
| Configuration           | LLM       | Embedding Model          | Chunk Size | Overlap | Temperature | Cosine Similarity | BLEU Score | ROUGE-2 Score |
|-------------------------|------------|---------------------------|-------------|---------|--------------|-------------------|-------------|----------------|
| Baseline Engineering     | Mistral     | multi-qa-mpnet-base-dot-v1 | 128         | 0       | 0.6          | 0.6943             | 0.0483      | 0.0825          |
| Best Engineering         | Cohere      | multi-qa-mpnet-base-dot-v1 | 128         | 25      | 0.6          | 0.8016             | 0.0381      | 0.0897          |
| 2nd Best Engineering     | Mistral     | all-distilroberta-v1       | 128         | 25      | 0.6          | 0.7643             | 0.0349      | 0.0688          |
| Baseline Marketing       | Mistral     | multi-qa-mpnet-base-dot-v1 | 128         | 0       | 0.6          | 0.7064             | 0.0366      | 0.0767          |
| Best Marketing           | Mistral     | all-distilroberta-v1       | 128         | 25      | 0.8          | 0.7302             | 0.0370      | 0.0673          |

---

## Repository Structure
- **`RAG_system.ipynb`**: Jupyter notebook containing the implementation of the RAG systems, including all configurations and evaluations.
- **`NLP_RAG_paper.pdf`**: Research paper detailing the project’s objectives, methods, evaluation, and results.

---

## Lessons Learned
- **Chunking & Overlap:** Configurations with chunk overlap performed better due to better context retention.
- **Prompt Design:** Clear, tailored prompts for each team resulted in better answers.
- **Model Selection:** The multi-qa-mpnet-base-dot-v1 embedding model outperformed other tested models for this task.
- **Metric Evaluation:** Multiple evaluation metrics (cosine similarity, BLEU, ROUGE) are necessary to capture response quality.

---

## Challenges and Limitations
- Limited computational resources restricted extensive experimentation.
- Document store was more suited for engineering content, limiting marketing response quality.
- Limited diversity of LLMs tested (Mistral-7B and Cohere’s LLM).
- Prompt sensitivity significantly affected response quality.

---

## Future Improvements
- Integrate additional LLMs beyond Mistral-7B and Cohere (e.g., GPT-4, Claude, LLaMA).
- Expand the document store to include a more diverse range of texts.
- Fine-tune the LLM on NLP and Generative AI content for domain-specific knowledge.
- Conduct a comprehensive grid search to explore more hyperparameter combinations.
- Implement a user feedback loop for continuous improvement.

---

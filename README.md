# Bayan – Bilingual Citizen Feedback Analysis System


## 1. Project Overview

**Bayan** is a bilingual NLP system designed to analyze citizen feedback and complaints written in Arabic or English.
The system combines multiple Natural Language Processing (NLP) components to turn unstructured messages into structured and useful information.
Instead of manually reading and organizing every complaint, Bayan automatically analyzes the text, identifies its main topic, extracts important information, and finds previously submitted complaints with similar meanings.

The main goal is to make citizen feedback easier to understand, organize, and analyze.


## 2. Problem Description

Citizens often submit complaints and feedback in different forms, including Arabic and English messages. These messages may contain different writing styles, dialects, personal information, and descriptions of various problems.
Processing these messages manually can be time-consuming and makes it difficult to identify common issues and connect similar complaints.
Bayan addresses this problem by using NLP techniques to automatically process citizen feedback.

The system aims to:

- **Text Classification:** Identify the main category of each complaint.
- **Sentiment Analysis:** Understand the sentiment expressed in the message.
- **Named Entity Recognition (NER):** Extract important information such as names, organizations, and locations.
- **Semantic Search:** Retrieve previously submitted complaints with similar meanings.

The expected output is a structured analysis containing the complaint category, extracted entities, and similar cases.


## 3. Dataset & Model Used
Bayan uses the datasets and models developed throughout Labs 1–7.

The project includes:

- **Complaint Dataset:** Contains previously collected complaints with their titles, descriptions, and resolutions.
- **Classification Model:** A trained NLP model used to identify complaint categories.
- **NER Model:** A trained model used to recognize important entities in Arabic and English text.
- **Embedding Model:** `paraphrase-multilingual-MiniLM-L12-v2`, used to convert text into numerical representations for semantic search.
- **FAISS Index:** Stores complaint embeddings and supports efficient similarity retrieval.

- ## 4. Workflow / Architecture
Bayan follows a pipeline that processes user input and produces structured results.

### System Workflow

1. **User Input:** The user submits a complaint in Arabic or English.
2. **Preprocessing:** The text is cleaned and personal information is masked.
3. **Classification:** The complaint is assigned to a category.
4. **Sentiment Analysis:** The system identifies the sentiment of the complaint.
5. **Named Entity Recognition:** Important entities are extracted from the text.
6. **Semantic Search:** The complaint is converted into an embedding and compared with existing cases using FAISS.
7. **Result Generation:** The system returns the analysis in a structured format.

### Architecture

User Input → Preprocessing → NLP Components → Structured Results
The system uses FastAPI to connect the NLP components and provide an API for the user interface.


## 5. Results & Evaluation
Bayan will be evaluated using different metrics to measure the performance and reliability of its NLP components.

| Component | Evaluation Metric |
|---|---|
| Classification | Macro-F1 |
| Sentiment Analysis | Macro-F1 |
| Named Entity Recognition | Entity-F1 |
| Extractive QA | Exact Match / F1 |
| Semantic Search | Recall@10 and MRR@10 |
| API Performance | p99 Latency |

### Evaluation Goals
The project aims to achieve the following targets:

- Classification performance at least 8 macro-F1 points above the TF-IDF baseline.
- NER entity-F1 of at least 0.80.
- Extractive QA with at least 17 correct answers out of 20.
- Semantic search Recall@10 of at least 0.80.
- Semantic search MRR@10 of at least 0.70.
- At least 95% invariance and 90% Minimum Functionality Test (MFT) success.
- Classifier HTTP p99 latency of 40 ms or less under the specified lab conditions.

A frozen test set will be kept separate from model development and used only for final evaluation.


## 6. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data processing |
| Hugging Face Transformers | NLP models and pipelines |
| Sentence Transformers | Text embeddings |
| FAISS | Similarity search |
| FastAPI

## 7. How to Run the Project

### Requirements
- Python installed.
- Required datasets and model files available.
- Saved FAISS index and model artifacts available.



## 8. Future Improvements
Several improvements can extend Bayan's capabilities:

- **Dialect Awareness:** Improve understanding of Gulf Arabic and other Arabic dialects.
- **Batch Processing:** Analyze multiple complaints in one request.
- **Question Answering:** Allow users to ask questions about existing complaint documents.
- **Improved Semantic Search:** Introduce a two-stage retrieval and re-ranking process.
- **Model Optimization:** Explore quantization and other optimization techniques while monitoring their effect on accuracy.
- **Better Multilingual Support:** Improve performance across Arabic and English.
- **Continuous Evaluation:** Monitor model performance and identify errors across different languages, dialects, and complaint categories.

## 9. SDAIA Academy
This project is part of the Applied Natural Language Processing program at [SDAIA Academy](https://github.com/SDAIAAcademy)
<img width="411" height="310" alt="بيان2" src="https://github.com/user-attachments/assets/0a44bba0-e01b-4b31-8b45-28f0a0b6ddee" />
<img width="450" height="291" alt="بيان1" src="https://github.com/user-attachments/assets/70bed9ed-fa1f-4c26-ae86-91b432d25288" />

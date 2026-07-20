# 📊 LLM Observability and Logging

## OS3 AI Evaluation Program

**Task ID:** L1-05 – LLM Observability and Logging

**Author:** Sumit Taware

---

# 📖 Project Overview

This project demonstrates the implementation of **observability and monitoring** in a Retrieval-Augmented Generation (RAG) application using **LangChain**, **Ollama**, **ChromaDB**, and **Streamlit**.

The application allows users to upload PDF documents, ask questions related to the document, and receive AI-generated answers. Alongside the chatbot functionality, the system captures structured logs to monitor application behavior, measure performance, and simplify debugging.

The primary objective of this project is to provide visibility into the interaction between users and the Large Language Model (LLM) by recording prompts, responses, latency, approximate token usage, retrieved context, and runtime errors.

---

# 🎯 Objectives

- Build a document-based AI assistant using LangChain.
- Implement structured logging for all LLM interactions.
- Monitor prompt and response lifecycle.
- Measure response generation latency.
- Track approximate token usage.
- Improve debugging and observability of the application.

---

# ✨ Features

- 📄 PDF document upload
- 🔍 Semantic document search using ChromaDB
- 🤖 Local LLM inference using Ollama
- 💬 Question Answering (RAG)
- 📝 Structured logging
- ⏱️ Response latency measurement
- 🔢 Approximate token usage tracking
- 📚 Retrieved context logging
- ❌ Error logging and exception handling
- 🎨 Interactive Streamlit interface

---

# 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| Python | Programming Language |
| Streamlit | User Interface |
| LangChain | LLM Orchestration |
| Ollama | Local LLM |
| ChromaDB | Vector Database |
| PyPDFLoader | PDF Loading |
| RecursiveCharacterTextSplitter | Document Chunking |
| Python Logging | Structured Logging |

---

# 📂 Project Structure

```
LLM_Observability/

│── app.py
│── requirements.txt
│── README.md
│── .env.example
│
├── data/
│     └── sample.pdf
│
├── logs/
│     └── app.log
│
├── chroma_db/
│
└── screenshots/
```

---

# 🏗️ System Architecture

```
                    User
                      │
                      ▼
             Streamlit Interface
                      │
                      ▼
                Upload PDF
                      │
                      ▼
             LangChain Loader
                      │
                      ▼
               Text Chunking
                      │
                      ▼
               ChromaDB Store
                      │
                      ▼
          Retrieve Relevant Context
                      │
                      ▼
                 Ollama LLM
                      │
                      ▼
              Generated Response
                      │
                      ▼
          Logging & Observability
```

---

# 🔄 Application Workflow

1. User uploads a PDF document.
2. The document is loaded using LangChain.
3. Text is divided into smaller chunks.
4. Chunks are converted into embeddings.
5. Embeddings are stored in ChromaDB.
6. User submits a question.
7. Relevant document chunks are retrieved.
8. Ollama generates the response.
9. Prompt, response, latency, token usage, and retrieved context are logged.

---

# 📈 Observability Strategy

The application records important runtime information to monitor performance and assist with debugging.

### Prompt Logging

Every user query is stored before being sent to the LLM.

Example

```
User Question:
What is Artificial Intelligence?
```

---

### Response Logging

Every AI-generated response is recorded.

Example

```
AI Response:
Artificial Intelligence is the simulation of human intelligence by machines.
```

---

### Response Latency

The execution time required to generate each response is measured.

Example

```
Latency:
1.82 seconds
```

---

### Approximate Token Usage

The application estimates the number of tokens used for prompts and responses to provide insight into LLM usage.

Example

```
Prompt Tokens : 35
Response Tokens : 120
Total Tokens : 155
```

---

### Retrieved Context Logging

The retrieved document chunks used to generate the final answer are logged for traceability.

Example

```
Retrieved Context:

Chunk 1

Chunk 2

Chunk 3
```

---

### Error Logging

Any unexpected exceptions are recorded with timestamps to simplify troubleshooting.

---

# 📝 Sample Log Output

```
2026-07-15 09:29:45

INFO

Session ID      : 1784087985

User Question   : What is AI?

Retrieved Context:
Artificial Intelligence...

Prompt Tokens   : 18

Response Tokens : 72

Latency         : 1.84 sec

Status          : Success
```

---

# 🚀 Installation

### Step 1 – Extract the Project

Extract the project ZIP file.

---

### Step 2 – Create a Virtual Environment

```
python -m venv venv
```

---

### Step 3 – Activate the Virtual Environment

**Windows**

```
venv\Scripts\activate
```

**Linux / macOS**

```
source venv/bin/activate
```

---

### Step 4 – Install Dependencies

```
pip install -r requirements.txt
```

---

### Step 5 – Configure Environment

Create a `.env` file.

Example

```
OLLAMA_MODEL=llama3
```

---

### Step 6 – Start Ollama

```
ollama serve
```

Download the model (only if not already installed)

```
ollama pull llama3
```

---

### Step 7 – Run the Application

```
streamlit run app.py
```

---

# 📊 Design Decisions

- **LangChain** simplifies the Retrieval-Augmented Generation workflow.
- **Ollama** enables private, offline LLM inference.
- **ChromaDB** provides efficient semantic document retrieval.
- **Streamlit** offers a lightweight and user-friendly interface.
- **Structured logging** improves debugging, monitoring, and performance analysis.
- **Approximate token counting** provides useful insights without relying on external APIs.

---

# 📌 Future Improvements

- OpenTelemetry integration
- Prometheus metrics
- Grafana dashboards
- Real token counting
- Multiple LLM provider support
- Cloud deployment
- User authentication
- Log analytics dashboard

---

# ✅ Deliverables Covered

✔ Logging-enabled application

✔ Prompt logging

✔ Response logging

✔ Latency tracking

✔ Approximate token usage

✔ Structured logging

✔ Documentation of observability strategy

---

# 📚 References

- LangChain Documentation
- Ollama Documentation
- ChromaDB Documentation
- Streamlit Documentation
- Python Logging Documentation

---

# 👨‍💻 Author

**Snehal Taware**
**OS3 AI Evaluation Program**
**Task ID: L1-05 – LLM Observability and Logging**
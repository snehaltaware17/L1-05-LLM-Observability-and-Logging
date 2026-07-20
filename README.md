# LLM Logging and Observability

## Project Overview
This project demonstrates how to add **observability and monitoring** to an LLM-based application built using **LangChain**, **Ollama**, **ChromaDB**, and **Streamlit**.
The application allows users to upload PDF documents, ask questions, retrieve relevant document chunks using Retrieval-Augmented Generation (RAG), and receive AI-generated answers.
In addition to the chatbot functionality, the application captures detailed logs for monitoring and debugging purposes, including prompt logging, response logging, execution latency, approximate token usage, and retrieval metadata.
This project fulfills the requirements of **OS3 AI Evaluation - Set 1 - L1-05 (LLM Observability and Logging).**


# Features
- PDF document upload
- Automatic document chunking
- ChromaDB vector database
- Ollama LLM integration
- LangChain Retrieval-Augmented Generation (RAG)
- Streamlit web interface
- Structured logging
- Prompt logging
- Response logging
- Response latency tracking
- Approximate token usage tracking
- Error logging
- Retrieval context logging



# Technologies Used
- Python
- Streamlit
- LangChain
- Ollama
- ChromaDB
- PyPDF
- Python Dotenv



# Project Structure

LLM logging and observeability/
│
├── app.py
├── requirements.txt
├── .env
│
├── data/
│     └── sample.pdf
│
├── chroma_db/
│
├── logs/
│     └── app.log
│
└── venv/
│
└── README.md



# Architecture

                User
                  │
                  ▼
          Streamlit Interface
                  │
                  ▼
          PDF Upload / Question
                  │
                  ▼
       LangChain Document Loader
                  │
                  ▼
        Text Splitter (Chunks)
                  │
                  ▼
            Chroma Vector DB
                  │
                  ▼
       Retrieve Relevant Chunks
                  │
                  ▼
             Ollama LLM
                  │
                  ▼
            AI Generated Answer
                  │
                  ▼
        Logging & Observability




# Observability Strategy
The application records important runtime information to help monitor system performance and simplify debugging.

The following information is logged:

### Prompt Logging
Every user question submitted to the LLM is recorded.
Example:
User Question:
What is Artificial Intelligence?


### Response Logging
The AI-generated response is stored.
Example:
AI Response:
Artificial Intelligence is the simulation of human intelligence by machines.


### Latency Logging
The total time required to generate an answer is measured.
Example:
Latency:
2.14 seconds


### Approximate Token Usage
Approximate token count is calculated for both prompt and response.
Example:
Prompt Tokens : 38
Response Tokens : 112
Total Tokens : 150



### Retrieval Logging
The retrieved document chunks used for answering are logged.
Example:
Retrieved Context:
Chunk 1
Chunk 2
Chunk 3


### Error Logging
Unexpected exceptions are written into the log file with timestamps.

Example:
ERROR:
Failed to load document.


# Logging Format
The application uses structured logging with timestamps.
Example:

2026-07-15 09:29:45

INFO

Session ID : 1784087985

User Question :
What is AI

Retrieved Context :
...

Prompt Tokens : 18

Response Tokens : 74

Latency : 1.84 sec

Status : Success



# Installation

## 1. Extract the Project
Extract the project ZIP file to your desired location.
Example:
LLM logging and observeability/

## 2. Navigate to the Project Folder
cd "LLM logging and observeability"

## 3. Create a Virtual Environment
python -m venv venv

## 4. Activate the Virtual Environment
### Windows
venv\Scripts\activate
### Linux / macOS
source venv/bin/activate

## 5. Install Dependencies
pip install -r requirements.txt

## 6. Configure the Environment
Create a `.env` file and add the required configuration.
Example:
OLLAMA_MODEL=llama3

## 7. Start Ollama
ollama serve
Pull the model if it is not already installed:
ollama pull llama3

## 8. Run the Application
streamlit run app.py



# Output
The application provides

- PDF upload
- Question answering
- AI responses
- Retrieval context
- Logging
- Performance metrics

Logs are stored in:
logs/app.log



# Design Decisions

- **Streamlit** was selected for a lightweight user interface.
- **LangChain** simplifies orchestration between document retrieval and LLM inference.
- **ChromaDB** provides efficient vector storage for semantic search.
- **Ollama** enables local LLM execution without external APIs.
- **Structured logging** improves traceability, debugging, and monitoring.
- Approximate token counting provides visibility into LLM usage without requiring external APIs.


# Future Improvements

- Grafana dashboard integration
- Multiple LLM support
- User authentication
- Log analytics dashboard



# Deliverables Covered
- Logging-enabled LLM application
- Prompt logging
- Response logging
- Latency tracking
- Approximate token usage
- Structured logging
- Documentation of observability strategy
- Working Streamlit application



# Author

**Snehal Taware**
OS3 AI Evaluation
Set 1 – L1-05
LLM Observability and Logging
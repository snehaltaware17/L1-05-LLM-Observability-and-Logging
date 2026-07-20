# 📊 LLM Observability and Logging Platform

> A comprehensive document-based AI assistant with built-in observability, monitoring, and structured logging for LLM interactions.

**Task ID:** L1-05 – LLM Observability and Logging  
**Author:** Snehal Taware

---

## 📖 Project Overview

This project demonstrates enterprise-grade **observability and monitoring** in a Retrieval-Augmented Generation (RAG) application. It combines **LangChain**, **Ollama**, **ChromaDB**, and **Streamlit** to create an intelligent document Q&A system with comprehensive logging and performance tracking.

### Key Value Proposition

Users can upload PDF documents and ask questions related to the content, receiving AI-generated answers. Simultaneously, the system captures structured logs that provide complete visibility into:
- Prompt and response interactions
- Response generation latency
- Approximate token usage
- Retrieved document context
- Runtime errors and exceptions

This enables teams to monitor application behavior, debug issues efficiently, and optimize LLM performance in production environments.

---

## 🎯 Objectives

- ✅ Build a scalable document-based AI assistant using LangChain
- ✅ Implement structured logging for all LLM interactions
- ✅ Monitor prompt and response lifecycle with detailed metrics
- ✅ Measure and track response generation latency
- ✅ Estimate and log approximate token usage
- ✅ Improve debugging capabilities and system observability

---

## ✨ Features

**Core Functionality:**
- 📄 **PDF Document Upload** – Support for single and batch document uploads
- 🔍 **Semantic Search** – ChromaDB-powered semantic search across documents
- 🤖 **Local LLM Inference** – Privacy-preserving local inference using Ollama
- 💬 **Intelligent Q&A** – RAG-based question answering with context retrieval

**Observability & Monitoring:**
- 📝 **Structured Logging** – JSON and text-based logging for all interactions
- ⏱️ **Latency Tracking** – Real-time response generation latency measurement
- 🔢 **Token Usage Estimation** – Approximate token counting for cost analysis
- 📚 **Context Logging** – Retrieved document context and relevance scores
- ❌ **Error Handling** – Comprehensive exception logging and error tracking
- 📊 **Performance Metrics** – System-wide performance monitoring

**User Interface:**
- 🎨 **Interactive Streamlit Dashboard** – Intuitive web-based interface
- 🔐 **Session Management** – Persistent state across interactions

---

## 🛠️ Technologies Used

| Technology | Version | Purpose |
|------------|---------|---------|
| **Streamlit** | 1.41.1 | Interactive web interface and dashboard
| **LangChain** | 0.3.14 | LLM orchestration and RAG pipeline
| **Ollama** | Latest | Local LLM inference engine
| **ChromaDB** | 0.5.23 | Vector database for semantic search
| **PyPDF** | 5.1.0 | PDF document processing
| **Python** | 3.8+ | Programming language

---

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- Ollama installed and running (https://ollama.ai)
- pip package manager

### Installation

1. **Clone or download this repository**
   ```bash
   cd "L1-05 LLM observeability and logging"
   ```

2. **Create and activate virtual environment**
   ```bash
   # Windows
   python -m venv venv
   venv\Scripts\activate
   
   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   ```bash
   # Create .env file in project root
   echo OLLAMA_BASE_URL=http://localhost:11434 > .env
   ```

5. **Start Ollama service** (if not already running)
   ```bash
   ollama serve
   ```

6. **Run the application**
   ```bash
   streamlit run app.py
   ```

The application will open in your browser at `http://localhost:8501`

---

## 📖 Usage Guide

### Basic Workflow

1. **Upload Documents**
   - Click the upload button in the sidebar
   - Select one or more PDF files
   - Wait for document processing and vectorization

2. **Ask Questions**
   - Enter your question in the chat interface
   - The system retrieves relevant document context
   - AI generates an answer based on retrieved content

3. **View Logs**
   - Check the `logs/` directory for detailed interaction logs
   - Logs include timestamps, latency, tokens, and errors

### Example Queries

```
"What are the main topics covered in this document?"
"Summarize the methodology section"
"Find information about budget allocation"
"Explain the key findings"
```

---

## 📊 Architecture

### System Components

```
┌─────────────────────────────────────────────────────────────┐
│                    Streamlit UI Layer                       │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│              LangChain RAG Pipeline                         │
│  ┌──────────────────────────────────────────────────────┐  │
│  │ Document Loader → Text Splitter → Embeddings        │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                            ↓
        ┌───────────────────┬───────────────────┐
        ↓                   ↓                   ↓
    ┌─────────┐         ┌─────────┐       ┌──────────┐
    │ ChromaDB│         │  Ollama │       │ Logging  │
    │ Vector  │         │  LLM    │       │ System   │
    │ Store   │         │         │       │          │
    └─────────┘         └─────────┘       └──────────┘
```

### Data Flow

1. **Ingestion**: PDF documents are loaded and split into chunks
2. **Vectorization**: Text chunks are converted to embeddings
3. **Storage**: Embeddings stored in ChromaDB vector database
4. **Query**: User questions converted to embeddings
5. **Retrieval**: Relevant document chunks retrieved via similarity search
6. **Generation**: LLM generates answer using context + prompt
7. **Logging**: All interactions logged with metrics

---

## 📝 Logging Configuration

### Log Location
- **File**: `logs/app.log`
- **Format**: `TIMESTAMP | LEVEL | MESSAGE`

### Logged Information

Each LLM interaction captures:
- **Timestamp**: Precise interaction time
- **Prompt**: User question
- **Retrieved Context**: Relevant document passages
- **Response**: Generated answer
- **Latency**: Response generation time (ms)
- **Tokens**: Estimated token usage
- **Error Info**: Any exceptions or failures

### Log Levels
- `INFO`: General application flow and interactions
- `WARNING`: Potential issues requiring attention
- `ERROR`: Failed operations and exceptions
- `CRITICAL`: System failures

### Managing Logs
```bash
# View recent logs
tail -f logs/app.log

# Clear logs (keep backup first)
copy logs/app.log logs/app.log.bak
del logs/app.log
```

---

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in the project root:

```env
# Ollama Configuration
OLLAMA_BASE_URL=http://localhost:11434
OLLAMA_MODEL=mistral  # or your preferred model

# ChromaDB Configuration
CHROMADB_PERSIST_DIR=./chroma_db

# Application Settings
LOG_LEVEL=INFO
CHUNK_SIZE=500
CHUNK_OVERLAP=100
```

### Streamlit Configuration

Create `.streamlit/config.toml` for advanced settings:

```toml
[theme]
primaryColor = "#1f77b4"
backgroundColor = "#ffffff"
secondaryBackgroundColor = "#f0f2f6"

[logger]
level = "info"

[server]
maxUploadSize = 200
```

---

## 🔍 Performance Optimization

### Tips for Better Results

1. **Model Selection**: Experiment with different Ollama models
   ```bash
   ollama list                    # See available models
   ollama pull mistral           # Download a model
   ```

2. **Chunk Size Tuning**: Adjust in `.env`
   - Larger chunks: Better context, slower retrieval
   - Smaller chunks: Faster retrieval, potentially less context

3. **Vector Database**: Use persistent storage
   ```bash
   # Enable persistence in config
   CHROMADB_PERSIST_DIR=./chroma_db
   ```

---

## 🐛 Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| **Ollama connection failed** | Ensure Ollama is running: `ollama serve` |
| **Model not found** | Download model: `ollama pull mistral` |
| **Memory errors** | Reduce chunk size or use smaller model |
| **Slow responses** | Check system resources; consider GPU acceleration |
| **Logs directory missing** | Create manually: `mkdir logs` |

### Debug Mode

Enable verbose logging:
```bash
# In app.py, set logger level
logger.setLevel(logging.DEBUG)
```

---

## 📚 Project Structure

```
L1-05 LLM observeability and logging/
├── app.py                 # Main Streamlit application
├── requirements.txt       # Python dependencies
├── .env                   # Environment variables
├── .streamlit/
│   └── config.toml       # Streamlit configuration
├── logs/
│   └── app.log           # Application logs
├── chroma_db/            # Vector database (auto-created)
└── README.md             # This file
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork or clone the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Make your changes with clear commit messages
4. Test thoroughly
5. Submit a pull request with description

### Areas for Contribution
- Enhanced logging formats
- Additional LLM model support
- Performance optimizations
- UI/UX improvements
- Documentation enhancements

---

## 📄 License

This project is part of the OS3 AI Evaluation Program.

---

## 🙏 Acknowledgments

- **LangChain** team for the excellent LLM framework
- **Ollama** for enabling local LLM inference
- **ChromaDB** for vector database capabilities
- **Streamlit** for the interactive framework

---

## 📞 Support

For issues, questions, or suggestions:
1. Check the [Troubleshooting](#-troubleshooting) section
2. Review log files for detailed error information
3. Consult the [Configuration](#-configuration) section

---

## 📊 Changelog

**v1.0.0** - Initial Release
- Core RAG functionality
- Structured logging system
- Performance monitoring
- Streamlit interface

---

## 🔗 Resources

- [LangChain Documentation](https://docs.langchain.com/)
- [Ollama GitHub](https://github.com/ollama/ollama)
- [ChromaDB Documentation](https://docs.trychroma.com/)
- [Streamlit Documentation](https://docs.streamlit.io/)

---

**Last Updated:** July 2026  
**Status:** Active Development
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
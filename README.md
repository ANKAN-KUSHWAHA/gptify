# GPTIFY

GPTIFY is a agentic AI chatbot built with Python, FastAPI, LangGraph, LangChain, Google Gemini, Tavily, ChromaDB, and SQLite. It supports streamed chat, multiple conversations, web search, calculations, long-term memory, and question answering over uploaded documents.

---

## Features

- Chat with an AI agent powered by Google Gemini
- Stream responses in real time
- Upload documents such as PDF, DOCX, TXT, MD, PY, and CSV
- Use uploaded files as context through RAG
- Search the web with Tavily for current information
- Store and recall conversation history
- Simple FastAPI-based web interface
- Docker-ready deployment
- AWS CI/CD support using GitHub Actions, ECR, and EC2

---

## Project Overview

This project combines:

- **FastAPI** for the backend server and API endpoints
- **Jinja2** for rendering the frontend UI
- **LangGraph** for agent orchestration
- **LangChain** for tools, messages, and RAG workflow
- **Google Gemini** as the LLM provider
- **Tavily** for web search
- **ChromaDB** for vector search over uploaded documents
- **SQLite** for conversation and persistence
- **Docker** for containerized deployment

---

## Prerequisites

Make sure you have the following installed:

- Python 3.11
- pip or conda
- Git
- Google API key for Gemini
- Tavily API key for web search

### Optional for deployment:

- Docker
- AWS account
- Amazon ECR repository
- EC2 instance
- GitHub Actions self-hosted runner

---

## Setup on Windows

Open PowerShell in the project folder and create a virtual environment:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Create a `.env` file in the project root. Add your own keys; do not commit this file or paste real keys into the README:

```dotenv
GOOGLE_API_KEY=your_google_ai_api_key
TAVILY_API_KEY=your_tavily_api_key
GEMINI_MODEL=gemini-2.5-flash
```

The app uses `gemini-2.5-flash` by default. The frontend can select from the model names configured in `agent.py`.

---

## Run the app

From the project folder, with the virtual environment active:

```powershell
python app.py
```

Open [http://localhost:8080](http://localhost:8080) in your browser. Keep the terminal open while using the app; startup and runtime errors are printed there.

---


## Data Storage

Conversation data is stored in `data/chatbot_memory.db`; LangGraph checkpoints are stored in `data/langgraph_checkpoints.sqlite`; document vectors are stored in `chroma_db`; uploaded files are stored in `uploads`.

---

## Project Structure

```text
BappyGPT/
│
├── app.py                  # FastAPI app and streaming chat endpoints
├── agent.py                # LangGraph agent setup and tool orchestration
├── database.py             # Conversation and persistence logic
├── rag.py                  # Document ingestion and RAG logic
├── tools.py                # Agent tools such as web search, memory, and RAG
├── requirements.txt        # Python dependencies
├── Dockerfile              # Docker image configuration
├── .dockerignore           # Docker ignore rules
│
├── templates/
│   └── index.html           # Frontend UI
│
├── uploads/                 # Uploaded documents
├── data/                    # SQLite database and app data
└── chroma_db/               # ChromaDB vector database storage
```
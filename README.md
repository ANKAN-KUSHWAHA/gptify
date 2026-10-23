# GPTIFY

GPTIFY is a agentic AI chatbot built with Python, FastAPI, LangGraph, LangChain, Google Gemini, Tavily, ChromaDB, and SQLite. It supports streamed chat, multiple conversations, web search, calculations, long-term memory, and question answering over uploaded documents.


## Features
Chat with an AI agent powered by Google Gemini
Stream responses in real time
Upload documents such as PDF, DOCX, TXT, MD, PY, and CSV
Use uploaded files as context through RAG
Search the web with Tavily for current information
Store and recall conversation history
Simple FastAPI-based web interface
Docker-ready deployment
AWS CI/CD support using GitHub Actions, ECR, and EC2

## Project Overview
This project combines:

FastAPI for the backend server and API endpoints
Jinja2 for rendering the frontend UI
LangGraph for agent orchestration
LangChain for tools, messages, and RAG workflow
Google Gemini as the LLM provider
Tavily for web search
ChromaDB for vector search over uploaded documents
SQLite for conversation and persistence
Docker for containerized deployment


## Prerequisites
Make sure you have the following installed:

Python 3.11
pip or conda
Git
Google API key for Gemini
Tavily API key for web search

# Optional for deployment:

Docker
AWS account
Amazon ECR repository
EC2 instance
GitHub Actions self-hosted runner




## Requirements

- Python 3.10 or newer
- A Google AI API key for Gemini chat and document embeddings
- A Tavily API key for web search

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

## Run the app

From the project folder, with the virtual environment active:

```powershell
python app.py
```

Open [http://localhost:8080](http://localhost:8080) in your browser. Keep the terminal open while using the app; startup and runtime errors are printed there.

## Features

- Streamed Gemini chat with conversation history
- Web search through Tavily
- Calculator tool
- Long-term memory saved per conversation
- Upload and search PDF, DOCX, TXT, Markdown, Python, and CSV files

Conversation data is stored in `data/chatbot_memory.db`; LangGraph checkpoints are stored in `data/langgraph_checkpoints.sqlite`; document vectors are stored in `chroma_db`; uploaded files are stored in `uploads`.

## Troubleshooting

- **`TemplateNotFound: index.html` or a 500 error on the home page:** make sure the frontend file is named `templates/index.html`.
- **The page will not open at `0.0.0.0:8080`:** use `http://localhost:8080` in your browser. `0.0.0.0` is the server's listen address, not the browser address.
- **Gemini authentication errors:** confirm `.env` contains the exact variable name `GOOGLE_API_KEY`, with a valid key, and restart the server after changing it.
- **Web search authentication errors:** confirm `.env` contains a valid `TAVILY_API_KEY`.
- **Chat errors:** read the traceback in the terminal where `python app.py` is running; the browser may only show a generic error.

## Project files

- `app.py` — FastAPI routes and streamed chat endpoint
- `agent.py` — Gemini and LangGraph agent setup
- `tools.py` — calculator, web search, document search, and memory tools
- `database.py` — SQLite conversation and memory storage
- `rag.py` — document reading, chunking, embedding, and retrieval
- `templates/index.html` — browser interface

# Industry AI Intelligence

An AI-powered industry knowledge assistant built with **React, FastAPI, LangChain, and Retrieval-Augmented Generation (RAG)**. The application is designed to let users interact with knowledge sources, upload documents, and ask context-aware questions through a conversational interface.

## Overview

Industry AI Intelligence combines document processing, website content extraction, vector search, and language models to provide a conversational interface for accessing industry-related information.

The project uses a Retrieval-Augmented Generation (RAG) architecture to retrieve relevant information from a knowledge base before generating responses.

## Features

- **AI-powered Chat:** Conversational interface for asking questions.
- **Document Upload:** Upload documents to make their content available to the knowledge pipeline.
- **Website Ingestion:** Extract content from websites for knowledge retrieval.
- **RAG Pipeline:** Process, split, embed, and retrieve relevant content.
- **Vector Search:** FAISS-based vector storage and similarity retrieval.
- **Conversation Memory:** Maintain conversational context.
- **Chat Export:** Export conversations.
- **React Frontend:** Interactive interface with reusable components.

## Tech Stack

| Category | Technologies |
|---|---|
| Frontend | React, Vite, JavaScript |
| Styling | Tailwind CSS |
| Backend | Python, FastAPI |
| AI Framework | LangChain |
| Language Model Integration | LangChain provider integrations |
| Vector Database | FAISS |
| Document Processing | PyPDF, Docx2txt |
| Data Processing | Pandas |
| Web Scraping | BeautifulSoup, Requests |
| API Communication | Axios |

## Architecture

```text
                 User
                  |
                  v
          React Frontend
                  |
             Axios API
                  |
                  v
           FastAPI Backend
                  |
       +----------+----------+
       |          |          |
       v          v          v
   Document    Website    Chat Memory
   Processing  Loader
       |          |
       +-----+----+
             |
             v
        Text Chunking
             |
             v
         Embeddings
             |
             v
        FAISS Vector Store
             |
             v
       Similarity Retrieval
             |
             v
       LLM Response Generation
             |
             v
        React Chat Interface
```

## Project Structure

```text
industry-ai-intelligence/
│
├── backend/
│   ├── api/
│   │   ├── chat.py
│   │   ├── memory.py
│   │   ├── upload.py
│   │   └── website.py
│   │
│   ├── memory/
│   │   └── chat_memory.py
│   │
│   ├── rag/
│   │   ├── chunker.py
│   │   ├── embeddings.py
│   │   ├── init_rag.py
│   │   ├── loader.py
│   │   ├── retriever.py
│   │   ├── universal_loader.py
│   │   ├── vector_store.py
│   │   └── web_loader.py
│   │
│   ├── services/
│   │   └── llm_service.py
│   │
│   ├── main.py
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── services/
│   │   ├── utils/
│   │   ├── txt/
│   │   ├── App.jsx
│   │   ├── index.css
│   │   └── main.jsx
│   │
│   ├── index.html
│   └── package.json
│
├── knowledge_base/
│   ├── csvs/
│   ├── jsons/
│   └── pdfs/
│
├── .env.example
├── .gitignore
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.12 recommended
- Node.js and npm
- Git
- Gemini API key or the API credentials required by your configured LLM provider

### 1. Clone the Repository

```bash
git clone https://github.com/RAGINI-06/industry-ai-intelligence.git

cd industry-ai-intelligence
```

### 2. Backend Setup

Create and activate a virtual environment:

**Windows PowerShell**

```powershell
cd backend

python -m venv venv

.\venv\Scripts\Activate.ps1
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Configure environment variables using the root `.env.example` as a reference. Create a `.env` file in the location expected by your backend configuration.

Start the FastAPI server from the project root:

```bash
python -m uvicorn backend.main:app --reload --host 127.0.0.1 --port 8000
```



### 3. Frontend Setup

Open a separate terminal:

```bash
cd frontend

npm install

npm run dev
```

Open the local development URL printed by Vite, usually:

http://localhost:5173

## Environment Variables

Create a `.env` file using the following template. Add only the credentials required by your configured provider.

```env
GEMINI_API_KEY=your_gemini_api_key
```

Never commit your actual API keys or secrets to GitHub.

## How RAG Works

The application follows a Retrieval-Augmented Generation workflow:

1. **Data Ingestion:** Documents and website content are loaded.
2. **Text Processing:** Extracted content is cleaned and divided into smaller chunks.
3. **Embedding Generation:** Text chunks are converted into vector representations.
4. **Vector Storage:** Embeddings are stored in FAISS.
5. **Retrieval:** Relevant chunks are retrieved based on the user's question.
6. **Response Generation:** Retrieved context is supplied to the configured language model to generate an answer.

## Development Status

This repository is under active development. Backend integration, LLM configuration, document processing, retrieval, and deployment are being tested and improved.

## Future Improvements

- Improved conversational memory.
- Source citations for generated responses.
- Support for additional document formats.
- More robust retrieval and reranking.
- Authentication and user-specific chat history.
- Production deployment and monitoring.



## Author

**Ragini Nishad**

GitHub: https://github.com/RAGINI-06

---

*Built as a learning and development project exploring AI-powered applications, backend engineering, and Retrieval-Augmented Generation.*

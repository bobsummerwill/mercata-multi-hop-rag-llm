# 🔍 Code Search and Analysis System

A semantic code search and analysis tool that indexes your codebase using embeddings and stores it in **Weaviate**, enabling **LLM-powered queries** over both code and documentation.

---

## 🧰 Tech Stack

- **Weaviate**: Vector database for semantic search  
- **OpenAI**: Embedding generation & LLM reasoning  
- **Python**: Backend for indexing, querying, and serving APIs  
- **Docker + Docker Compose**: Containerized infrastructure  
- **Flask**: Lightweight API server  
- **Node.js + NVM**: Frontend interface for search and visualization  

---

## ⚙️ Prerequisites

- Python 3.10+  
- Docker + Docker Compose  
- `venv` (or any Python virtual environment tool)  
- Node.js 21 (via NVM) for the frontend  

---

## 📦 Installation

### 🔁 Clone the repository

```bash
git clone https://github.com/your-org/code-search-ai.git
cd code-search-ai
```

---

## 🧠 Indexing the Codebase

### 1. Set up Python backend

```bash
python3 -m venv .venv
source .venv/bin/activate  # or `.venv\Scripts\activate` on Windows
pip install -r requirements.txt
```

### 2. Start Weaviate vector DB

```bash
docker-compose up -d
```

> Weaviate will be started with the `text2vec-transformers` vectorizer plugin.

### 3. Run the code indexer

```bash
python index_codebase.py
```

This will:
- 🧹 Clean existing data  
- 🏗️ Initialize schema  
- 🧾 Parse code using Tree-sitter  
- 🔗 Extract call graphs and definitions  
- 📚 Process documentation (e.g. Markdown, docx)  
- 📡 Upload everything to Weaviate  

---

## 🌐 Starting the Search Backend (API)

```bash
python query_backend.py
```

> Exposes an API at `http://localhost:5000`.

---

## 💻 Frontend Setup

```bash
cd frontend
npm install
nvm use 21
npm run dev
```

> This will launch the frontend at `http://localhost:3000` (or specified port).

---

## 📡 API Capabilities

Once the backend is running:
- Search function and variable definitions semantically  
- Ask: “Where is function X used?”, “What calls Y?”, “What does Z mean?”  
- Retrieve and cross-link code, docs, and relationships  

---

## ⚙️ Configuration

### 🔧 Weaviate Settings

Modify:
- `docker-compose.yml` for container settings  
- Class schema, vectorizer, and module options  

### 🔑 OpenAI Settings

Set in `.env` or environment:

```bash
export OPENAI_API_KEY=your-api-key
```

### 🧠 Model Configs

Tweak inside `query_backend.py` or `embed_code.py`

---

## 🛠️ Troubleshooting

### 🔍 Weaviate Issues

```bash
docker ps                        # ensure containers are up
docker logs mercata-llm3_weaviate_1
```

- Check `.env` for valid OpenAI key  
- Ensure vector modules are enabled in Docker Compose  

### 🧩 Indexing Issues

- Tree-sitter must be installed and working  
- Watch logs for parser or schema errors  

---

## 📜 License

MIT License or Custom License — insert here.

---

## 👨‍💻 Maintainer

David Nallapu – [LinkedIn](https://linkedin.com/in/david-nallapu)

--
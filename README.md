# Local RAG Chatbot (PDF + Chroma + Ollama + Gradio)

**Created by Christian Cubides**

---

## 🌟 About This Project

This project represents **one of my first hands-on explorations into building with LLMs beyond prebuilt chat interfaces**. My goal was simple: move from *using AI* to *creating AI-powered tools*, learning the mechanics of **Retrieval-Augmented Generation (RAG)**, embeddings, and vector databases along the way.

Rather than relying on cloud APIs, I built a fully **local, self-contained chatbot** that can answer questions grounded in PDFs or manuals. This project demonstrates:

- Initiative to learn cutting-edge AI tools hands-on  
- Ability to assemble multiple technologies into a coherent pipeline  
- Understanding of embeddings, vector search, and LLM orchestration  
- Commitment to producing functional, usable prototypes  

---

## 🚀 Project Overview

This chatbot combines several components into a **retrieval-augmented system**:

| Component | Technology | Purpose |
|-----------|------------|---------|
| Embeddings | `sentence-transformers/all-MiniLM-L6-v2` | Converts text chunks into dense vectors |
| Vector Database | `ChromaDB` | Stores embeddings for fast retrieval |
| LLM | `Ollama` (`llama3.1`) | Generates answers based on retrieved context |
| PDF Loader | `PyPDFDirectoryLoader` | Loads manuals or documents from `/data` |
| Text Splitter | `RecursiveCharacterTextSplitter` | Breaks documents into chunks (300 chars, 100 overlap) |
| UI | `Gradio` | Streams responses in a web chat interface |

---

## 🧩 How It Works

1. **Ingest Documents**
   - PDFs are loaded from `/data`
   - Text is split into overlapping chunks
   - Each chunk is embedded and stored in `ChromaDB`

2. **Answer Questions**
   - User submits a query via Gradio
   - Retriever finds top 5 relevant chunks from the vector database
   - LLaMA generates an answer **using only the retrieved knowledge**
   - Response is streamed live in the chat interface

**Prompt Template Used:**


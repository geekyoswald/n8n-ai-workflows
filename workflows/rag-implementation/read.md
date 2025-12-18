# 📘 RAG Implementation Workflow

This workflow implements a Retrieval-Augmented Generation (RAG) pipeline in n8n.  
It processes documents uploaded to Google Drive, generates embeddings using OpenAI, and stores them in Pinecone for semantic search.

## 🔄 What It Does
1. Watches a Google Drive folder for new files  
2. Downloads the file into n8n  
3. Parses and splits the document  
4. Creates embeddings using OpenAI  
5. Stores embeddings inside a Pinecone index  
6. Includes an AI Agent that can answer questions using the stored knowledge  

## 🧱 Nodes Used
- **Google Drive Trigger** – watches a folder  
- **Google Drive Download** – fetches binary file  
- **Default Document Loader** – reads PDF/text  
- **Character Text Splitter** – chunks content  
- **OpenAI Embeddings** – generates vector embeddings  
- **Pinecone Vector Store** – stores vectors  
- **OpenAI Chat Model** – LLM for Q&A  
- **AI Agent** – orchestrates retrieval + answering  

## 🖼 Optional Screenshot
Add a screenshot named `screenshot.png` here.

## 🔒 Security Note
API keys and credentials are **not** included in this JSON export.

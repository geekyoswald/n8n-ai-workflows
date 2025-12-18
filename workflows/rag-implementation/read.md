# 📘 RAG Implementation Workflow (Google Drive → OpenAI → Pinecone)

This workflow implements a **Retrieval-Augmented Generation (RAG)** pipeline using n8n, OpenAI, LangChain, and Pinecone.  
It automatically watches a Google Drive folder for new documents, processes them, generates embeddings, and stores them in a vector database for semantic search and AI-powered Q&A.

---

## 🔄 What This Workflow Does

### **1. Watches a Google Drive folder for new files**
- Uses **Google Drive Trigger**
- Detects when a new document is uploaded to the configured folder

### **2. Downloads the file**
- Retrieves the binary file from Google Drive

### **3. Loads and splits the document**
Using LangChain components:
- **Document Loader** processes PDF/text files  
- **Character Text Splitter** breaks the content into chunks suitable for embeddings

### **4. Generates embeddings**
- Creates vector embeddings using **OpenAI Embeddings**

### **5. Stores embeddings in Pinecone**
- Saves chunks into the Pinecone index  
- Uses the namespace `n8n_demo` to organize data  

This enables fast and accurate semantic retrieval.

### **6. Includes an AI Chat Agent for querying**
The workflow includes an optional AI agent that can:
- Retrieve relevant information from Pinecone  
- Use an OpenAI model to generate answers  
- Respond to user queries through a chat interface  

---

## 🧱 Node Breakdown

| Node | Purpose |
|------|---------|
| **Google Drive Trigger** | Detects new files in a specific Drive folder |
| **Download File** | Fetches the uploaded document |
| **Default Data Loader** | Loads PDF/text into a unified format |
| **Character Text Splitter** | Splits content into chunks |
| **OpenAI Embeddings** | Generates vector embeddings |
| **Pinecone Vector Store** | Stores vectors in Pinecone |
| **Chat Trigger** | Starts a user chat session |
| **OpenAI Chat Model** | Generates responses for Q&A |
| **AI Agent (LangChain)** | Coordinates retrieval + reasoning |
| **Pinecone Tool** | Retrieves relevant text from Pinecone |

---

## 🛠 Technologies Used

- **n8n**  
- **Google Drive API**  
- **OpenAI API** (GPT + Embeddings)  
- **LangChain** (Document Loader, Splitter, Agent)  
- **Pinecone** vector database  

---

## 🧪 How to Use

1. Import `workflow.json` into your n8n instance  
2. Set up credentials:
   - Google Drive OAuth  
   - OpenAI API  
   - Pinecone API  
3. Update:
   - Pinecone index name  
   - Namespace (optional)
   - Folder ID (optional)  
4. Upload a document to the monitored Google Drive folder  
5. Ask questions using the Chat Trigger (if enabled)

---

## 🔒 Security Notice

This workflow JSON does **not** contain:
- API keys  
- OAuth tokens  
- Google Drive permissions  
- Pinecone secret keys  
- n8n credential files  

All sensitive credentials remain securely stored inside n8n.

---


## 🖼 Workflow Screenshot

![Workflow Screenshot](./workflow.png)


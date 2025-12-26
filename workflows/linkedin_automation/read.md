# 📲 LinkedIn Post Generator + Image Creator (Telegram-Powered Automation)

This workflow is an **AI-driven LinkedIn content creation system** built in n8n.  
It turns a Telegram message into a full, ready-to-publish LinkedIn post **with a matching AI-generated image**, and then emails the final package directly to you.

---

## 🔄 What This Workflow Does

### **1. Triggers from a Telegram message**
Whenever you send a message to your Telegram bot, the workflow begins.

### **2. Runs a Tavily Web Search**
The text you send is used as a query.  
The workflow fetches **8 search results**, each containing content + relevance scores.

### **3. Selects and merges the top results**
A Code node:

- sorts results by score  
- takes the **top 4**  
- merges their content into **one consolidated research chunk**  
- outputs it for downstream AI generation  

This ensures the AI receives a clean, high-signal dataset.

### **4. Generates a LinkedIn post (AI Agent #1)**
A dedicated LangChain Agent:

- receives the merged research  
- writes a **human-sounding, engaging LinkedIn post**  
- returns structured JSON:  
  - `title` (headline)  
  - `postContent` (full markdown post)

### **5. Converts the post into a graphic concept (AI Agent #2)**
A second AI Agent reads the LinkedIn post and:

- extracts the key message  
- generates a **professional marketing-style image prompt**  
- describes layout, elements, and style  
- outputs **only** the final prompt  

### **6. Generates an AI image**
Uses OpenAI Images API to produce a **1536×1024 high-quality visual**.

### **7. Converts the base64 output into a binary file**
Prepares the image as a downloadable attachment.

### **8. Emails the final package**
You receive an email containing:

- **Subject:** the LinkedIn post title  
- **Body:** the full markdown LinkedIn post  
- **Attachment:** the generated image  

---

## 🛠 Node Breakdown

| Node | Purpose |
|------|---------|
| **Telegram Trigger** | Starts workflow based on Telegram messages |
| **Tavily HTTP Request** | Performs multi-result web search |
| **Code (Sort + Merge)** | Picks top 4 results and merges content |
| **AI Agent 1** | Creates the detailed LinkedIn post |
| **Structured Output Parser** | Ensures valid JSON output |
| **OpenAI Chat Model** | LLM powering both agents |
| **AI Agent 2** | Turns post into an image prompt |
| **Generate Image** | Creates the AI image (OpenAI API) |
| **Convert to Binary** | Converts base64 → file |
| **Gmail Send** | Emails the final result |

---

## 🎯 Use Cases

- Automated LinkedIn content creation  
- Daily expert-style posts  
- Research-powered insights  
- AI-generated social media visuals  
- Telegram → LinkedIn content pipeline  

---

## 🧪 How to Use

1. Import the workflow into n8n.  
2. Add your credentials:
   - Telegram Bot API  
   - Tavily API  
   - OpenAI API  
   - Gmail OAuth2  
3. Update the Gmail recipient address.  
4. Activate the workflow.  
5. Send any topic to your Telegram bot  
   - “AI in logistics”  
   - “Latest robotics news”  
   - “Explain autonomous agents”  

You’ll receive a **LinkedIn-ready post + AI-generated graphic** directly in your inbox.

---

## 🔒 Security Notice

This workflow export does **not** include:

- API keys  
- Gmail credentials  
- Telegram secrets  
- OpenAI keys  

All sensitive info remains secure inside n8n’s encrypted credential store.

---

## 🖼 Workflow Video

![Workflow Video](./workflow.mp4)
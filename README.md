# Autonomous Multi-Agent Ecosystem (n8n & Multi-Modal RAG)

An enterprise-grade, autonomous multi-agent workspace built using n8n orchestration. The system utilizes a centralized Orchestrator Agent that dynamically evaluates multi-modal inputs (Text, Voice, Images) from WhatsApp and intelligently delegates tasks to specialized sub-agents equipped with Retrieval-Augmented Generation (RAG) and cross-platform communication tools.

---

## 🚀 Key Features

- **Multi-Agent Architecture:** Centralized Orchestrator that parses user intent and routes execution to dedicated sub-agents (Search, Mail, Calendar, Twitter).
- **Multi-Modal Ingestion:** Seamless ingestion of WhatsApp data streams including Text, Voice (Automated Audio Transcription), and Image analysis.
- **High-Precision RAG Pipeline:** Integration of **Pinecone Vector DB** and OpenAI Embeddings, optimized with a **Cohere Reranker** for semantic context retrieval.
- **Automated Workspaces:** Out-of-the-box execution blocks for Gmail (CRUD), Google Calendar scheduling, Google Search live updates, and X/Twitter automated posting.
- **Advanced Context Management:** State retention utilizing memory modules combined with precision prompt engineering for continuous conversational flows.

---

## 🏗️ Architecture Flow

```text
       ┌──────────────────┐
       │  WhatsApp Input  │ (Text, Voice, Image)
       └─────────┬────────┘
                 │
                 ▼
       ┌──────────────────┐
       │   n8n Gateway    │ (Conditional Routing / Switch Nodes)
       └─────────┬────────┘
                 │
                 ▼
    ┌────────────────────────┐
    │   Orchestrator Agent   │ <───> [ Pinecone Vector DB + Cohere Reranker ]
    │     (GPT-4o-mini)      │
    └────┬───┬───┬─────────┬─┘
         │   │   │         │
         │   │   │         └─► 🔎 Web Search Agent (Google, Wikipedia, HackerNews)
         │   │   └───────────► 📧 E-Mail Agent (Gmail CRUD Operations)
         │   └───────────────► 📅 Calendar Agent (Event Management)
         └───────────────────► 🐦 Social Media Agent (X/Twitter Integration)

🛠️ Tech Stack
Orchestration: n8n

LLM Backbone: OpenAI (GPT-4o-mini, Text-Embeddings-3)

Vector Database: Pinecone

Reranking: Cohere Reranker

APIs & Integrations: WhatsApp Business API, Google Workspace APIs (Gmail, Calendar), Twitter v2 API

Scripting & Logic: Node.js / JavaScript

📁 Repository Structure

multi-agent-ecosystem/
│
├── workflows/
│   ├── main_orchestrator.json      # Core n8n workflow definition
│   └── sub_agents_config.json      # Individual sub-agent prompt templates
│
├── scripts/
│   ├── custom_mapping.js           # JavaScript nodes for advanced data manipulation
│   └── audio_processor.py          # Helper for supplementary voice handling (if applicable)
│
├── .env.example                    # Template for required API keys and credentials
└── README.md                       # Project documentation

🔧 Setup & Deployment
Prerequisites
An active n8n instance (Self-hosted or Cloud)

Accounts and API Keys for: OpenAI, Pinecone, Cohere, Google Cloud Console, and Meta Developer (WhatsApp).


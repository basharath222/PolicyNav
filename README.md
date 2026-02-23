# 📜 PolicyNav: AI-Powered Civic Consultant

Target Problem Statement: Developing a user-friendly digital assistant providing legal information in multiple languages to enhance accessibility for marginalized communities.

## 🚀 Overview
PolicyNav is a lightweight, AI-driven platform that simplifies complex government policies and legal documents into actionable, step-by-step roadmaps. Unlike standard chatbots, it uses a Smart Intake Interface to profile user needs and provides structured guidance in vernacular languages (e.g., Tamil).

## ✨ Key Features
♦ Smart Intake Interface: Replaces open-ended chat with structured intent detection and dynamic follow-up forms.

♦ Plain-Language Translator: Converts dense "legalese" and government PDFs into simple, conversational guidance.

♦ Actionable Roadmaps: Generates structured dashboards with mandatory licenses, eligible schemes, and document checklists.

♦ Multi-language Support: Integrated translation (Bhashini/Google) for accessibility in regional languages.

♦ Local-First RAG: Uses a lightweight vector database (ChromaDB) to ensure high accuracy and low latency without expensive cloud overhead.

♦ Document Checklist Generator: Provides a downloadable PDF summary of the exact steps and documents needed.

## 🛠️ The Tech Stack
Language: Python 3.9+

Frontend: Streamlit (For a fast, interactive UI)

Backend: FastAPI (High-performance API handling)

AI Orchestration: LangChain / Gemini 1.5 Flash (via API)

Vector Database: ChromaDB (Local persistent storage)

Data Processing: PyPDF2 / BeautifulSoup (For scraping and indexing policy PDFs)

## 🏗️ Step-by-Step Implementation Guide
#### Phase 1: Knowledge Base Setup
Data Collection: Gather policy PDFs from sources like myScheme.gov.in or TN State Gazettes.

Indexing: Create a script using LangChain to:
♦ Load PDFs.
♦ Split text into 500-character chunks.
♦ Generate embeddings and store them in a Local ChromaDB folder.

### Phase 2: The Logic Engine (FastAPI)
Intent Parser: Create a function that uses Gemini to extract Business Type, Location, and Scale from the user's first input.

RAG Pipeline: Develop a retrieval function that queries ChromaDB for laws matching the user's profile.

Roadmap Generator: Use a structured prompt to force the LLM to output specific sections: Licenses, Schemes, and Documents.

### Phase 3: The UI (Streamlit)
State Management: Use st.session_state to track which step the user is on (Intake -> Form -> Result).

Dynamic Forms: Create a form that only shows questions relevant to the detected intent (e.g., if "Food Stall," ask about "Premises Type").

Dashboard Display: Use st.tabs or st.expander to display the final roadmap categories clearly.

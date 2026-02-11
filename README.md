# RAG Chatbot - Retrieval Augmented Generation System

## Problem Statement

Organizations seeking detailed information about Tata Consultancy Services (TCS), its services, operations, and strategic initiatives often struggle to find accurate, comprehensive answers quickly. Traditional search mechanisms lack the contextual understanding needed to deliver personalized, multi-faceted responses about enterprise IT services, digital transformation, and corporate information.

## Context

This intelligent RAG (Retrieval Augmented Generation) chatbot leverages machine learning, natural language processing, and Generative AI to deliver fast, accurate, and context-aware responses about TCS. The system:

- Implements advanced retrieval mechanisms to access TCS knowledge base
- Uses Generative AI to craft coherent, personalized responses
- Provides deeper insights into TCS services, corporate strategy, and business operations
- Enables informed decision-making through comprehensive information retrieval

## Objective

The RAG chatbot enhances user experience by delivering intelligent, context-aware responses to queries about:

- TCS company overview, history, and global presence
- Service offerings and industry solutions
- Technology platforms and products
- Corporate governance and financial performance
- Career opportunities and employee wellness
- Sustainability and ESG initiatives
- Q&A on frequently asked questions about TCS

## How it Works

The TCS RAG chatbot uses a retrieval-augmented generation pipeline combining document retrieval with generative AI to answer user queries about TCS with accuracy and context.

## Key Components

### 1. Knowledge Base

- **Scraping Module** (`scraping/`): Contains 22 TCS topic documents in .txt format
  - Company overview, global presence, services, products, platforms
  - Career opportunities, governance, sustainability, investor relations
  - Q&A document with 20+ frequently asked questions
- **Document Store** (`static/` & `docs/`): PDF versions of all knowledge base documents
  - 22 TCS topic PDFs + Q&A PDFs in each folder
  - Enriched with theoretical background and practical implications
  - Ready for RAG model ingestion and document retrieval

### 2. Retrieval Mechanism

- FAISS vector index (`faiss/index.faiss`) enables fast similarity-based document retrieval
- When a user submits a query, the system finds relevant documents from the knowledge base
- Retrieved documents provide context for accurate answer generation

### 3. Generative Model

- Uses Generative AI (e.g., LLMs) to craft coherent, context-aware responses
- Synthesizes information from retrieved TCS documents
- Delivers natural, conversational answers tailored to user queries

### 4. Chatbot Pipeline

1. **User Query** → User asks a question about TCS (e.g., "What services does TCS offer?")
2. **Retrieval** → System searches FAISS index for relevant documents
3. **Context Preparation** → Retrieved documents are formatted and passed to the generative model
4. **Response Generation** → Generative AI crafts a comprehensive response based on retrieved context
5. **Delivery** → Response presented to user in conversational format via web interface

## Architecture

![TCS RAG Chatbot Architecture](https://github.com/user-attachments/assets/86f014a1-548f-4ad6-8de5-8e75511e9969)

## Project Structure

```
.
├── app.py                          # Flask application server
├── prompts.py                      # Prompt templates for chat
├── README.md                       # Project documentation
├── templates/                      # HTML templates (Tailwind CSS removed, standard CSS)
│   ├── chat.html                   # Chat interface
│   ├── home.html                   # Landing page
│   ├── index.html                  # Multi-document interface
│   └── pdf.html                    # PDF viewer
├── static/                         # PDF documents (22 TCS PDFs + Q&A)
│   ├── tcs-company-overview.pdf
│   ├── tcs-services-overview.pdf
│   ├── tcs-digital-transformation.pdf
│   ├── tcs-artificial-intelligence.pdf
│   ├── ... (18 additional TCS topic PDFs)
│   ├── TCS_Q&A.pdf                 # Q&A document with 20+ Qs & As
│   └── TCS_QA.pdf             # Alias for TCS_Q&A (backward compatible)
├── docs/                           # Archive of TCS PDFs (same as static/)
│   └── (22 TCS PDFs + Q&A)
├── scraping/                       # Text source documents
│   ├── tcs-company-overview.txt
│   ├── tcs-services-overview.txt
│   ├── ... (19 additional TCS topic documents)
│   ├── tcs-qa.txt                  # Q&A source document
│   ├── pages_name.txt              # URLs for TCS resources
│   └── extract.ipynb               # Jupyter notebook for web scraping
├── faiss/                          # Vector index
│   └── index.faiss                 # FAISS index for document retrieval
├── scripts/                        # Utility scripts
│   ├── recreate_pdfs.py            # Generate PDFs from text sources
│   ├── expand_and_regen_pdfs.py    # Add theoretical content to PDFs
│   └── generate_qa_pdf.py          # Generate Q&A PDFs
└── prompts.py                      # LLM prompt configuration
```
## Usage

### Running the Chatbot

```bash
python app.py
```

The chatbot will start on `http://localhost:5000`

### 22 Topic Documents

1. Company Overview
2. Global Presence & Worldwide Operations
3. Services Overview
4. Consulting Services
5. Products & Platforms
6. Interactive Services (Creative Technology)
7. Manufacturing Solutions
8. CPG & Retail Solutions
9. Employee Wellbeing
10. Corporate Governance
11. Privacy & Compliance
12. Business Strategy
13. Career Opportunities (India)
14. Enterprise Architecture
15. Insights & Thought Leadership
16. Investor Relations
17. Press Releases & Announcements
18. Research Studies
19. Digital Transformation
20. Artificial Intelligence & ML Services
21. Sustainability & ESG
22. Q&A (Frequently Asked Questions)

## Technology Stack

- **Backend**: Flask (Python)
- **Frontend**: HTML + CSS (no framework)
- **Vector Search**: FAISS
- **AI/LLM**: Configurable (supports GPT, Claude, open-source LLMs)
- **Web Scraping**: BeautifulSoup, Requests
- **PDF Generation**: fpdf2

## Features

✓ Web-based chat interface
✓ Multi-document retrieval
✓ PDF viewer integration
✓ Responsive design (mobile/tablet/desktop)
✓ Fast FAISS-based document search
✓ Theoretical background for each topic
✓ Q&A reference document
✓ No external CSS framework dependency


## The current implementation uses a static session
## identifier for maintaining chat history, which is 
## suitable for demonstration purposes. Dynamic session
## handling can be implemented for multi-user production
## environments.”

## Future Enhancements

- Add real-time document updates
- Implement multi-language support
- Enhanced semantic search with embeddings
- Advanced analytics and user feedback
- Document versioning and history

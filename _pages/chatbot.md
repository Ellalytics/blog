---
layout: single
title: "AskElla PDFChatBot V1"
permalink: /portfolio/chatbot/
author_profile: true
---

---

##  Project Overview


Traditional product searches often return irrelevant, keyword-based results. <br>
I build a **Natural Language Interface** that delivers accurate, context-aware answers.
<br>

**AskElla PDFChatBot** is a smart customer service assistant built with **Streamlit**, **LangChain**, **ChromaDB**, **Generative AI.** 
It's designed to answer product-related queries from PDF, combine RAG with modern vector search and LLMs to deliver accurate, context-aware responses. It serves as a template for any domain where structured documents need to be transformed into conversational experiences. Addtionally, I also built [ AskElla PDFChatBot V2](/blog/AI/RAG_2/) which supports more document formats for upload.

---

## High-Level Architecture

```
       ┌───────────────┐
       │   PDF Input   │ 
       └──────┬────────┘
              ↓
 ┌────────────────────────┐
 │ PDF Text Extraction    │◄────────────┐                
 └────────┬───────────────┘             │
          ↓                             │
 ┌──────────────────────────────┐       │
 │ Text Chunking                │       │
 │ (LangChain's RCT Splitter)   │       │
 └────────┬─────────────────────┘       │
          ↓                             │
 ┌──────────────────────────────┐       │
 │ Text Embedding               │       │  
 └────────┬─────────────────────┘       │
          ↓                             │
 ┌─────────────────────────────────────┐│
 │ Vector Storage: ChromaDB            │◄┘
 └─────────────────────────────────────┘
          ▲
          │  Similarity Search
          │  (Top-k chunks)
          │
┌─────────┴──────────────┐
│  Query Embedding       │
│  (User question → vec) │
└─────────┬──────────────┘
          ↓
 ┌──────────────────────────────────────────┐
 │ LangChain + Gemini                       │
 │ Combines query + retrieved chunks        │
 │ Generates context-grounded response      │
 └──────────────┬───────────────────────────┘
                ↓
         ┌───────────────┐
         │ Streamlit UI  │
         │ (Chat window) │
         └───────────────┘

         
```


## Core Components
- **Streamlit Frontend:** Clean and interactive interface for user queries and responses, with assistant info in the sidebar.
- **PDF Processing:** Extracts text page by page, preserving layout for accurate chunking.
- **Chunking with LangChain:** Utilizeed RecursiveCharacterTextSplitter to break down text into overlapping chunks. Balances chunk size for optimal embedding and retrieval.
- **Embeddings with Google:** Converts text chunks into vectors using Google’s embedding model.
- **ChromaDB Vector Store:** Stores and indexes the embeddings with their corresponding text. Enables fast and accurate semantic search during query time.
- **RAG:** Embeds user queries and retrieves top-k relevant chunks.Constructs a context-aware prompt with LangChain. Passes prompt to gemini for grounded response generation.
- **LangChain Orchestration:** Coordinates the full pipeline: from PDF ingestion to chunking, retrieval, and LLM invocation. Uses a predefined prompt template to ensure responses are based strictly on the document.

## Key Advantages

- **Context-Aware**: No hallucination—answers grounded in the PDF only
- **Fast Retrieval**: Embeddings + ChromaDB ensures quick response times
- **Scalable Design**: Easily replace PDF, swap embedding models, or upgrade the LLM

## [Github](https://github.com/Ellalytics/CustomerServiceAssistant)
<img src="/blog/assets/images/askella_1.png" alt="askella chatbot">


## [Github](https://github.com/Ellalytics/ShoeStoreCustomerServiceAssistantMultimodal)
<img src="/blog/assets/images/askella_2.png" alt="askella chatbot">
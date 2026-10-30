# AI-Based RAG PDF Parser | Document Question Answering System

An AI-powered PDF document parser built using **Retrieval-Augmented Generation (RAG)** that allows users to upload PDF documents and ask questions based on their content.

The application extracts text from PDF documents, divides it into smaller chunks, generates vector embeddings, and stores them in a Supabase PostgreSQL database using the pgvector extension.

When a user asks a question, the system retrieves the most relevant document chunks using vector similarity search and provides them as context to an LLM to generate an accurate, context-aware response.

---

## 🚀 Project Overview

Traditional LLM applications generate responses based on their pre-trained knowledge. However, they cannot automatically access private documents or newly uploaded information.

This project solves that problem using **Retrieval-Augmented Generation (RAG)**.

Users can upload PDF documents and interact with them through natural-language questions. Instead of sending the entire PDF to the LLM every time, the application retrieves only the most relevant information from the vector database.

### Key Features

- **PDF Upload and Parsing:** Upload PDF documents and extract their textual content.
- **Text Chunking:** Divide large documents into smaller, manageable chunks.
- **Embedding Generation:** Convert text chunks into numerical vector representations.
- **Vector Storage:** Store embeddings and corresponding text in Supabase PostgreSQL using pgvector.
- **Semantic Search:** Retrieve relevant document chunks based on the meaning of the user's question.
- **AI-Powered Responses:** Generate contextual answers using an LLM.
- **RAG Pipeline:** Combine document retrieval with LLM-based response generation.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Node.js | Backend runtime environment |
| Express.js | REST API development |
| JavaScript | Application logic |
| OpenAI API | Embedding generation and LLM responses |
| Supabase | Database and vector storage |
| PostgreSQL | Relational database |
| pgvector | Vector similarity search |
| PDF Parser | Extracting text from PDF documents |
| REST APIs | Communication between frontend and backend |

---

## 🏗️ System Architecture

The application follows a Retrieval-Augmented Generation architecture consisting of two major pipelines:

### 1. Document Ingestion Pipeline

This pipeline processes uploaded PDF documents and prepares them for semantic search.

1. User uploads a PDF document.
2. Backend receives the document.
3. PDF parser extracts text from the document.
4. Extracted text is divided into smaller chunks.
5. Each chunk is converted into a vector embedding using an embedding model.
6. Embeddings and their corresponding text are stored in Supabase PostgreSQL using pgvector.

### 2. Question Answering Pipeline

This pipeline retrieves relevant information and generates answers.

1. User submits a natural-language question.
2. The question is converted into a vector embedding.
3. Supabase performs similarity search against stored document embeddings.
4. The most relevant document chunks are retrieved.
5. Retrieved chunks are provided as context to the LLM.
6. The LLM generates an answer based on the retrieved information.
7. The answer is returned to the user.

### Architecture Diagram

```text
             USER
               |
               |
        Upload PDF Document
               |
               v
        NODE.JS BACKEND
               |
               v
          PDF PARSER
               |
               v
        TEXT EXTRACTION
               |
               v
          TEXT CHUNKING
               |
               v
       EMBEDDING GENERATION
               |
               v
        SUPABASE DATABASE
          (PostgreSQL)
               |
             pgvector
               |
        Store Embeddings
               |
               |
        USER ASKS QUESTION
               |
               v
        QUESTION EMBEDDING
               |
               v
       VECTOR SIMILARITY SEARCH
               |
               v
       RETRIEVE RELEVANT CHUNKS
               |
               v
          LLM + CONTEXT
               |
               v
        GENERATE ANSWER
               |
               v
          USER RESPONSE
```

---

## 🧠 Understanding RAG

RAG stands for **Retrieval-Augmented Generation**.

It combines two important concepts:

**1. Retrieval**

The system searches an external knowledge source, such as uploaded PDF documents, to find information relevant to a user's question.

**2. Generation**

The retrieved information is passed to a Large Language Model, which generates a natural-language response using that context.

### Why RAG?

- Reduces dependence on the LLM's pre-trained knowledge.
- Allows users to query their own documents.
- Provides context-specific responses.
- Reduces the need to fine-tune an LLM for every new document.
- Helps reduce hallucinations by grounding answers in retrieved information.

---

## 📄 PDF

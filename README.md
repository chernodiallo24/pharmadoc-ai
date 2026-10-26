# PharmaDoc AI
### AI-Powered Pharmaceutical Document Q&A Chatbot

PharmaDoc AI is a Python-based chatbot that allows users to upload pharmaceutical PDF documents and ask questions about their contents. It uses Retrieval-Augmented Generation (RAG) to find relevant information and generate answers with source page references.

I developed this project as part of my AI-powered document insights externship to explore how artificial intelligence can make pharmaceutical document review more efficient.

## Project Overview

Pharmaceutical documents often contain important information such as product expiration dates, lot numbers, quality certifications, and supplier records. Finding these details manually can be time-consuming, particularly when working with scanned documents.

PharmaDoc AI addresses this challenge by combining PDF text extraction, Optical Character Recognition (OCR), semantic search, and a language model into a document question-answering system.

## Key Features

- **PDF Processing:** Extracts text from uploaded pharmaceutical documents.
- **OCR Support:** Uses Tesseract to extract text from scanned PDF pages.
- **Semantic Search:** Finds document passages relevant to the user's question.
- **AI-Generated Answers:** Uses Qwen to generate responses based on retrieved information.
- **Source References:** Displays retrieved document pages for verification.
- **Interactive Interface:** Provides a Gradio chatbot for uploading documents and asking questions.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| PyMuPDF | PDF text extraction |
| Tesseract OCR | Scanned document processing |
| LangChain | Text chunking |
| BGE-small-en-v1.5 | Text embeddings |
| FAISS | Vector similarity search |
| Qwen 2.5 1.5B Instruct | Answer generation |
| Gradio | User interface |
| Google Colab | Development environment |

## How It Works

1. The user uploads a pharmaceutical PDF.
2. The system extracts text using PyMuPDF or OCR when needed.
3. The extracted text is divided into smaller chunks.
4. BGE converts the chunks into numerical embeddings.
5. FAISS retrieves the three most relevant chunks for the user's question.
6. Qwen uses the retrieved information to generate an answer.
7. The chatbot displays the answer and retrieved source pages.

This approach is known as Retrieval-Augmented Generation (RAG), which helps ground the model's responses in the uploaded document.

## Evaluation Results

I evaluated the system using ten questions based on a ten-page sample pharmaceutical PDF.

| Metric | Result |
|---|---|
| Answer Accuracy | 80% (8/10 correct) |
| Page-Based Recall@3 | 100% |
| Page-Based Precision@3 | 50% |
| Page-Based MRR | 0.90 |
| PDF Processing Time | 0.161 seconds |
| Full RAG Response Time | 2.832 seconds |

*Processing and response times reflect individual tests, not averages. Retrieval metrics were evaluated using expected source pages rather than independently verified answer-containing passages.*

### Example Question

**Question:** What is the expiration date of the AKTA ready High Flow Kit?

**Chatbot Answer:** July 12, 2021.

The chatbot correctly identified the expiration date and displayed the retrieved source pages.

## Limitations and Future Improvements

Although the system achieved encouraging results, testing revealed several limitations.

For example, the chatbot sometimes confused part numbers with lot numbers. In another test, it retrieved the correct source page for an operating pressure question but failed to generate the correct answer.

Potential improvements include:

- Adding field validation for lot numbers, expiration dates, and other structured information.
- Implementing reranking to improve the relevance of retrieved passages.
- Improving extraction from complex tables and scanned documents.
- Supporting questions across multiple uploaded PDFs.
- Expanding testing to larger and more varied document collections.

## What I Learned

This project gave me hands-on experience with Python, OCR, semantic search, vector databases, language models, and RAG pipelines.

It also reinforced the importance of evaluating AI-generated answers rather than assuming that retrieving relevant information guarantees an accurate response.

## Project Status

Completed capstone prototype. Further accuracy improvements and expanded testing are planned.

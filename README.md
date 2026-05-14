# Legal AI — Grounded Legal Draft Generation with Self-Improving Rules

An AI-powered legal drafting system that transforms messy legal documents into grounded, structured legal drafts while continuously improving through operator feedback.

This project processes scanned PDFs, OCR-heavy documents, handwritten letters, and text files, retrieves relevant legal context using hybrid search, and generates citation-backed legal drafts using Anthropic Claude. It also learns reusable drafting rules from human edits and applies them automatically in future generations.

---

## 🚀 Features

### 📄 Intelligent Document Processing
- Extracts text from PDFs using `pdfplumber`
- OCR fallback support via `Tesseract` for scanned documents
- Cleans OCR artifacts and formatting noise automatically

### 🧠 Structured Legal Information Extraction
Uses Claude to identify and extract:
- Case numbers
- Parties and attorneys
- Dates and jurisdictions
- Legal issues and claims
- Other key metadata

### 🔍 Hybrid Retrieval System
Combines:
- Semantic search using `Sentence Transformers`
- Vector storage with `ChromaDB`
- Keyword overlap scoring

This improves grounding accuracy and retrieval relevance.

### ✍️ Grounded Draft Generation
Claude generates legal draft sections using only retrieved evidence.

Key capabilities:
- Inline chunk citations
- Hallucination-resistant prompting
- Evidence-grounded reasoning
- Structured legal drafting workflows

### 🔁 Self-Improving Rule Engine
When operators edit generated drafts:
1. Original and revised text are compared
2. Claude extracts a generalized drafting instruction
3. Rules are stored and reinforced over time
4. Future drafts automatically apply learned rules

### 📊 Evaluation & Quality Metrics
Built-in evaluation metrics include:
- Precision@1
- Citation coverage
- Rule application tracking
- Hallucination detection flags

---

# 🏗️ Architecture Overview

```text
Input Documents (PDF / TXT)
        │
        ▼
Text Extraction & OCR Cleaning
        │
        ▼
Chunking (350 words, 60 overlap)
        │
        ▼
Vector Indexing (ChromaDB + MiniLM Embeddings)
        │
        ▼
Hybrid Retrieval
(Semantic + Keyword Search)
        │
        ▼
Top Relevant Chunks
        │
        ▼
Claude Draft Generation
(Grounded + Citation-Based)
        │
        ▼
Operator Review & Edits
        │
        ▼
Rule Extraction & Deduplication
        │
        ▼
Reusable Drafting Rules Database
        │
        ▼
Improved Future Drafts

git clone https://github.com/dfaysalamin/legal-ai-drafting.git
cd legal-ai-drafting

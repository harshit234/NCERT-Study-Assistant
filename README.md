# NCERT Study Assistant (Retrieval-Ready RAG System)

## Project Overview

This project builds a **retrieval-ready study assistant** for NCERT Class 9 Science chapters.
The system extracts textbook content, structures it into meaningful units, retrieves relevant information using BM25, and prepares for grounded answer generation using LLMs.

The goal is to ensure that answers are **strictly based on textbook content**, avoiding hallucinations and maintaining trust.

---

## Key Features

* PDF Text Extraction (PyMuPDF)
* Data Cleaning & Noise Removal
* Content Structuring:

  * Concepts
  * Examples
  * Activities
  * Questions
* ✂️ Intelligent Chunking with Metadata
* 🔍 BM25-based Retrieval System
* ⚙️ Ready for Grounded LLM Integration

---

## Project Structure

```
NCERT-Study-Assistant/
│
├── notebook.ipynb        # Main pipeline (runs end-to-end)
├── main.py               # Supporting script (optional)
├── README.md             # Project documentation
│
├── extracted/            # Extracted raw text
├── chunks/               # Processed chunks
├── retrieval/            # BM25 logic
├── generation/           # LLM integration (Stage 3)
├── evaluation/           # Evaluation outputs
```

---

## Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/your-username/NCERT-Study-Assistant.git
cd NCERT-Study-Assistant
```

---

### 2. Create Virtual Environment

```bash
python -m venv venv
venv\Scripts\activate   # Windows
```

---

### 3. Install Dependencies

```bash
pip install pymupdf transformers torch rank_bm25 numpy pandas scikit-learn google-generativeai
```

---

### 4. Add NCERT PDF

Download from:
https://ncert.nic.in/textbook.php?iesc1=0-11

---

## How to Run

Open:

```
notebook.ipynb
```


### Pipeline:

1. PDF Extraction
2. Text Cleaning
3. Structure Detection
4. Chunk Creation
5. BM25 Retrieval

---

## Retrieval Example

```python
search("What is work?")
```

Output:

* Top relevant chunks
* Section + type metadata

---

## Chunking Strategy

* Structure-based chunking (concepts, examples, activities)
* Chunk size: ~200–500 tokens equivalent
* Sentence-level splitting for large blocks
* Metadata included:

  * Section
  * Content type
* Small overlap used to preserve boundary context

---

## Tokenizer Comparison

Compared:

* GPT-2 (BPE)
* BERT (WordPiece)
* T5 (SentencePiece)

Key observations:

* Different token counts for same text
* Different subword splitting behavior
* Impacts chunk size decisions


## Challenges Faced

* Noisy PDF extraction (headers, page numbers)
* Broken words (e.g., ORK, NERGY)
* Incorrect structure detection
* Chunk boundary issues

---

## Key Learnings

* Data quality impacts system more than model choice
* Chunking is critical for retrieval performance
* BM25 works effectively for textbook-based QA
* Most hallucinations come from wrong retrieval

---

## Future Improvements

* LLM-based grounded answer generation
* Evaluation pipeline (15–20 questions)
* Dense retrieval (embeddings)
* Guardrails for out-of-scope queries

---


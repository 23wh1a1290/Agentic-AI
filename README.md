# 🎓 Educational AI Content Generator using RAG

An AI-powered educational content generation system that creates personalized lessons, quizzes, and topic explanations using Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG).

The application allows students to upload PDF textbooks or study materials and generate educational content based on the information retrieved from those documents.

## 🚀 Project Overview

The Educational AI Content Generator uses AI to simplify learning by generating grade-specific educational materials.

Students can:
- Upload PDF textbooks and study notes.
- Enter a topic and select their grade level.
- Choose a difficulty level: Easy, Medium, or Hard.
- Generate lesson notes, multiple-choice quizzes, or topic explanations.
- Receive content grounded in uploaded study materials through RAG.

## ✨ Features

### 1. PDF Upload and Processing
- Upload educational PDF documents.
- Extract text using PyMuPDF.
- Divide extracted text into smaller chunks.
- Process documents for semantic retrieval.

### 2. Embedding Generation
- Uses Sentence Transformers.
- Embedding model: `all-MiniLM-L6-v2`.
- Converts text chunks into numerical vector representations.

### 3. Vector Database
- Uses FAISS for vector indexing and similarity search.
- Stores document embeddings.
- Retrieves the most relevant text chunks based on student queries.

### 4. AI-Powered Content Generation

The application supports three content generation modes:

**Lesson Mode**
- Lesson title
- Learning objectives
- Detailed concept explanation
- Important concepts
- Worked examples
- Summary

**Quiz Mode**
- Generates 10 multiple-choice questions.
- Provides four options per question.
- Generates a separate answer key.

**Explanation Mode**
- Provides clear topic explanations.
- Explains important concepts.
- Includes relevant examples.

### 5. Retrieval-Augmented Generation (RAG)
- Retrieves relevant information from uploaded PDFs.
- Passes retrieved context to the Groq LLM.
- Generates context-aware educational content.
- Uses general knowledge when relevant PDF context is unavailable.

### 6. Interactive User Interface
- Built using Gradio.
- Supports PDF uploads.
- Provides topic, grade, difficulty, and content-type selection.
- Displays generated educational content.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend development |
| Groq API | LLM integration |
| GPT-OSS 20B | Educational content generation |
| Sentence Transformers | Text embeddings |
| all-MiniLM-L6-v2 | Embedding model |
| FAISS | Vector database and similarity search |
| PyMuPDF | PDF text extraction |
| Gradio | Frontend interface |
| Google Colab | Development environment |

## 🏗️ System Architecture

```text
             Student
                |
                v
          Gradio Interface
                |
        Upload PDF / Enter Topic
                |
                v
          PDF Processing
                |
          Text Extraction
                |
            Chunking
                |
                v
       Sentence Transformers
         Embedding Generation
                |
                v
          FAISS Vector DB
                |
          Similarity Search
                |
          Retrieve Top-K Chunks
                |
                v
          Retrieved Context
                |
                v
             Groq LLM
                |
        Prompt Engineering
                |
                v
       Educational AI Agent
                |
        +-------+--------+
        |       |        |
      Lesson   Quiz  Explanation
        |       |        |
        +-------+--------+
                |
                v
          Generated Output
```

## ⚙️ Installation and Setup

### Step 1: Clone the repository

```bash
git clone https://github.com/your-username/your-repository.git

cd your-repository
```

### Step 2: Install dependencies

```bash
pip install groq gradio sentence-transformers faiss-cpu pymupdf numpy
```

### Step 3: Configure Groq API Key

Obtain an API key from:

https://console.groq.com/keys

For Google Colab, add your API key under Secrets with the name `Groq`.

Access it securely:

```python
from google.colab import userdata
from groq import Groq

groq_key = userdata.get("Groq")

client = Groq(api_key=groq_key)
```

### Step 4: Load the embedding model

```python
from sentence_transformers import SentenceTransformer

embedding_model = SentenceTransformer(
    "sentence-transformers/all-MiniLM-L6-v2"
)
```

### Step 5: Run the application

Execute the notebook cells in order and launch the Gradio interface.

## 🧪 Example Usage

| Input | Example |
|---|---|
| Topic | Computer Networks |
| Grade | 12 |
| Difficulty | Medium |
| Content Type | Quiz |
| Uploaded PDF | Computer Networks Notes |

**Expected Result:** The system retrieves relevant information from the uploaded notes and generates multiple-choice questions with an answer key.

## 🔍 How RAG Works in This Project

The project follows a Retrieval-Augmented Generation workflow:

1. **Document Loading:** Students upload PDF study materials.
2. **Text Extraction:** PyMuPDF extracts readable text.
3. **Chunking:** Extracted text is divided into smaller overlapping chunks.
4. **Embedding Generation:** Sentence Transformers converts chunks into numerical vectors.
5. **Vector Storage:** FAISS stores the generated embeddings.
6. **Retrieval:** Student queries are converted into embeddings and compared against stored vectors.
7. **Context Generation:** The most relevant chunks are retrieved.
8. **Response Generation:** Retrieved context is passed to the Groq LLM to generate educational content.

## 📌 Future Enhancements

- Support for multiple PDF uploads.
- OCR support for scanned and handwritten notes.
- Download generated lessons and quizzes as PDF.
- Student answer evaluation and personalized feedback.
- Chat-based question answering from uploaded textbooks.
- Persistent vector database storage.
- Source citations with page numbers.
- Support for multilingual educational content.

## 🎯 Project Objective

The main objective is to make learning more personalized and accessible by combining Large Language Models, semantic search, embeddings, and Retrieval-Augmented Generation to generate educational content based on student requirements and uploaded study materials.

## 👩‍💻 Development Environment

- Google Colab
- Python 3
- Groq API
- Gradio

---

**Project:** Educational AI Content Generator using Retrieval-Augmented Generation (RAG)

**Domain:** Artificial Intelligence | Generative AI | Natural Language Processing

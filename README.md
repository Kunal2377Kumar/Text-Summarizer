# Text-Summarizer
#  AI Text Summarizer

> **An intelligent, fast, and professional web application that transforms long-form text into concise, meaningful summaries using a fine-tuned T5 Transformer model.**

---

##  Project Overview

**AI Text Summarizer** is a full-stack Natural Language Processing application built with **FastAPI**, **Hugging Face Transformers**, and a clean web interface.

Users can simply paste their content into the application, click **Summarize**, and receive an AI-generated summary within seconds.

The project demonstrates how modern Transformer-based NLP models can be integrated into a lightweight production-style web application.

---

# Project Architecture

```text
                    ┌──────────────────────────┐
                    │         USER             │
                    │                          │
                    │  Paste / Enter Text      │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │       WEB INTERFACE      │
                    │        index.html        │
                    │                          │
                    │      Text Input          │
                    │      Summarize Button    │
                    └────────────┬─────────────┘
                                 │
                                 │ POST /summarize/
                                 ▼
                    ┌──────────────────────────┐
                    │       FASTAPI API        │
                    │                          │
                    │  Input Validation        │
                    │  Request Processing      │
                    └────────────┬─────────────┘
                                 │
                                 ▼
              ┌──────────────────────────────────┐
              │       TEXT PREPROCESSING         │
              │                                  │
              │  ✓ Remove line breaks            │
              │  ✓ Remove extra spaces           │
              │  ✓ Remove HTML tags              │
              │  ✓ Normalize text                │
              └────────────────┬─────────────────┘
                               │
                               ▼
              ┌──────────────────────────────────┐
              │      T5 TRANSFORMER MODEL        │
              │                                  │
              │   Tokenization                   │
              │          ↓                       │
              │   Neural Text Generation         │
              │          ↓                       │
              │   Beam Search                    │
              └────────────────┬─────────────────┘
                               │
                               ▼
                    ┌──────────────────────────┐
                    │     GENERATED SUMMARY    │
                    │                          │
                    │   Concise AI Output      │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │         USER             │
                    │                          │
                    │   📄 Summary Displayed   │
                    └──────────────────────────┘
```

---

# 🚀 Key Features

| Feature                 | Description                                                    |
| ----------------------- | -------------------------------------------------------------- |
| 🤖 AI-Powered           | Uses a T5 Transformer model for abstractive text summarization |
| ⚡ FastAPI Backend       | Lightweight and high-performance API architecture              |
| 🧠 Smart Preprocessing  | Removes unnecessary spaces, line breaks, and HTML tags         |
| 💻 Clean Web Interface  | Simple interface for entering and summarizing text             |
| 🔄 REST API             | Dedicated `/summarize/` endpoint                               |
| 🖥️ Device Optimization | Automatically supports Apple MPS, NVIDIA CUDA, and CPU         |
| 🎯 Beam Search          | Uses multiple beams to improve summary generation              |
| 🔒 Input Validation     | Uses Pydantic models for structured request validation         |

---

# 🛠️ Technology Stack

```text
┌───────────────────────────────────────────────────────┐
│                   TECHNOLOGY STACK                    │
├───────────────────────┬───────────────────────────────┤
│ Backend               │ FastAPI                       │
│ Programming Language  │ Python                        │
│ AI Framework          │ PyTorch                       │
│ NLP Framework         │ Hugging Face Transformers     │
│ AI Model              │ T5                            │
│ Data Validation       │ Pydantic                      │
│ Frontend              │ HTML, CSS, JavaScript         │
│ API Communication     │ Fetch API / JSON              │
└───────────────────────┴───────────────────────────────┘
```

---

# 📂 Project Structure

```text
AI-Text-Summarizer/
│
├── app.py
│   ├── FastAPI application
│   ├── T5 model loading
│   ├── Text preprocessing
│   ├── Summarization logic
│   └── API endpoints
│
├── index.html
│   ├── User interface
│   ├── Text input area
│   ├── Summarize button
│   └── Summary output section
│
├── saved_summary_model/
│   ├── Model weights
│   ├── Tokenizer files
│   └── Configuration files
│
├── requirements.txt
│
└── README.md
```

---

# ⚙️ How It Works

## 1️⃣ User Enters Text

The user writes or pastes content into the application's text area.

```text
┌─────────────────────────────────────────────┐
│                                             │
│  Enter your long text or dialogue here...   │
│                                             │
│                                             │
└─────────────────────────────────────────────┘

                 [ SUMMARIZE ]
```

⬇️

## 2️⃣ Frontend Sends Request

The browser sends the user's text to the FastAPI backend.

```text
POST /summarize/

{
    "dialogue": "Your text goes here..."
}
```

⬇️

## 3️⃣ Text Cleaning

Before summarization, the application processes the text.

```text
Raw Text
    │
    ▼
Remove Line Breaks
    │
    ▼
Remove Extra Spaces
    │
    ▼
Remove HTML Tags
    │
    ▼
Normalize Text
    │
    ▼
Clean Input
```

⬇️

## 4️⃣ AI Model Generates Summary

The cleaned text is tokenized and passed to the T5 Transformer model.

```text
Input Text
    │
    ▼
┌───────────────┐
│   Tokenizer   │
└───────┬───────┘
        │
        ▼
┌───────────────┐
│   T5 Model    │
│               │
│ Beam Search   │
└───────┬───────┘
        │
        ▼
Generated Tokens
        │
        ▼
┌───────────────┐
│    Decoder    │
└───────┬───────┘
        │
        ▼
Final Summary
```

⬇️

## 5️⃣ Summary Is Returned

The backend returns a JSON response.

```json
{
    "summary": "This is the AI-generated summary."
}
```

The frontend then displays the generated summary to the user.

---

# 🧠 Model Configuration

The application uses a T5 sequence-to-sequence architecture.

```text
                    ┌─────────────────┐
                    │   INPUT TEXT    │
                    └────────┬────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │   TOKENIZATION      │
                  │                     │
                  │ Max Input: 512      │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │      T5 MODEL       │
                  │                     │
                  │ Encoder → Decoder   │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │   BEAM SEARCH       │
                  │                     │
                  │ Number of Beams: 4  │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │   FINAL SUMMARY     │
                  │                     │
                  │ Max Length: 51      │
                  └─────────────────────┘
```

---

# 💻 Installation

## Clone the Repository

```bash
git clone <your-repository-url>
cd AI-Text-Summarizer
```

## Create a Virtual Environment

```bash
python -m venv venv
```

### Windows

```bash
venv\Scripts\activate
```

### macOS / Linux

```bash
source venv/bin/activate
```

## Install Dependencies

```bash
pip install fastapi
pip install uvicorn
pip install torch
pip install transformers
pip install sentencepiece
```

Or use:

```bash
pip install -r requirements.txt
```

---

# ▶️ Run the Application

Start the FastAPI server:

```bash
uvicorn app:app --reload
```

Then open:

```text
http://127.0.0.1:8000
```

---

# 🔌 API Documentation

FastAPI automatically provides interactive API documentation.

```text
Swagger UI
```

```text
http://127.0.0.1:8000/docs
```

---

# 📡 API Endpoint

## Summarize Text

```text
POST /summarize/
```

### Request

```json
{
    "dialogue": "Artificial Intelligence is transforming the way people work, learn, and communicate..."
}
```

### Response

```json
{
    "summary": "Artificial Intelligence is transforming work, learning, and communication."
}
```

---

# 🖥️ Device Support

The application automatically selects the best available processing device.

```text
                ┌───────────────────────┐
                │    START APPLICATION  │
                └───────────┬───────────┘
                            │
                            ▼
                  Is Apple MPS Available?
                       /          \
                     YES          NO
                      │            │
                      ▼            ▼
                   MPS Device   Is CUDA Available?
                                  /          \
                                YES          NO
                                 │            │
                                 ▼            ▼
                              CUDA GPU       CPU
```

This allows the application to take advantage of available hardware acceleration.

---

# 🎯 Example Workflow

```text
┌─────────────────────────────────────────────┐
│                 INPUT                       │
│                                             │
│  Long Article / Conversation / Document     │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
             AI SUMMARIZATION
                       │
                       ▼
┌─────────────────────────────────────────────┐
│                 OUTPUT                      │
│                                             │
│       Short, Meaningful Summary             │
└─────────────────────────────────────────────┘
```

---

# 🔮 Future Improvements

The following features can make the project more powerful:

* 📄 PDF and document upload support
* 📊 Summary length selection
* 🌐 Multilingual summarization
* 📋 Copy summary button
* ⬇️ Download summary as TXT or PDF
* 🕘 Summary history
* 👤 User authentication
* ☁️ Cloud deployment
* 📈 Analytics dashboard
* 🔗 Social-media content summarization

---

# 👨‍💻 Application Flow

```text
        USER
          │
          ▼
   ┌─────────────┐
   │  index.html │
   └──────┬──────┘
          │
          │ JavaScript Fetch API
          ▼
   ┌──────────────────┐
   │  FastAPI Server  │
   │                  │
   │ /summarize/      │
   └────────┬─────────┘
            │
            ▼
   ┌──────────────────┐
   │ Text Cleaning    │
   └────────┬─────────┘
            │
            ▼
   ┌──────────────────┐
   │ T5 Transformer   │
   │                  │
   │ Hugging Face     │
   └────────┬─────────┘
            │
            ▼
   ┌──────────────────┐
   │ Generated Summary│
   └────────┬─────────┘
            │
            ▼
          USER
```

---

# 📈 Project Highlights

> **Input → Clean → Tokenize → Generate → Decode → Summarize**

This project combines a modern **Transformer-based NLP model** with a lightweight **FastAPI backend** and an interactive **web interface**.

It demonstrates the complete machine-learning application workflow:

```text
┌──────────────┐
│ USER INPUT   │
└──────┬───────┘
       ▼
┌──────────────┐
│ PREPROCESS   │
└──────┬───────┘
       ▼
┌──────────────┐
│ TOKENIZATION │
└──────┬───────┘
       ▼
┌──────────────┐
│ AI MODEL     │
└──────┬───────┘
       ▼
┌──────────────┐
│ TEXT OUTPUT  │
└──────────────┘
```

---




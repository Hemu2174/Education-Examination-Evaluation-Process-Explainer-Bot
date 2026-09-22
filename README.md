# 🎓 Education Examination & Evaluation Process Explainer Bot

> An intelligent AI-powered chatbot that helps students understand academic examination and evaluation processes using institutional documents.

[![Streamlit](https://img.shields.io/badge/Streamlit-1.40.1-FF4B4B?style=flat&logo=streamlit)](https://streamlit.io)
[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat&logo=python)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

 
**Institution:** AITAM (Aditya Institute of Technology and Management)  
**Team:** Error Squad  
**Academic Year:** 2025-2026 (6th Semester)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [Deployment](#deployment)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [Developer](#developer)
- [License](#license)

---

## 🎯 Overview

The Education Examination & Evaluation Process Explainer Bot is a RAG (Retrieval-Augmented Generation) based chatbot designed to help students understand complex examination and evaluation processes. By uploading institutional PDF documents, students can ask questions and receive accurate, document-grounded answers about:

- Examination patterns and schedules
- Grading systems (CGPA, GPA, letter grades)
- Revaluation and recounting processes
- Supplementary and improvement examinations
- Attendance rules and eligibility criteria
- Hall ticket and registration procedures
- Result publication and transcript processes

### 🎯 Key Highlights

- **Document-Grounded Responses**: Answers are strictly based on uploaded documents
- **No Hallucinations**: Built-in guardrails prevent AI from making up information
- **Student-Friendly**: Simple, clear explanations with examples
- **Multi-Document Support**: Process multiple PDFs simultaneously
- **OCR Support**: Handles scanned/image-based PDFs
- **Voice Input/Output**: Ask questions by voice, hear answers read aloud
- **Real-Time Progress**: Visual feedback during document processing

---

## ✨ Features

### Core Features

| Feature | Description |
|---------|-------------|
| 📄 **PDF Upload** | Upload multiple exam regulation PDFs at once |
| 🔨 **Knowledge Base Building** | Automatic text extraction, chunking, and vectorization |
| 💬 **Intelligent Q&A** | Ask questions in natural language, get accurate answers |
| 🧠 **RAG Pipeline** | FAISS vector search + Groq LLM for grounded responses |
| 📊 **Progress Tracking** | Real-time progress bar during KB building |
| 🎙️ **Voice Input** | Speak your questions using Groq Whisper API |
| 🔊 **Voice Output** | Hear answers read aloud using gTTS |
| 🤖 **Model Selection** | Choose from multiple AI models (Llama, Mixtral, Gemma) |
| ⚙️ **Customizable Settings** | Adjust temperature, top-p, max tokens, retrieval chunks |
| 📱 **Responsive Design** | Works on desktop, tablet, and mobile devices |

### Advanced Features

- **Smart File Detection**: Only rebuilds KB when new files are uploaded
- **Error Recovery**: Graceful error handling with detailed messages
- **File Size Warnings**: Alerts for large files (>50MB)
- **OCR Fallback**: Automatically uses OCR for scanned PDFs
- **Chat History**: Maintains conversation context
- **Persistent Storage**: Saves KB to disk for quick reloading
- **Academic Integrity**: Built-in guardrails against misuse

---

## 🛠️ Tech Stack

### Frontend
- **Streamlit 1.40.1** - Web application framework
- **HTML/CSS** - Custom styling and UI components

### Backend & AI
- **Groq API** - LLM inference (Llama 3.3 70B, Mixtral, Gemma2)
- **LangChain** - RAG framework and text processing
- **FAISS** - Vector database for semantic search
- **HuggingFace Transformers** - Embedding models

### Document Processing
- **PyPDF2** - PDF text extraction
- **pdf2image + Tesseract** - OCR for scanned PDFs
- **LangChain Text Splitters** - Intelligent text chunking

### Voice I/O
- **Groq Whisper API** - Fast speech-to-text transcription
- **gTTS** - Text-to-speech synthesis
- **SpeechRecognition** - Fallback STT

### ML & Data Science
- **PyTorch** - Deep learning framework
- **sentence-transformers** - Semantic embeddings
- **NumPy, Pandas** - Data manipulation
- **scikit-learn** - ML utilities

---

## 📦 Installation

### Prerequisites

- Python 3.11 or higher
- pip (Python package manager)
- Git
- Groq API key (free at [console.groq.com](https://console.groq.com))

### Step 1: Clone Repository

```bash
git clone https://github.com/malipeddisekhar/Education-Examination-Evaluation-Process-Explainer-Bot.git
cd Education-Examination-Evaluation-Process-Explainer-Bot
```

### Step 2: Create Virtual Environment

```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS/Linux
python3 -m venv .venv
source .venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables

```bash
# Copy example file
cp .env.example .env

# Edit .env and add your Groq API key
# GROQ_API_KEY=your_actual_api_key_here
```

### Step 5: Run Application

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`

---

## 🚀 Usage

### Quick Start Guide

1. **Upload Documents**
   - Open the sidebar (left panel)
   - Click "Browse files"
   - Select your exam regulation PDFs
   - Files upload instantly

2. **Build Knowledge Base**
   - Click "🔨 Build KB" button
   - Watch the progress bar:
     - 20%: Extracting text from PDFs
     - 40%: Splitting text into chunks
     - 60%: Creating embeddings
     - 80%: Saving knowledge base
     - 100%: Complete!

3. **Ask Questions**
   - Type your question in the chat input
   - Or click the microphone icon to speak
   - Press Enter
   - Get instant, accurate answers!

### Example Questions

```
"How does the grading system work?"
"What is the revaluation process?"
"What are the attendance requirements for eligibility?"
"How do supplementary exams work?"
"What is the CGPA calculation method?"
"When are the exam results published?"
```

### Tips for Best Results

- **Be Specific**: Ask clear, focused questions
- **Use Keywords**: Include terms from your documents
- **Check Context**: Ensure your question relates to uploaded documents
- **Adjust Settings**: Lower temperature (0.0-0.3) for factual answers
- **Multiple Documents**: Upload all relevant PDFs together

---

## 🌐 Deployment

### Deploy to Render (Recommended)

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Create Render Web Service**
   - Go to [render.com/dashboard](https://render.com/dashboard)
   - Click "New +" → "Web Service"
   - Connect your GitHub repository

3. **Configure Service**
   ```
   Name: education-explainer-bot
   Environment: Python 3
   Build Command: pip install --upgrade pip && pip install -r requirements.txt
   Start Command: streamlit run app.py --server.port=$PORT --server.address=0.0.0.0 --server.headless=true
   ```

4. **Add Environment Variable**
   ```
   Key: GROQ_API_KEY
   Value: [Your Groq API key]
   ```

5. **Deploy**
   - Click "Create Web Service"
   - Wait 5-10 minutes
   - Your app is live!

### Deploy to Streamlit Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io)
2. Click "New app"
3. Select your repository
4. Add secrets:
   ```toml
   GROQ_API_KEY = "your_key_here"
   ```
5. Click "Deploy!"

---

## 📁 Project Structure

```
Education-Examination-Evaluation-Process-Explainer-Bot/
│
├── app.py                      # Main application (846 lines)
├── htmlTemplates.py            # CSS and HTML templates
├── requirements.txt            # Python dependencies
├── runtime.txt                 # Python version specification
├── Procfile                    # Deployment configuration
├── render.yaml                 # Render deployment config
├── Aptfile                     # System dependencies
├── packages.txt                # Alternative system dependencies
│
├── .streamlit/
│   ├── config.toml            # Streamlit configuration
│   └── secrets.toml.example   # Secrets template
│
├── .env.example               # Environment variables template
├── .gitignore                 # Git ignore rules
├── .python-version            # Python version
│
├── docs/
│   ├── ARCHITECTURE.md        # System architecture
│   └── SETUP.md              # Detailed setup guide
│
├── faiss_knowledge_base/      # Generated at runtime
│   ├── index.faiss           # Vector index
│   └── index.pkl             # Metadata
│
└── README.md                  # This file
```

---

## ⚙️ Configuration

### Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GROQ_API_KEY` | Yes | Your Groq API key from console.groq.com |
| `PYTHONUNBUFFERED` | No | Set to `true` for better logging |

### Streamlit Configuration

Edit `.streamlit/config.toml`:

```toml
[server]
maxUploadSize = 200          # Max file size in MB
headless = true              # Run without browser
enableXsrfProtection = true  # Security

[theme]
primaryColor = "#FF6B6B"     # Accent color
backgroundColor = "#0E1117"   # Dark background
```

### Model Configuration

Available models in `app.py`:

```python
AVAILABLE_MODELS = {
    "Llama 3.3 70B": "llama-3.3-70b-versatile",      # Best quality
    "Llama 3.1 8B (Fast)": "llama-3.1-8b-instant",   # Fastest
    "Mixtral 8x7B": "mixtral-8x7b-32768",            # Long context
    "Gemma2 9B": "gemma2-9b-it",                     # Lightweight
}
```

### RAG Configuration

Adjust in `app.py`:

```python
CHUNK_SIZE = 500              # Characters per chunk
CHUNK_OVERLAP = 50            # Overlap between chunks
RETRIEVAL_TOP_K = 2           # Chunks to retrieve
DEFAULT_TEMPERATURE = 0.0     # LLM temperature
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 style guide
- Add docstrings to functions
- Test thoroughly before submitting
- Update README if needed

---

## 👨‍💻 Developer

<div align="center">

### **Malipeddi Sekhar**

**B.Tech Student | AI/ML Enthusiast | Full-Stack Developer**

📍 Aditya Institute of Technology and Management (AITAM)  
🎓 6th Semester, Academic Year 2025-2026  
👥 Team: Error Squad

[![GitHub](https://img.shields.io/badge/GitHub-malipeddisekhar-181717?style=flat&logo=github)](https://github.com/malipeddisekhar)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat&logo=linkedin)](https://linkedin.com/in/malipeddisekhar)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=flat&logo=gmail)](mailto:malipeddisekhar@gmail.com)

</div>

### About the Developer

Malipeddi Sekhar is a passionate B.Tech student specializing in Artificial Intelligence and Machine Learning. With a strong foundation in full-stack development and a keen interest in building practical AI solutions, Sekhar developed this chatbot as part of his academic project to help students better understand examination processes.

**Skills & Expertise:**
- 🤖 AI/ML: RAG, LLMs, NLP, Computer Vision
- 💻 Full-Stack: Python, Streamlit, FastAPI, React
- 🗄️ Databases: PostgreSQL, MongoDB, FAISS
- ☁️ Cloud: AWS, Render, Streamlit Cloud
- 🛠️ Tools: Git, Docker, VS Code

**Project Motivation:**

> "As a student, I've experienced firsthand the confusion around examination processes. This chatbot aims to make institutional information accessible and understandable for all students, reducing anxiety and improving transparency in academic evaluations."
> 
> — Malipeddi Sekhar

### Contact & Support

- **GitHub Issues**: [Report bugs or request features](https://github.com/malipeddisekhar/Education-Examination-Evaluation-Process-Explainer-Bot/issues)
- **Email**: malipeddisekhar@gmail.com
- **Institution**: AITAM, Tekkali, Andhra Pradesh, India

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2026 Malipeddi Sekhar

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🙏 Acknowledgments

- **AITAM** - For providing the academic environment and support
- **Error Squad Team** - For collaboration and feedback
- **Groq** - For providing free, fast LLM API access
- **Streamlit** - For the amazing web framework
- **HuggingFace** - For open-source models and embeddings
- **LangChain** - For the RAG framework

---

## 📊 Project Stats

- **Lines of Code**: ~1,500+
- **Development Time**: 3 months
- **Technologies Used**: 15+
- **Dependencies**: 40+
- **Supported File Types**: PDF
- **Max Upload Size**: 200MB
- **Response Time**: 2-5 seconds
- **Accuracy**: Document-grounded (no hallucinations)

---

## 🎯 Future Enhancements

- [ ] Support for Word documents (.docx)
- [ ] Multi-language support
- [ ] Advanced analytics dashboard
- [ ] User authentication system
- [ ] Document comparison feature
- [ ] Export chat history
- [ ] Mobile app version
- [ ] Integration with institutional databases

---

## 📞 Support

If you encounter any issues or have questions:

1. Check the [docs/](docs/) folder for detailed guides
2. Search [existing issues](https://github.com/malipeddisekhar/Education-Examination-Evaluation-Process-Explainer-Bot/issues)
3. Create a [new issue](https://github.com/malipeddisekhar/Education-Examination-Evaluation-Process-Explainer-Bot/issues/new) with details
4. Contact the developer directly

**Last Updated**: May 11, 2026  
**Version**: 1.0.0  
**Status**: ✅ Production Ready


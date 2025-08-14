# MediBot: AI Medical Chatbot with RAG 🚀

[![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-v0.3.26-green?logo=langchain)](https://langchain.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-v1.46.1-red?logo=streamlit)](https://streamlit.io/)


**MediBot** is a Retrieval-Augmented Generation (RAG) chatbot for querying medical PDF documents. Built with LangChain, HuggingFace, FAISS, and Streamlit, it delivers accurate, context-aware answers, minimizing hallucinations. Ideal for healthcare professionals, researchers, and students.

## 🌟 Features
- **Document Processing**: Loads PDFs, splits into 500-character chunks with 50 overlap, embeds using HuggingFace's all-MiniLM-L6-v2.
- **Vector Storage**: Stores embeddings in FAISS for fast similarity search.
- **RAG Pipeline**: Integrates LLMs (Mistral-7B or Llama-4) for grounded responses.
- **Interactive UI**: Streamlit chat interface with source document display.
- **Modular Design**: Three-phase architecture (Memory, LLM, UI) for scalability.
- **Custom Prompts**: Context-bound answers with no small talk.
- **Future-Ready**: Supports authentication, multi-document embedding, unit testing.

## 📂 Project Structure
```
.
├── README.md                  # This file
├── create_memory_for_llm.py   # Loads PDFs, chunks, embeds, stores in FAISS
├── connect_memory_with_llm.py # Connects LLM with FAISS for CLI queries
├── medibot.py                 # Streamlit chatbot UI
├── requirements.txt           # Dependency list
├── Pipfile                    # Pipenv configuration
├── Pipfile.lock               # Locked dependencies
├── data/                      # Input PDFs directory
├── vectorstore/               # FAISS vector database
└── medical-chatbot-ppt.pdf    # Project presentation
```

## 🛠️ Installation

### Prerequisites
- Python 3.12
- Pipenv

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/medibot.git
   cd medibot
   ```

2. Install dependencies:
   ```
   pipenv install
   ```
   Or:
   ```
   pip install -r requirements.txt
   ```

3. Set environment variables:
   ```
   HF_TOKEN=your_huggingface_token
   GROQ_API_KEY=your_groq_api_key
   ```

## 🚀 Usage

### Phase 1: Build Vector Database
Place PDFs in `data/`, then run:
```
pipenv run python create_memory_for_llm.py
```
Outputs FAISS index to `vectorstore/db_faiss`.

### Phase 2: CLI Querying
Run:
```
pipenv run python connect_memory_with_llm.py
```
Enter queries via terminal.

### Phase 3: Chatbot UI
Launch Streamlit:
```
pipenv run streamlit run medibot.py
```
Access at `http://localhost:8501`.

**Example Query**: "What are the symptoms of diabetes?"

## 📈 How It Works
1. **Load & Chunk**: PyPDFLoader and RecursiveCharacterTextSplitter prepare documents.
2. **Embed & Store**: HuggingFaceEmbeddings with FAISS for vector storage.
3. **Retrieve & Generate**: RetrievalQA fetches top-3 chunks, LLM generates answers.
4. **UI**: Streamlit caches vector store, manages sessions, displays results.

## 🔧 Customization
- Switch LLMs: Modify `medibot.py` for HuggingFace or Groq.
- Adjust Chunks: Edit `chunk_size`, `chunk_overlap` in `create_memory_for_llm.py`.
- Enhance Prompt: Update `CUSTOM_PROMPT_TEMPLATE`.

## 📊 Improvements
- **Efficiency**: Low-latency PDF processing with FAISS.
- **Accuracy**: RAG ensures context-aware answers.
- **Next Steps**: Add authentication, document upload, multi-PDF support, unit tests.



## 🙏 Acknowledgments
- LangChain, HuggingFace, Groq, FAISS, Streamlit.


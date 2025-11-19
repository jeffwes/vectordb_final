# Supportco AI Support Assistant  
**A local RAG + OpenAI-powered desktop chat app that answers questions using your own support manual**

![](https://img.shields.io/badge/Python-3.11-blue) ![](https://img.shields.io/badge/Tkinter-GUI-green) ![](https://img.shields.io/badge/Qdrant-Vector%20DB-orange) ![](https://img.shields.io/badge/OpenAI-GPT--3.5%20/%20GPT--4-brightgreen)

This app turns any PDF (or .txt/.md) support manual into an intelligent AI assistant that can answer user questions in natural language — instantly and accurately.

No training. No fine-tuning. Just drop your manual and ask questions.

---

### Features
- **Local semantic search** using Sentence-Transformers + Qdrant (offline & private)
- **Natural answers** powered by OpenAI GPT (gpt-3.5-turbo or gpt-4o)
- **Zero hallucinations** — answers come only from your documents
- **Beautiful desktop GUI** with Tkinter
- **Secure** — OpenAI key stored in `.env`
- Works completely offline (except the final GPT call)

---

### Quick Start (Cold Boot → Running in < 2 minutes)

```bash
# 1. Clone / open the project folder
cd /path/to/VectorDB

# 2. Activate virtual environment
source venv/bin/activate

# 3. Start Qdrant (Docker)
docker start qdrant_demo || docker run -d --name qdrant_demo \
  -p 6333:6333 -p 6334:6334 \
  -v $(pwd)/qdrant_storage:/qdrant/storage qdrant/qdrant

# 4. Build the knowledge base (once, or when you update docs)
python build_vector_db.py

# 5. Launch the AI chat
python support_chat.py
```

That’s it — ask anything about your manual!

---

### Folder Structure
```
VectorDB/
├── build_vector_db.py          # Builds vector DB from your docs
├── support_chat.py             # The AI chat GUI (main app)
├── support_docs/               # ← Put your PDFs, .txt, .md here
│   └── Supportco Manual.pdf
├── qdrant_storage/             # Persistent Qdrant data (Docker)
├── .env                        # Your OpenAI key (never commit!)
├── venv/                       # Python virtual environment
└── vector_db_built.flag        # Created when DB is ready
```

---

### Requirements
- Python 3.11
- Docker Desktop (for Qdrant)
- OpenAI API key

Install everything once:
```bash
pip install -r requirements.txt   # (or use the full pip command from the guide)
```

---

### Configuration
Create a `.env` file in the project root:
```env
OPENAI_API_KEY=sk-your-real-key-here
```

Add to `.gitignore`:
```gitignore
.env
*.env
```

---

### Supported Document Types
- `.pdf`
- `.txt`
- `.md` (Markdown)
- Just drop them in `support_docs/` — they’re automatically loaded!

---

### Want a Web Version?
Run this instead of `support_chat.py`:
```bash
python web_app.py        # → opens http://localhost:5000 in browser
```


---

### Credits & License
- Built with **LangChain**, **Sentence-Transformers**, **Qdrant**, **Tkinter**, and **OpenAI**
- Free for personal and educational use
- Made with love for teaching real-world AI

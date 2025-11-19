# 1. Open Terminal (or iTerm)

# 2. Go to your project folder
cd /Users/jeff/Dropbox/UDEL/Code/VectorDB
# (or wherever your folder is)

# 3. Activate your virtual environment
source venv/bin/activate
# → You will see (venv) in your prompt

# 4. Start Qdrant (Docker) — this survives reboots if you keep the terminal open
docker start qdrant_demo || docker run -d --name qdrant_demo -p 6333:6333 -p 6334:6334 -v $(pwd)/qdrant_storage:/qdrant/storage qdrant/qdrant
# → If it was stopped → starts it. If not exist → creates it.

# 5. Wait 5 seconds for Qdrant to be ready, then test (optional but good)
sleep 5 && curl http://localhost:6333 > /dev/null && echo "Qdrant is running!" || echo "Qdrant failed"

# 6. Start Jupyter Notebook (in the same activated venv)
jupyter notebook
# → Browser opens automatically

# 7. In Jupyter: open your notebook → run all cells
#    (or just run build_vector_db.py once if needed)

# 8. In the same terminal (or a new tab with venv active), launch the chat
python support_chat.py
# → Your AI chat window opens and is fully working
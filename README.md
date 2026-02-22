# 🌐 Crawl4Chat: Chat with Any Website

Crawl4Chat is a powerful, Streamlit-based web application that allows you to crawl any website, extract its content, and engage in a conversational chat with that data using Retrieval-Augmented Generation (RAG).

Built with **Crawl4AI** for efficient web scraping and **LangChain** for AI orchestration, this tool transforms static websites into interactive knowledge bases.

## 🚀 Features

- **Smart Web Crawling**: Uses `Crawl4AI` to asynchronously crawl websites, respecting depth limits and page counts.
- **Markdown Extraction**: Automatically converts web pages into clean Markdown, providing high-quality context for the LLM.
- **Conversational RAG**: Implements a `ConversationalRetrievalChain` with memory, allowing for follow-up questions and context-aware responses.
- **Vector Search**: Utilizes `FAISS` for fast and efficient similarity search across crawled content.
- **Source Attribution**: Every answer includes links to the specific pages used as sources.
- **User-Friendly UI**: A clean Streamlit interface with sidebar configurations and real-time progress tracking.
- **Configurable Crawl Parameters**: Adjust maximum pages (1-50) and crawl depth (0-5) via the sidebar.
- **Chat History**: Maintains conversation history for contextual follow-up questions.

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | [Streamlit](https://streamlit.io/) |
| Crawler | [Crawl4AI](https://github.com/unclecode/crawl4ai) |
| LLM Framework | [LangChain](https://www.langchain.com/) |
| Vector Database | [FAISS](https://github.com/facebookresearch/faiss) |
| Embeddings & LLM | OpenAI (GPT-3.5 Turbo / Text-Embedding-3-Small) |
| Parsing | BeautifulSoup4 |

## 📋 Prerequisites

- Python 3.9+
- An OpenAI API Key

## ⚙️ Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/Crawl4Chat.git
   cd Crawl4Chat
   ```

2. **Create a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install streamlit crawl4ai langchain langchain-openai langchain-community faiss-cpu python-dotenv beautifulsoup4
   ```

4. **Configure Environment Variables**:
   Create a `.env` file in the root directory and add your OpenAI API key:
   ```env
   OPENAI_API_KEY=your_api_key_here
   ```

## ⚙️ Configuration

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `OPENAI_API_KEY` | Your OpenAI API key for LLM and embeddings | Yes |

### Crawl Settings

| Parameter | Default | Range | Description |
|-----------|---------|-------|-------------|
| Maximum Pages | 5 | 1-50 | Number of pages to crawl |
| Crawl Depth | 1 | 0-5 | How deep to follow links from the starting URL |

## 🚀 Running the App

Start the Streamlit server:
```bash
streamlit run app.py
```

The application will open in your default browser at `http://localhost:8501`.

## 📖 How to Use

1. **Configure**: Ensure your OpenAI API key is loaded (checked in the sidebar).
2. **Crawl**: Enter a target URL (e.g., `https://docs.python.org`), set the maximum pages and crawl depth.
3. **Process**: Click **"Crawl & Process"**. The app will:
   - Crawl the specified website
   - Extract content from each page
   - Split text into chunks for better retrieval
   - Build a FAISS vector index with embeddings
4. **Chat**: Once processing is complete, use the chat interface to ask questions about the website's content.
5. **View Sources**: Expand the "Sources" section in any response to see which pages were used as references.

### Example Usage

```python
# Environment setup
OPENAI_API_KEY=sk-...

# Run the app
streamlit run app.py

# Then:
# 1. Enter URL: https://docs.python.org/3/
# 2. Set Max Pages: 10, Depth: 2
# 3. Click "Crawl & Process"
# 4. Ask: "What are the main features of Python?"
```

## 🏗️ Project Structure

```
Crawl4Chat/
├── app.py              # Main Streamlit application
│                       # - Crawling logic (async with crawl4ai)
│                       # - RAG chain setup (LangChain + FAISS)
│                       # - UI components and chat interface
├── .env                # Environment variables (API keys)
├── requirements.txt    # Python dependencies
└── LICENSE             # Apache 2.0 License
```

### Key Components in `app.py`

- **`crawl_website()`** - Async website crawler with depth/page limits
- **`create_vector_store()`** - FAISS vector store creation from crawled content
- **`create_conversation_chain()`** - LangChain ConversationalRetrievalChain setup
- **`render_sidebar()`** - Sidebar UI for configuration
- **`render_chat_interface()`** - Chat UI with source attribution

## 🔧 Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| `OPENAI_API_KEY not found` | Create a `.env` file with your OpenAI API key |
| No content extracted | Check if the URL is accessible and has crawlable content |
| Crawl takes too long | Reduce max pages or depth in sidebar settings |
| Rate limiting errors | Wait a moment and try again, or reduce concurrent requests |

### Getting Help

- **OpenAI API Key**: Get one at [platform.openai.com](https://platform.openai.com/)
- **Crawl4AI Issues**: Check the [GitHub repo](https://github.com/unclecode/crawl4ai)
- **Streamlit Issues**: See [Streamlit docs](https://docs.streamlit.io/)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 🧪 Advanced Usage

### Custom Embedding Models

Modify `create_vector_store()` in `app.py` to use different embedding models:

```python
embeddings = OpenAIEmbeddings(
    model="text-embedding-3-small",  # or "text-embedding-ada-002"
    openai_api_key=api_key
)
```

### Adjusting Chunk Size

The default chunk size is 1000 characters with 200 character overlap. Modify in `create_vector_store()`:

```python
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=1500,  # Increase for larger chunks
    chunk_overlap=300  # Increase for more context overlap
)
```

## ⚖️ License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---

*Created with ❤️ using Crawl4AI and LangChain.*
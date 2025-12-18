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

## 🛠️ Tech Stack

- **Frontend**: [Streamlit](https://streamlit.io/)
- **Crawler**: [Crawl4AI](https://github.com/unclecode/crawl4ai)
- **LLM Framework**: [LangChain](https://www.langchain.com/)
- **Vector Database**: [FAISS](https://github.com/facebookresearch/faiss)
- **Embeddings & LLM**: OpenAI (GPT-3.5 Turbo / Text-Embedding-3-Small)
- **Parsing**: BeautifulSoup4

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

## 🚀 Running the App

Start the Streamlit server:
```bash
streamlit run app.py
```

## 📖 How to Use

1. **Configure**: Ensure your OpenAI API key is loaded (checked in the sidebar).
2. **Crawl**: Enter a target URL (e.g., `https://docs.python.org`), set the maximum pages and crawl depth.
3. **Process**: Click **"Crawl & Process"**. The app will crawl the site, chunk the text, and build a vector index.
4. **Chat**: Once processing is complete, use the chat interface to ask questions about the website's content.

## 🏗️ Project Structure

- `app.py`: The main Streamlit application containing crawling logic, RAG chain setup, and UI components.
- `.env`: (User-created) Stores sensitive API keys.
- `LICENSE`: Apache 2.0 License.

## ⚖️ License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---
*Created with ❤️ using Crawl4AI and LangChain.*

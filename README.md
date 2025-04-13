# Hybrid Search RAG with Pinecone and LangChain

<div align="center">
<<<<<<< HEAD
  <img src="assets/pinecone-seeklogo.png" alt="Pinecone Logo" width="200"/>
  <img src="assets/langchain-seeklogo.png" alt="LangChain Logo" width="200"/>
=======
  <img src="https://seeklogo.com/images/P/pinecone-logo-482364.svg" alt="Pinecone Logo" width="200"/>
  <img src="https://seeklogo.com/images/L/langchain-logo-611655.svg" alt="LangChain Logo" width="200"/>
>>>>>>> fb57756f7bd5dbac78d45f7aa1b444594b350f1f
</div>

## 🚀 Overview

This project implements a powerful Hybrid Search RAG (Retrieval-Augmented Generation) system that combines the strengths of both vector search and keyword-based search using Pinecone DB and LangChain. By leveraging Reciprocal Rank Fusion, this hybrid approach delivers more accurate and contextually relevant search results than either method alone.

## 🔍 What is Hybrid Search?

Hybrid search combines two complementary search methodologies:

1. **Vector Search (Semantic Search)**: Uses embeddings to find semantically similar content, even when exact keywords don't match.
2. **Keyword Search (BM25)**: Uses traditional keyword matching to find exact matches based on term frequency and importance.

The system uses Reciprocal Rank Fusion to intelligently combine the results from both approaches, giving you the best of both worlds.

## 🏗️ Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│                 │     │                 │     │                 │
│  User Query     │────▶│  Query          │────▶│  Vector Search  │
│                 │     │  Processing     │     │  (Embeddings)   │
│                 │     │                 │     │                 │
└─────────────────┘     └────────┬────────┘     └────────┬────────┘
                                 │                       │
                                 │                       │
                                 ▼                       ▼
                        ┌─────────────────┐     ┌─────────────────┐
                        │                 │     │                 │
                        │  Keyword Search │     │  Results        │
                        │  (BM25)         │     │  Ranking        │
                        │                 │     │                 │
                        └────────┬────────┘     └────────┬────────┘
                                 │                       │
                                 │                       │
                                 ▼                       ▼
                        ┌─────────────────┐     ┌─────────────────┐
                        │                 │     │                 │
                        │  Reciprocal     │     │  Final          │
                        │  Rank Fusion    │────▶│  Results        │
                        │                 │     │                 │
                        └─────────────────┘     └─────────────────┘
```

## ✨ Features

- **Semantic Understanding**: Captures the meaning behind queries, not just keywords
- **Exact Matching**: Ensures important keyword matches are not missed
- **Reciprocal Rank Fusion**: Intelligently combines results from both search methods
- **Pinecone Integration**: Leverages Pinecone's vector database for efficient similarity search
- **LangChain Framework**: Utilizes LangChain for seamless integration with LLMs
- **BM25 Algorithm**: Implements the industry-standard BM25 algorithm for keyword search
- **HuggingFace Embeddings**: Uses state-of-the-art embedding models

## 🛠️ Setup

### Prerequisites

- Python 3.8+
- Pinecone API key
- HuggingFace account (for embeddings)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Hybrid-Search-RAG.git
   cd Hybrid-Search-RAG
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up environment variables:
   Create a `.env` file in the root directory with your API keys:
   ```
   PINECONE_API_KEY=your_pinecone_api_key
   ```
   
### Advanced Configuration

You can customize the hybrid search behavior by adjusting parameters:

- **Embedding Model**: Choose different HuggingFace models for embeddings
- **BM25 Parameters**: Adjust k1 and b parameters for keyword search
- **Reciprocal Rank Fusion**: Modify the fusion algorithm parameters

## 📊 How It Works

1. **Document Processing**:
   - Documents are split into chunks
   - Each chunk is embedded using HuggingFace embeddings
   - BM25 statistics are computed for keyword search

2. **Query Processing**:
   - The query is embedded using the same embedding model
   - The query is also processed for BM25 keyword search

3. **Dual Search**:
   - Vector search finds semantically similar documents
   - Keyword search finds documents with matching terms

4. **Result Fusion**:
   - Reciprocal Rank Fusion combines the ranked results
   - Final results are returned with relevance scores

## 🔬 Example

In the included notebook, we demonstrate how to:
- Set up a Pinecone index for hybrid search
- Process and index documents
- Perform hybrid searches with different queries
- Analyze the results from both search methods

## 📈 Performance

Hybrid search typically outperforms either method alone:
- **Vector Search**: Great for semantic understanding but can miss exact matches
- **Keyword Search**: Excellent for exact matches but struggles with synonyms and context
- **Hybrid Search**: Combines both strengths for more accurate and comprehensive results

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [Pinecone](https://www.pinecone.io/) for their vector database
- [LangChain](https://www.langchain.com/) for their RAG framework
- [HuggingFace](https://huggingface.co/) for their embedding models

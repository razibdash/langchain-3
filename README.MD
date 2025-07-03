# LangChain Data Loader RAG Demo

This notebook demonstrates how to use various data loaders from the `langchain_community` library to load and process different data formats for Retrieval-Augmented Generation (RAG) workflows. Below is a line-by-line description of each topic covered:

---

## 1. Environment Setup

- **Load Environment Variables:**  
  Uses `dotenv` to load API keys and other environment variables from a `.env` file.

- **Import Required Libraries:**  
  Imports necessary Python packages, including `os`, `dotenv`, and LangChain modules.

---

## 2. LLM Initialization

- **Initialize Groq LLM:**  
  Sets up the `ChatGroq` large language model with your API key and model parameters.

- **Test LLM:**  
  Sends a sample message to the LLM and prints the response.

---

## 3. Data Loaders

### a. Text Data Loader

- **TextLoader:**  
  Loads plain text files (e.g., `data/be-good.txt`) and prints the content.

### b. CSV Data Loader

- **CSVLoader:**  
  Loads CSV files (e.g., `data/Street_Tree_List.csv`) and prints the first row's content.

### c. HTML Data Loader

- **UnstructuredHTMLLoader:**  
  Loads and parses HTML files (e.g., `data/test.html`).

### d. PDF Data Loader

- **PyPDFLoader:**  
  Loads and splits PDF files (e.g., `data/5pages.pdf`) and prints the first page's content.

### e. JSON Data Loader

- **JSONLoader:**  
  Loads JSON files (e.g., `data/people.json`) using a `jq_schema` to extract specific fields.  
  Prints each document's content.

### f. Wikipedia Data Loader

- **WikipediaLoader:**  
  Loads content from Wikipedia for a given query (e.g., "Tesla") and prints the result.

---

## 4. Prompt Engineering

- **ChatPromptTemplate:**  
  Demonstrates how to create a prompt template for the LLM, including context from loaded data.

---

## 5. LLM Response Generation

- **Invoke LLM with Context:**  
  Sends a formatted prompt (with context) to the LLM and prints the response.

---

## 6. Troubleshooting

- **Common Errors:**
  - `ModuleNotFoundError`: Install missing packages using `pip`.
  - `BadZipFile`: Ensure you use valid `.docx` files for DOCX loaders.
  - `ValueError`: Convert dicts to strings when required for output.

---

## 7. Requirements

- Python 3.8+
- Install dependencies:
  ```
  pip install langchain_community langchain_groq python-dotenv jq
  ```

---

---

# LangChain RAG Components Demo

This notebook demonstrates the core components of a Retrieval-Augmented Generation (RAG) workflow using the LangChain library. Below is a line-by-line description of each topic and code section:

---

## 1. Environment Setup

- **Load Environment Variables:**  
  Uses `dotenv` to load API keys and environment variables from a `.env` file.
- **Import Required Libraries:**  
  Imports Python packages such as `os`, `dotenv`, and LangChain modules.

---

## 2. Text Data Loading

- **TextLoader:**  
  Loads a plain text file (`data/be-good.txt`) and reads its content.

---

## 3. Text Splitting

- **CharacterTextSplitter:**  
  Splits the loaded text into chunks using a character-based splitter with specified chunk size and overlap.
- **RecursiveCharacterTextSplitter:**  
  Demonstrates recursive splitting of text into smaller chunks for more granular processing.

---

## 4. Embeddings

- **Install Sentence Transformers:**  
  Installs the `sentence-transformers` package for embedding generation.
- **HuggingFaceEmbeddings:**  
  Uses a HuggingFace model (`all-MiniLM-L6-v2`) to convert text chunks into numerical vectors (embeddings).

---

## 5. Vector Stores

- **Chroma Vector Store:**  
  Loads document chunks and their embeddings into a Chroma vector database for efficient similarity search.
- **FAISS Vector Store:**  
  Installs and uses FAISS as an alternative vector database for storing and retrieving embeddings.

---

## 6. Similarity Search

- **Querying the Vector Store:**  
  Performs a similarity search in the vector database to find the most relevant text chunks for a given question.

---

## 7. Retriever

- **Vector Store as Retriever:**  
  Converts the vector store into a retriever object, allowing for easy retrieval of top-k relevant chunks for a query.

---

## 8. Example Queries

- **Sample Questions:**  
  Demonstrates how to ask questions about the loaded documents and retrieve relevant answers using the retriever.

---

## 9. Troubleshooting

- **Common Errors:**
  - `ModuleNotFoundError`: Install missing packages using `pip`.
  - `ValueError`: Ensure correct data types when processing text and embeddings.
  - `BadZipFile`: Use valid `.docx` files for DOCX loaders.

---

## 10. Requirements

- Python 3.8+
- Install dependencies:
  ```
  pip install langchain_community langchain_chroma langchain_text_splitters langchain.embeddings sentence-transformers faiss-cpu python-dotenv
  ```

---

## 11. Notes

- Ensure all data files exist in the `data/` directory.
- Update API keys and environment variables as needed.
- For DOCX files, always use `.docx` format (not `.doc`).

---

# Basic RAG Implementation with LangChain

This notebook demonstrates a step-by-step implementation of a basic Retrieval-Augmented Generation (RAG) workflow using LangChain. Below is a line-by-line description of each topic and code section:

---

## 1. Environment Setup

- **Load Environment Variables:**  
  Uses `dotenv` to load API keys and environment variables from a `.env` file.
- **Import Required Libraries:**  
  Imports Python packages such as `os`, `dotenv`, and LangChain modules.

---

## 2. Embedding Model Initialization

- **Install and Import Embeddings:**  
  Uses HuggingFace's `sentence-transformers/all-MiniLM-L6-v2` model to generate embeddings for text chunks.

---

## 3. Data Loading

- **TextLoader:**  
  Loads a plain text file (`data/razib.txt`) and reads its content for further processing.

---

## 4. Text Splitting

- **CharacterTextSplitter:**  
  Splits the loaded document into smaller chunks using a character-based splitter with specified chunk size and overlap.

---

## 5. Vector Store Creation

- **FAISS Vector Store:**  
  Converts the text chunks into embeddings and stores them in a FAISS vector database for efficient similarity search.

---

## 6. Retriever Setup

- **Create Retriever:**  
  Converts the vector store into a retriever object, which can fetch relevant chunks for a given query.

---

## 7. Simple Retrieval Example

- **Query the Retriever:**  
  Demonstrates how to ask a question (e.g., "What is Razib Dash?") and retrieve the most relevant chunk from the vector store.

---

## 8. LLM Setup and Prompt Engineering

- **Initialize LLM (ChatGroq):**  
  Sets up the Groq large language model with API key and parameters.
- **Prompt Template:**  
  Defines a prompt template that instructs the LLM to answer questions based only on the provided context.

---

## 9. RAG Chain Construction

- **Format Documents:**  
  Defines a function to format retrieved documents for the prompt.
- **Build LCEL Chain:**  
  Constructs a LangChain Expression Language (LCEL) chain that retrieves context, formats it, applies the prompt, invokes the LLM, and parses the output.

---

## 10. RAG Example Queries

- **Invoke the Chain:**  
  Shows how to use the chain to answer questions like "What is Razib Dash?" and "Razib Dash skills and expertise?" using the RAG workflow.

---

## 11. Troubleshooting

- **Common Errors:**
  - `ModuleNotFoundError`: Install missing packages using `pip`.
  - `ValueError`: Ensure correct data types when processing text and embeddings.

---

## 12. Requirements

- Python 3.8+
- Install dependencies:
  ```
  pip install langchain_community langchain_groq langchain_text_splitters langchain_core sentence-transformers faiss-cpu python-dotenv
  ```

---

## 13. Notes

- Ensure all data files exist in the `data/` directory.
- Update API keys and environment variables as needed.

---

# Multimodal RAG App

This repository contains a Jupyter notebook for building a **Multimodal Retrieval-Augmented Generation (RAG) pipeline** using PDFs. The workflow leverages advanced PDF parsing, extracts text, tables, and images, summarizes each modality, and enables retrieval of relevant information using language models including multi-modal LLMs like GPT-4 Vision.

## Features

- **PDF Parsing with Unstructured:** Extracts text, images, and tables from PDFs.
- **Summarization:** 
  - Summarizes tables and text using OpenAI models for embedding-based retrieval.
  - Generates image summaries using GPT-4 Vision via base64-encoded images.
- **Multivector Retrieval:** 
  - Indexes summaries and returns raw elements (text, tables, images) using a `MultiVectorRetriever` and Chroma vector store.
- **RAG Chain:** 
  - Combines retrieved context and user queries into a prompt for a multi-modal LLM.
- **Image Utilities:** 
  - Encode, display, and resize base64 images for visualization and processing.
- **End-to-end Example:** 
  - Query the system for information (e.g., "What are the categories of AI?") using the built RAG pipeline.

## Quick Start

1. **Install Poppler & Tesseract:**
   - **Windows:** Download from [Poppler Windows](http://blog.alivate.com.au/poppler-windows/) and [Tesseract](https://github.com/UB-Mannheim/tesseract/wiki)
   - **Linux:** `sudo apt-get install poppler-utils tesseract-ocr`
   - **macOS:** `brew install poppler tesseract`

2. **Install Python dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up OpenAI API Key:**
   - Create a `.env` file in the project root:
     ```
     OPENAI_API_KEY=your_openai_api_key_here
     ```

4. **Prepare Data:**
   - Place your PDF in the `./Data/` directory.
   - The notebook extracts images and tables to `./extracted_data/`.

5. **Run the Notebook:**
   - Open `mutimodel_RAG_app.ipynb` in Jupyter and follow the cells.

## Code Structure

- **PDF Extraction:** Uses `unstructured.partition.pdf.partition_pdf` to extract elements.
- **Summarization:** Uses `langchain` and `langchain_openai` for generating summaries.
- **Image Handling:** Utilities for base64 encoding, displaying, and resizing images.
- **Retrieval:** Uses `Chroma` and `MultiVectorRetriever` for indexing and fetching multimodal content.
- **RAG Pipeline:** Combines text, table, and image context for multi-modal LLM Q&A.

## Example Query

```python
chain_multimodal_rag.invoke("What are the categories of AI?")
```

## Notes

- The notebook assumes access to GPT-4 Vision via OpenAI API.
- For large PDFs or lots of images, processing may take time.
- All images and tables are extracted to the `extracted_data` directory.

## License

This project is for educational purposes. Please check the licenses of the respective libraries used.

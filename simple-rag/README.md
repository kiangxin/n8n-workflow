# Simple RAG Workflow

A Retrieval Augmented Generation (RAG) implementation in n8n that enhances AI responses with external knowledge.

## Overview

This workflow implements a basic RAG system that:
1. Loads documents from Google Drive
2. Processes and chunks the document text
3. Creates vector embeddings using Google Gemini
4. Stores these embeddings in a vector database
5. Allows querying the knowledge base through an AI chatbot interface

## How It Works

### Document Processing Pipeline
- **Google Drive Node**: Downloads a PDF document from your Google Drive
- **Extract from File Node**: Extracts text content from the PDF
- **Default Data Loader**: Prepares the text data for processing
- **Recursive Character Text Splitter**: Chunks the text into manageable segments (200 character overlap)
- **Embeddings Google Gemini**: Creates vector embeddings using Google's Gemini model
- **Simple Vector Store**: Stores the document chunks and their embeddings for retrieval

### Chat Interface
- **When chat message received**: Trigger node that activates the workflow when a user sends a message
- **AI Agent**: Orchestrates the retrieval and response generation process
- **OpenRouter Chat Model**: LLM that generates responses based on the retrieved context
- **Vector Store Tool**: Connects the agent to the knowledge base
- **Simple Vector Store**: Retrieves relevant document chunks based on query similarity

## Setup Instructions

1. Configure Google Drive credentials to access your documents
2. Set up Google Gemini API credentials for the embedding model
3. Configure OpenRouter API credentials for the chat model
4. Select a PDF document in Google Drive to serve as your knowledge source
5. Run the document processing part of the workflow first (starting with "When clicking 'Execute workflow'")
6. Test the chatbot by sending messages through the chat interface

## Usage

1. Activate the workflow
2. Send a question through the chat interface
3. The system will:
   - Create an embedding of your question
   - Find similar content in the vector store
   - Provide the relevant context to the AI model
   - Generate a response based on the retrieved information

## Notes

- Both document processing and query embeddings use the same Google Gemini model for consistency
- The recursive text splitter ensures optimal chunk sizes for accurate retrieval
- This implementation uses in-memory vector storage, which is suitable for demonstration purposes
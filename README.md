# Spring AI RAG Demo

A demonstration project showcasing Retrieval Augmented Generation (RAG) implementation using Spring AI and OpenAI's GPT models. This application enables intelligent document querying by combining the power of Large Language Models (LLMs) with local document context.

## Overview

This project demonstrates how to:
- Ingest PDF documents into a vector database
- Perform semantic searches using Spring AI
- Augment LLM responses with relevant document context
- Create an API endpoint for document-aware chat interactions

## Making Requests

Query the API using curl or your preferred HTTP client:

```bash
curl http://localhost:8080/
```

The response will include context from your documents along with the LLM's analysis.

## Architecture Highlights

- **Document Processing**: Uses Spring AI's PDF document reader to parse documents into manageable chunks
- **Vector Storage**: Utilizes PGVector for efficient similarity searches
- **Context Retrieval**: Automatically retrieves relevant document segments based on user queries
- **Response Generation**: Combines document context with GPT-4's capabilities for informed responses

## Getting Started

1. Configure your environment variables:
```properties
OPENAI_API_KEY=your_api_key_here
```

2. Update `application.properties`:
```properties
spring.ai.openai.api-key=${OPENAI_API_KEY}
spring.ai.openai.chat.model=gpt-4
spring.ai.vectorstore.pgvector.initialize-schema=true
```

3. Place your PDF documents in the `src/main/resources/docs` directory

## Running the Application

1. Start Docker Desktop

2. Launch the application:
```bash
./mvnw spring-boot:run
```

The application will:
- Start a PostgreSQL database with PGVector extension
- Initialize the vector store schema
- Ingest documents from the configured location
- Start a web server on port 8080
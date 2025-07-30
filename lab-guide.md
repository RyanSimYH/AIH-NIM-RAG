# Generative AI Examples - Basic RAG Setup

This guide provides step-by-step instructions for setting up and running the Basic RAG (Retrieval-Augmented Generation) example using LangChain.

## Setup Instructions

### 1. Navigate to the Project Directory

First, navigate to the basic RAG example directory:

```bash
cd ~/GenerativeAIExamples/RAG/examples/basic_rag/langchain
```

### 2. Run the Setup Script

Execute the setup script to configure the environment:

```bash
. setup.sh
```

**Note:** The dot (.) before `setup.sh` is important as it sources the script in the current shell session.

### 3. Start the Services

Launch the required services using Docker Compose with the specified profiles:

```bash
docker compose --profile local-nim --profile milvus up -d
```

This command will:
- Start services in detached mode (`-d`)
- Use the `local-nim` profile for local NIM (NVIDIA Inference Microservice) setup
- Use the `milvus` profile for the Milvus vector database

## What's Running

After successful setup, you should have:
- **Local NIM**: NVIDIA Inference Microservice for language model inference
- **Milvus**: Vector database for storing and retrieving embeddings
- **Supporting Services**: Additional containers required for the RAG pipeline


## Interacting With The RAG Playground
On your browser, visit the following URL:
```
<host-ip>:8090
```
Your host should be in the range: ```192.168.10.231-246```

### Ways To Explore The Application
1. ##### Enter a query to the model, for example:
```
Hello, tell me more about DELL AI Factory.
```
2. ##### Explore the Context Window
Use the context window feature to understand how the RAG model incorporates retrieved context into its responses. This helps you see which documents or information snippets influenced the answer.

2. ##### Add your own knowledge
- Click the document upload button in the top right corner
- Upload your own documents to expand the knowledge base or you can use the prepared documents in the repo
- Important: Use only non-sensitive documents for testing to avoid security complications
Supported formats typically include PDF, TXT, and other common document types

4. ##### Enter a query using ```knowledge```.
 You can see how the model incorporates context into its answer. Regardless of how short or long your knowledge base is, the dynamic context reduces the model's chance to hallucinate.

#### Understanding RAG Benefits
As you explore the application, you'll observe how the Retrieval-Augmented Generation approach:

- Provides more accurate, contextual responses
- Reduces model hallucination by grounding answers in retrieved documents
- Allows real-time knowledge base updates without retraining the model
- Maintains performance regardless of knowledge base size through dynamic context selection

## Stopping All Services

To stop all running services:

```bash
docker compose down
```
```bash
docker kill nemollm-inference-microservice
```

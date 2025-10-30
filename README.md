🤖 RAG Chatbot using Amazon Bedrock


📘 Overview

This project demonstrates how to build a Retrieval-Augmented Generation (RAG) chatbot using Amazon Bedrock, Amazon S3, and Amazon OpenSearch Serverless.

RAG enhances an AI model’s ability to answer context-specific questions by retrieving relevant information from external knowledge sources (like your documents) before generating a response.

In simpler terms — this chatbot not only understands your questions but also searches your own data to give accurate, context-aware answers!

💡 What is RAG?

AI models like ChatGPT or Claude are intelligent but limited to their training data. They cannot access your private data or documents unless you explicitly provide them.

Retrieval-Augmented Generation (RAG) solves this by combining two powerful processes:

Retrieval: The model retrieves relevant information from your own data (stored in a Knowledge Base or database).

Generation: It then uses a large language model (LLM) to generate a natural, human-like response based on that retrieved information.

This method enables AI systems to provide accurate, customized answers using your organization’s or project’s private documents.

🧱 Architecture

The RAG chatbot workflow consists of:

Knowledge Base Creation (Amazon Bedrock)

Acts as the chatbot’s personal library.

Stores all relevant documents for answering queries.

Storage (Amazon S3)

Holds the documents that make up the Knowledge Base.

Documents are indexed and embedded for retrieval.

Vector Database (Amazon OpenSearch Serverless)

Stores embeddings (numerical representations of document meaning).

Enables semantic search — finding information by meaning, not just exact words.

AI Models (Amazon Bedrock Models)

Use Titan Text Embeddings v2 for creating embeddings.

Use Llama 3.1 8B and Llama 3.3 70B Instruct for generating conversational responses.

Chat Interface

Allows users to ask questions and receive data-driven, contextually accurate answers.

⚙️ Step-by-Step Implementation
🪣 Step 1: Create a Knowledge Base

Navigate to Amazon Bedrock in the AWS Console.

Create a Knowledge Base with vector store.

Choose Amazon S3 as the data source.

Configure IAM permissions using a new service role.

📁 Step 2: Upload Documents to S3

Create an S3 bucket in the same region (Ohio us-east-2).

Upload your documents (around 10 files recommended).

Keep Block all public access enabled for security.

🧠 Step 3: Finish Setting Up the Knowledge Base

Connect your S3 bucket to the Knowledge Base.

Choose the Titan Text Embeddings v2 model for generating embeddings.

Select Amazon OpenSearch Serverless as the vector database.

Complete setup and create your Knowledge Base.

🔑 Step 4: Enable AI Models

Go to Model Access under Bedrock Configurations.

Enable access for:

Titan Text Embeddings v2

Llama 3.1 8B Instruct

Llama 3.3 70B Instruct

Accept AWS model terms and conditions.

🔄 Step 5: Sync the Knowledge Base

Return to Bedrock → Knowledge Bases.

Select your data source and click Sync.

Bedrock will:

Retrieve documents from S3

Chunk and embed the data

Store embeddings in OpenSearch

💬 Step 6: Chat with Your Chatbot

Click Test Knowledge Base in Bedrock.

Choose the Llama 3.1 8B Instruct model (or 70B for deeper reasoning).

Ask questions like:

“What is levels of IoT?”

“Which AWS services has the student worked with?”

Observe context-based, document-informed responses.

🧩 Core AWS Services Used
Service	Purpose
Amazon Bedrock	Manages the entire RAG pipeline — models, embeddings, and chat interface.
Amazon S3	Stores user or organization documents for Knowledge Base creation.
Amazon OpenSearch Serverless	Stores and retrieves embeddings for semantic search.
IAM	Grants Bedrock permissions to access S3 and OpenSearch resources.

📊 Pricing Overview
Service	                          Cost (Approx.)
Titan Text Embeddings v2	        $0.00002 / 1K tokens
Llama 3.1 8B Instruct	            $0.00022 / 1K tokens
Llama 3.3 70B Instruct	          $0.00072 / 1K tokens
Knowledge Base + OpenSearch	      ~$0.10 / hour

💰 Total estimated cost for this demo: less than $0.01.
🗑️ Don’t forget to delete your Knowledge Base and OpenSearch store after completion to avoid ongoing charges.

📸 Demo Summary

“Hello” Test → Model responds conversationally.

“What is BigData ANalytics” → Retrieves and summarizes information from Knowledge Base.

“How to make tea?” → Returns an “out of context” or “not found” message, proving restricted scope.

🚀 Key Learnings

RAG enables context-specific intelligence without retraining models.

Amazon Bedrock simplifies AI app development with centralized model access.

Vector databases like OpenSearch enhance semantic retrieval.

Proper chunking and embeddings improve chatbot accuracy.

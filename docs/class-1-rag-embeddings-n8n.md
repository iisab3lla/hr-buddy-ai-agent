# Class 1 - RAG, Embeddings and n8n

## Overview

Class 1 focused on building the knowledge base of the HR assistant.

The goal was to create a workflow capable of loading HR policy content, converting it into embeddings, and storing it in a Vector Store so the AI agent could later retrieve relevant information.

---

## Objective

The objective of this class was to create the first version of the assistant's knowledge layer.

This layer allows the chatbot to answer general HR policy questions, such as:

- Vacation rules;
- Work model;
- Internal policies;
- Benefits;
- Working hours.

---

## Workflow 1 - Document Ingestion

The first workflow was responsible for retrieving and processing HR policy content.

The workflow structure was:

```text
Manual Trigger
      |
      v
HTTP Request
      |
      v
Simple Vector Store
     / \
    /   \
Embeddings Cohere
Default Data Loader
```

---

## Manual Trigger

The Manual Trigger was used to start the workflow manually during testing.

This is useful when building an ingestion process because the document does not need to be loaded continuously.

---

## HTTP Request

The HTTP Request node was used to retrieve the HR policy document from an external URL.

This allowed n8n to load the text that would later be transformed into searchable knowledge.

---

## Document Loader

The Document Loader prepared the raw content so it could be processed by the Vector Store.

Its role was to transform the retrieved data into a format that the vector database could understand.

---

## Embeddings with Cohere

Cohere Embeddings were used to convert the HR policy text into numerical vectors.

These vectors represent the meaning of the text and make semantic search possible.

This is important because the user does not need to use the exact same words that appear in the original document. The system can search by meaning.

---

## Vector Store

The Simple Vector Store was used to store the document chunks and their embeddings.

When a user asks a question, the system can compare the question embedding with the stored embeddings and retrieve the most relevant text sections.

---

## Workflow 2 - Chatbot with AI Agent

After creating the knowledge base, a second workflow was created to test the chatbot.

The workflow included:

```text
Chat Trigger
      |
      v
AI Agent
  /    |     \
Chat  Memory  Vector Store Tool
Model
```

---

## AI Agent

The AI Agent receives the user's message, interprets the request, and decides whether it should use the Vector Store to search for information.

The agent is connected to:

- A chat model;
- A memory node;
- A Vector Store tool.

---

## Chat Model

The Cohere Chat Model is responsible for understanding the user message and generating the final response.

It is different from the embedding model:

- The chat model generates language;
- The embedding model generates vectors for semantic search.

---

## Memory

The Simple Memory node stores recent conversation context.

This allows the assistant to understand follow-up questions instead of treating every message as completely isolated.

---

## Vector Store as a Tool

The Vector Store was connected to the AI Agent as a tool.

This allows the agent to retrieve HR policy information when the user asks a general HR question.

---

## Tool Description

A tool description was added to help the agent understand when to use the Vector Store.

This is important because agents choose tools based on names, descriptions, and instructions.

A good tool description improves the quality of tool selection.

---

## Result

At the end of Class 1, the project had:

- A document ingestion workflow;
- A Vector Store containing HR policy content;
- An AI Agent connected to a chat model;
- Memory for conversation context;
- A Vector Store tool for policy-based answers.

---

## Key Learnings

In this class, I practiced:

- Creating workflows in n8n;
- Loading external documents;
- Understanding embeddings;
- Using a Vector Store;
- Building a basic RAG pipeline;
- Connecting a Vector Store to an AI Agent;
- Testing an agent inside n8n before connecting it to Telegram.

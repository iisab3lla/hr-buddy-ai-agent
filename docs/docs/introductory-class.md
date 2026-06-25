# Introductory Class - From Generative AI to AI Agents

## Overview

This introductory class presented the evolution of generative AI, from isolated language models to more capable AI agents connected to tools, memory, external data, and automation workflows.

The main idea was to understand that modern AI systems are no longer limited to generating text. They can retrieve information, call tools, interact with databases, and execute tasks through orchestration platforms.

---

## Generative AI

Generative AI is a category of artificial intelligence capable of creating new content based on patterns learned during training.

Examples of generated content include:

- Text;
- Images;
- Audio;
- Code;
- Summaries;
- Structured answers.

In this project, generative AI is used mainly to understand user messages and generate natural language responses.

---

## LLM

LLM stands for Large Language Model.

A Large Language Model is trained on large volumes of text and learns statistical patterns in language. It predicts the most likely continuation of a text based on the context it receives.

In practice, an LLM can:

- Understand user instructions;
- Generate answers;
- Summarize information;
- Classify text;
- Translate content;
- Help write code;
- Interact with external tools when integrated into an agentic system.

However, an LLM by itself does not automatically know private company data or real-time information. It needs external context, tools, or integrations to answer specific questions reliably.

---

## Hallucinations

A hallucination happens when an AI model generates information that sounds correct but is inaccurate, invented, or unsupported by the available data.

This is one of the reasons why systems based only on a language model can be risky in business scenarios.

To reduce hallucinations, AI applications can use:

- RAG;
- Databases;
- Tool calling;
- External validation;
- Clear system instructions;
- Human review for sensitive cases.

---

## RAG

RAG stands for Retrieval-Augmented Generation.

RAG is a technique that allows an AI system to retrieve relevant information from external sources before generating an answer.

Instead of relying only on the model's internal knowledge, the system searches documents or databases and sends the relevant context to the model.

A simplified RAG flow:

```text
User question
      |
      v
Search relevant documents
      |
      v
Send retrieved context to the LLM
      |
      v
Generate an answer based on the context
```

In HR Buddy, RAG is used to answer questions about general HR policies.

---

## Embeddings

Embeddings are numerical representations of text.

They allow a system to compare the meaning of different pieces of text. Texts with similar meanings tend to have similar vector representations.

For example:

```text
"How many vacation days do I have?"
```

can be semantically related to:

```text
"Vacation balance and time off policy"
```

even if the exact words are different.

Embeddings are essential for semantic search and RAG systems.

---

## Tools

Tools are external functions or services that an AI agent can use to retrieve data or perform actions.

Examples of tools:

- Querying a database;
- Calling an API;
- Sending a Telegram message;
- Searching a document;
- Running a calculation;
- Creating or updating records.

In this project, the AI agent uses tools such as MySQL and Vector Store.

---

## Agentic AI

Agentic AI refers to systems that can reason about a goal, choose actions, use tools, and adjust their behavior based on results.

An AI agent usually combines:

- A language model;
- Instructions;
- Memory;
- Tools;
- External data;
- An orchestration layer.

In this project, n8n acts as the orchestration layer, while Cohere provides the language and embedding models.

---

## Technology Stack Introduced

The class introduced the main technologies used throughout the project:

| Tool | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| Cohere | Language model and embeddings |
| MySQL | Structured data storage |
| Railway | Cloud database hosting |
| Telegram | Chatbot interface |
| RAG | Retrieval from external documents |
| Vector Store | Semantic search over text |

---

## Key Takeaway

The most important concept from the introductory class is that a useful AI system is not only a chatbot.

A practical AI agent combines language understanding, external knowledge, tools, memory, and automation to complete real tasks.

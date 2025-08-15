# Multi-Tool-And-Retriever-Conversational-AI-Agent-with-LangChain-RAG-Tool-
# Multi-Tool Conversational AI Agent with LangChain & Groq

![Python Version](https://img.shields.io/badge/python-3.8+-blue.svg)
![LangChain](https://img.shields.io/badge/LangChain-b033ff?style=flat&logo=langchain&logoColor=white)
![Groq](https://img.shields.io/badge/Powered%20by-Groq-5dae5d?style=flat)

This project demonstrates how to build a powerful and versatile conversational AI agent using LangChain, Groq's Llama 3 model, and a combination of specialized tools. The agent is capable of answering a wide range of queries by leveraging **Wikipedia** for general knowledge, a custom **RAG (Retrieval-Augmented Generation)** pipeline for specific documentation (in this case, LangSmith), and **Tavily** for real-time web search.

---

## 📜 About The Project

This notebook implements an advanced conversational agent that can dynamically choose the best tool to answer a user's question. By integrating multiple data sources, the agent can provide comprehensive and accurate responses on various topics, from factual information and technical documentation to current events.

This project serves as an excellent example of how to:
- Integrate multiple tools within a LangChain agent.
- Use a custom retriever for domain-specific knowledge.
- Leverage a fast LLM provider like Groq for near-instant inference.
- Create a flexible and intelligent conversational AI.

---

## ✨ Features

- **Multi-Tool Capability**: Seamlessly switches between different tools to find the best information.
- **Wikipedia Integration**: Accesses the vast repository of Wikipedia for general knowledge questions about people, places, and historical events.
- **Custom Document Search**: Utilizes a custom-built retriever to search through specific documentation—in this case, the LangSmith docs.
- **Real-Time Web Search**: Employs the Tavily Search API to answer questions about current events and provide up-to-date information.
- **Fast and Powerful LLM**: Powered by the **Llama-3 8B model** running on the Groq LPU™ Inference Engine for high-speed responses.

---

## 🛠️ How It Works

The agent's intelligence stems from its architecture, which combines several key components:

1.  **Tools**: The agent has access to a set of tools. Each tool has a specific purpose:
    * `wikipedia`: For answering general knowledge questions.
    * `langsmith-search`: A custom retriever that searches the LangSmith documentation. It uses a FAISS vector store and Hugging Face embeddings to find relevant document chunks.
    * `tavily_search_results_json`: For performing real-time web searches to get up-to-date information.

2.  **LLM (Large Language Model)**: The core of the agent is the **Llama 3** model, accessed via the Groq API. The LLM is responsible for reasoning, understanding the user's query, and deciding which tool (if any) to use.

3.  **Agent**: The `create_openai_tools_agent` function from LangChain assembles the LLM and the tools. It uses a prompt template (`hwchase17/openai-functions-agent`) that instructs the model on how to behave as an agent and how to use the available tools.

4.  **Agent Executor**: This is the runtime for the agent. When a user query is received, the `AgentExecutor` passes it to the agent. The agent (powered by the LLM) decides which tool to call. The `AgentExecutor` then runs that tool, gets the output, and passes it back to the agent. The agent then synthesizes the final response to the user. This process may involve multiple tool calls.

5.  

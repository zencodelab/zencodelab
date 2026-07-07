# ZenCodeLab

Production-grade AI and full-stack demos by [Afsal A Azeez](https://github.com/afsalaazeez) — M.Tech IIT Bombay, 5+ years building LLM systems and full-stack software at Zettabytes, makers of Roost.ai.

---

## Projects

### [AgentForge](https://github.com/zencodelab/agent-orchestrator) — Real-Time Multi-Agent Orchestration Platform

A LangGraph **Planner → Researcher → Synthesizer** pipeline whose execution is streamed live to the browser and visualized on an interactive graph. **[Live demo →](https://zencodelab.github.io/agent-orchestrator/)** (runs entirely client-side, no API keys needed).

- **Server-Sent Events** stream every node transition and token to a live [React Flow](https://reactflow.dev) graph (idle → active → done/error) with a token-by-token log
- **Resumable streaming**: events persisted with a monotonic `seq`; the client reconnects with `last_event_id` and the server replays only the missed tail
- Runs persisted to SQLite (refresh- and replay-safe) with per-node error resilience — a failed agent turns red while the rest of the pipeline finishes
- **Deterministic mock LLM** so the full stack demos offline; swap in real OpenAI + Tavily via env vars
- Dockerized (`docker compose up`) — FastAPI backend + Vite/React frontend

**Stack:** React · TypeScript · React Flow · Zustand · FastAPI · LangGraph · SQLite · SSE · Docker

---

### [GovShield](https://github.com/zencodelab/raglearn) — Secure Offline RAG Portal

100% offline Retrieval-Augmented Generation system with role-based access control.

- **RBAC pre-filtering** at the vector store layer — chunks tagged `L1`/`L2`/`Public` at ingestion; clearance enforced before retrieval, not post-retrieval
- Full ingestion pipeline: multi-page PDF parsing, sentence-level chunking, local embedding via Ollama (`nomic-embed-text` 768d), storage in PostgreSQL pgvector
- **FastAPI REST API** (`POST /query`) with Pydantic-validated request/response and auto-generated Swagger UI
- Streamlit dashboard + interactive CLI
- Dockerized multi-service deployment (pgvector DB + Streamlit UI + FastAPI)
- Grounding guardrail refuses out-of-scope queries

**Stack:** Python · LlamaIndex · PostgreSQL pgvector · FastAPI · Ollama · Docker

---

### [TaskEngine](https://github.com/zencodelab/aiautonomous) — Autonomous Task Agent

Plan → Execute → Reflect autonomous loop built with LangChain and LangGraph.

- **Planner** (LangChain + GPT-4o) decomposes plain-text queries into ordered atomic steps with tool hints; retrieves similar past runs from Pinecone for few-shot context
- **Executor** (LangGraph `create_react_agent`) runs each step as a ReAct agent with a full tool suite: web search, Python execution, file I/O, math evaluation, knowledge retrieval
- **Reflector** (LangChain) scores output quality 0.0–1.0 and triggers re-planning if below threshold
- **Knowledge store** (Pinecone) persists past execution results for future planner context
- FastAPI REST server, CLI interface, and test suite included

**Stack:** Python · LangChain · LangGraph · Pinecone · FastAPI · OpenAI

---

## About

| | |
|---|---|
| **Main profile** | [github.com/afsalaazeez](https://github.com/afsalaazeez) |
| **Portfolio** | [afsal-a-azeez.in](https://afsal-a-azeez.in) |
| **LinkedIn** | [linkedin.com/in/afsalaazeez](https://www.linkedin.com/in/afsalaazeez/) |
| **Email** | afsalaazeez@gmail.com |

Core stack across projects: Python · TypeScript · React · Node.js · FastAPI · LangChain · LlamaIndex · PostgreSQL · Docker · Kubernetes · AWS

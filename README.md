<div align="center">

# William Dumaszak

### Senior AI Engineer · LLM Systems · RAG · AI Agents · MLOps

</div>

---

AI Engineer focused on designing and delivering end-to-end inteligent systems for enterprise environments — from architecture decisions and fine-tuning strategy to production serving, evaluation pipelines, and observability.

I work across the full data and AI stack: classical machine learning and mlops systems, retrieval-augmented generation with adaptive routing and hybrid search and production-grade serving infrastructure with real-time monitoring. My work is driven by the question of what actually makes AI systems reliable and maintainable in production, not just on paper.

---

## Featured Projects

### 🔍 [Agentic RAG Platform](https://github.com/WilliamDumaszak/agentic-rag-platform)

> Graph-based agentic RAG with adaptive routing, hybrid retrieval, reranking, and evaluation.

The core design challenge here is routing: not every query needs retrieval, and not every retrieval needs the same strategy. The agent, built with **LangGraph**, routes per query across local vector search (ChromaDB), cloud semantic search (Azure AI Search), web fallback, and direct generation — then generates multiple candidates and ranks them by semantic similarity before returning the best answer with a confidence score.

Includes a full RAGAS evaluation endpoint, document ingestion pipeline via Azure Document Intelligence, prompt versioning, and a HITL queue for edge case review.

```
Query → decision node → [Chroma | Azure AI Search | web search | direct]
      → generate N candidates → rerank → best answer + confidence + sources
```

**Design decisions:** LangGraph over vanilla chains for explicit state management and auditability. Hybrid retrieval (BM25 + dense) with cross-encoder reranking to reduce hallucination on ambiguous queries.

`Python` `LangGraph` `FastAPI` `Azure AI Search` `ChromaDB` `Docker` `RAGAS` `Azure Document Intelligence`

---

### 📡 [LLM Serving & Monitoring](https://github.com/WilliamDumaszak/llm-serving-monitoring)

> Production LLM serving stack with RAG, full observability, audit logging, and scheduled ingestion.

This project addresses what happens after a model is deployed: how do you actually know if it's working well in production? The stack runs Ollama/vLLM/Azure OpenAI behind a FastAPI layer, with every interaction persisted to PostgreSQL for audit and retraining signals. A custom Prometheus exporter tracks retrieval latency, generation latency, and RAGAS quality scores in real time — surfaced in Grafana dashboards.

Document ingestion runs on an Airflow schedule, keeping the Elasticsearch index fresh without manual intervention. Kubernetes manifests and HPA config included for horizontal scaling.

```
Airflow DAG → Elasticsearch refresh
User query → /query → BM25 retrieval → LLM → PostgreSQL audit → Prometheus metrics → Grafana
```

**Design decisions:** Prometheus over managed observability for cost control and custom metric flexibility. PostgreSQL for interaction storage over NoSQL to enable structured querying for evaluation.

`Python` `Elasticsearch` `Ollama` `vLLM` `PostgreSQL` `Prometheus` `Grafana` `Airflow` `Kubernetes` `Docker`

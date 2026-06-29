<div align="center">

# William Dumaszak

### Senior AI Engineer · LLM Systems · RAG · Fine-tuning · MLOps

<p>
  <a href="https://www.linkedin.com/in/william-dumaszak-17072000/">
    <img src="https://img.shields.io/badge/LinkedIn-william--dumaszak-0A66C2?style=flat-square&logo=linkedin" />
  </a>
  <a href="mailto:william.dumaszak@avanade.com">
    <img src="https://img.shields.io/badge/Avanade-AI%20Engineer-FF6900?style=flat-square&logo=microsoft" />
  </a>
</p>

</div>

---

AI Engineer at **Avanade** focused on designing and delivering end-to-end LLM systems for enterprise environments — from architecture decisions and fine-tuning strategy to production serving, evaluation pipelines, and observability.

I work across the full LLM stack: retrieval-augmented generation with adaptive routing and hybrid search, LoRA fine-tuning with rigorous baseline comparison, and production-grade serving infrastructure with real-time monitoring. My work is driven by the question of what actually makes LLM systems reliable and maintainable in production, not just on paper.

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

### 💹 [LLM Fine-tuning for Finance](https://github.com/WilliamDumaszak/llm-finetuning-finance)

> End-to-end LoRA fine-tuning pipeline for financial sentiment — from dataset prep to Azure production.

Fine-tuned a 1B parameter LLM on financial news for 3-class sentiment classification (`negative`, `neutral`, `positive`) using instruction-style formatting and TRL. Evaluation is structured as a proper A/B: base model vs. tuned model on the same held-out set, tracked via MLflow.

The project covers the full lifecycle: data curation with quality filters, LoRA training with configurable rank/alpha, checkpoint evaluation, adapter merge for clean export, FastAPI serving with per-class confidence scores, and Azure deployment via Terraform + GitHub Actions CI/CD.

```
financial_phrasebank → data prep → LoRA (TRL) → eval vs. base → merge → FastAPI → Azure
```

**Design decisions:** LoRA over full fine-tuning for parameter efficiency and reproducibility. Instruction-tuning format to keep the model general while specializing on the task.

`Python` `LoRA` `TRL` `HuggingFace` `FastAPI` `MLflow` `Docker` `Terraform` `Azure` `GitHub Actions`

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

---

## Tech Stack

| Area | Tools |
|---|---|
| **LLM / Fine-tuning** | HuggingFace Transformers, TRL, LoRA/QLoRA, MLflow |
| **Agentic / RAG** | LangGraph, LangChain, RAGAS, cross-encoder reranking |
| **Serving** | FastAPI, Ollama, vLLM, Azure OpenAI |
| **Retrieval** | Elasticsearch, Azure AI Search, ChromaDB |
| **Infrastructure** | Docker, Kubernetes, Terraform, GitHub Actions |
| **Observability** | Prometheus, Grafana, Airflow |
| **Cloud** | Azure (AI Search, Document Intelligence, Container Apps, ML, AKS) |

---

## Currently

- Building and evaluating agentic LLM systems for enterprise use cases at Avanade
- Exploring evaluation frameworks beyond RAGAS: LLM-as-judge patterns and automated red-teaming
- Interested in conversations about production RAG, fine-tuning strategy, and LLM reliability

---

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=WilliamDumaszak&show_icons=true&theme=dark&hide_border=true&count_private=true)

</div>

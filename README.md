<div align="center">

# William Dumaszak

### ML/AI Engineer · LLM Systems · RAG · MLOps

<p>
  <a href="https://github.com/WilliamDumaszak">
    <img src="https://img.shields.io/badge/GitHub-WilliamDumaszak-181717?style=flat-square&logo=github" />
  </a>
  <a href="https://linkedin.com/in/williamdumaszak">
    <img src="https://img.shields.io/badge/LinkedIn-williamdumaszak-0A66C2?style=flat-square&logo=linkedin" />
  </a>
</p>

</div>

---

I build production-grade LLM systems — from fine-tuning and RAG pipelines to serving infrastructure with observability and evaluation loops.

---

## Featured Projects

### 🔍 [Agentic RAG Platform](https://github.com/WilliamDumaszak/agentic-rag-platform)

> Graph-based RAG agent with adaptive routing, hybrid retrieval, and answer ranking.

Built with **LangGraph**, the agent dynamically decides per query whether to retrieve from a knowledge base, fall back to web search, or generate directly — then ranks N candidates by semantic similarity before returning the best answer.

```
Query → route → [retrieve | web search | direct] → rank candidates → best answer + confidence + sources
```

`Python` `LangGraph` `FastAPI` `Azure AI Search` `ChromaDB` `Docker` `RAGAS`

---

### 💹 [LLM Fine-tuning for Finance](https://github.com/WilliamDumaszak/llm-finetuning-finance)

> End-to-end LoRA fine-tuning for financial sentiment classification — from dataset prep to Azure deployment.

Fine-tuned a 1B LLM on financial news for 3-class sentiment (`negative`, `neutral`, `positive`) using instruction-style formatting and TRL. Includes base vs. tuned evaluation, LoRA merge, FastAPI serving with confidence scores, and Azure deployment via Terraform + GitHub Actions.

```
financial_phrasebank → LoRA training → evaluate → merge → serve (FastAPI) → deploy (Azure)
```

`Python` `LoRA` `TRL` `HuggingFace` `FastAPI` `Docker` `Terraform` `Azure` `MLflow`

---

### 📡 [LLM Serving & Monitoring](https://github.com/WilliamDumaszak/llm-serving-monitoring)

> Production LLM serving stack with RAG retrieval, full observability, and scheduled ingestion.

Demonstrates an end-to-end production environment: retrieval via Elasticsearch or Azure AI Search, generation via Ollama/vLLM/Azure OpenAI, interaction persistence in PostgreSQL, real-time metrics in Prometheus + Grafana, and scheduled document ingestion via Airflow.

```
Airflow ingestion → Elasticsearch index → /query API → LLM → PostgreSQL → Prometheus/Grafana
```

`Python` `Elasticsearch` `Ollama` `vLLM` `PostgreSQL` `Prometheus` `Grafana` `Airflow` `Kubernetes` `Docker`

---

## Tech Stack

| Area | Tools |
|---|---|
| **LLM / ML** | HuggingFace Transformers, TRL, LoRA, LangGraph, RAGAS, MLflow |
| **Serving** | FastAPI, Ollama, vLLM, Azure OpenAI |
| **Retrieval** | Elasticsearch, Azure AI Search, ChromaDB |
| **Infrastructure** | Docker, Kubernetes, Terraform, GitHub Actions |
| **Observability** | Prometheus, Grafana, Airflow |
| **Cloud** | Azure (AI Search, Container Apps, ML, AKS) |

---

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=WilliamDumaszak&show_icons=true&theme=dark&hide_border=true&count_private=true)

</div>

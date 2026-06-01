# Retrieval-Augmented Generation Powered by SAP Gen AI Hub and SAP AI Core Document Grounding

<!-- [![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/sap-genai-hub-with-sap-hana-cloud-vector-engine)](https://api.reuse.software/info/github.com/SAP-samples/sap-genai-hub-with-sap-hana-cloud-vector-engine) -->

## 📝 Description

In this use case, we explore how to build a **Retrieval-Augmented Generation (RAG)** pipeline using **SAP AI Core Document Grounding** and the **SAP Generative AI Hub Orchestration Service**.

The goal is to equip you with the knowledge and skills to handle structured and semi-structured data and build efficient AI-powered search applications — without managing a separate vector database.

### What you will build

- **Index** a product catalog CSV into a **SAP AI Core Document Grounding** collection (vector store managed by SAP AI Core)
- **Retrieve** semantically relevant product records using the Document Grounding Vector API
- **Generate** natural language answers using the **Orchestration Service** (grounding + LLM in a single API call)
- **Deploy** a Flask-based REST API to Cloud Foundry that answers product queries via RAG

### Architecture

```
User Query
    │
    ▼
Orchestration Service
    ├── Grounding Module  ──►  Document Grounding (Vector Search)
    │                              └── products-it-accessories collection
    └── LLM Module        ──►  gpt-4o-mini
    │
    ▼
Answer
```

### Notebooks

| Notebook | Description |
|---|---|
| `1-rag_with_document_grounding.ipynb` | End-to-end RAG with SAP AI Core Document Grounding (primary) |
| `1-rag_with_hana_vectordb.ipynb` | Alternative RAG implementation using SAP HANA Cloud vector engine |

### Service (`product_search_rag_python-srv/`)

A production-ready Flask service with two interchangeable backends:

| | Document Grounding (default) | HANA Cloud (optional) |
|---|---|---|
| **Vector store** | SAP AI Core Document Grounding | SAP HANA Cloud |
| **Server** | `server_dg.py` | `server.py` |
| **Embed script** | `embed_product_catalog_dg.py` | `embed_product_catalog.py` |

See [`product_search_rag_python-srv/README.md`](product_search_rag_python-srv/README.md) for setup and deployment instructions.

## Known Issues
No known issues.

## Contributing
We currently do not accept community contributions.

## License
Copyright (c) 2024 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.
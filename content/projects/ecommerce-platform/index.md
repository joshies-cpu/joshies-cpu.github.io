---
title: "Enterprise Hybrid-RAG Platform"
date: 2025-10-01
summary: "Privacy-first AI backend combining static documentation with real-time data streams using Llama 3 and Chroma DB, achieving <500ms query latency."
tags:
  - Full-Stack
  - Backend
  - AI
  - RAG
tech_stack:
  - Python
  - FastAPI
  - Chroma DB
  - Docker
  - Llama 3
  - Ollama
links:
  - type: github
    url: https://github.com/joshies-cpu
    label: Code
featured: true
status: "Completed"
role: "Solo Developer"
duration: "3 months"
highlights:
  - "<500ms query latency achieved"
  - "Hybrid search over static + live data"
  - "Fully local, privacy-first AI deployment"
  - "Scalable ETL pipeline for unstructured PDFs"
---

A privacy-first, production-grade AI backend that synthesizes static documentation with high-frequency real-time data using a custom Hybrid RAG architecture.

## Overview

Designed and built an end-to-end AI platform that allows users to query both indexed knowledge bases (PDFs, source code) and live system metrics through a unified interface — all without sending data to any external API.

## Key Features

### Hybrid Retrieval Engine
- **Static Knowledge Base** — Unstructured PDFs and source code indexed into a Chroma DB vector store using `pdfminer.six`
- **Real-Time Data Watcher** — Python-based watcher ingesting live system metrics and logs into the retrieval pipeline
- **Custom Hybrid Search** — Blends vector similarity search with keyword filtering for optimized, context-aware retrieval

### AI Backend
- **Ollama + Llama 3** — Fully local LLM inference with no cloud dependency
- **FastAPI** — High-performance async REST API for chat and query endpoints
- **Docker** — Containerized deployment for reproducibility and portability

### ETL Pipeline
- Automated ingestion of PDF documents using `pdfminer.six`
- Chunking, embedding, and upserting into Chroma DB vector collections
- Real-time metric streaming into the knowledge pipeline

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                  FastAPI Backend                     │
│                                                     │
│  ┌──────────────┐      ┌────────────────────────┐  │
│  │ ETL Pipeline │      │  Real-Time Data Watcher│  │
│  │ (pdfminer)   │      │  (live metrics/logs)   │  │
│  └──────┬───────┘      └──────────┬─────────────┘  │
│         │                         │                 │
│         ▼                         ▼                 │
│  ┌──────────────────────────────────────────────┐  │
│  │            Chroma DB Vector Store             │  │
│  │       (static + real-time embeddings)         │  │
│  └───────────────────┬──────────────────────────┘  │
│                      │                              │
│         ┌────────────▼────────────┐                 │
│         │  Hybrid Search Engine   │                 │
│         └────────────┬────────────┘                 │
│                      │                              │
│         ┌────────────▼────────────┐                 │
│         │   Ollama (Llama 3)      │                 │
│         │   Local LLM Inference   │                 │
│         └─────────────────────────┘                 │
└─────────────────────────────────────────────────────┘
```

## Performance

- **Query Latency**: Achieved **<500ms** end-to-end response time including retrieval + LLM inference
- **Privacy**: 100% local — no data leaves the machine
- **Scalability**: ETL pipeline handles large PDF corpora and continuous real-time ingestion

## Challenges & Solutions

### Challenge: Combining Static and Live Data
**Problem**: Vector stores are typically static; live data needed to be queryable in near real-time.

**Solution**: Built a Python Real-Time Data Watcher that continuously ingests and embeds live metrics, upserting them into Chroma DB on configurable intervals.

### Challenge: Retrieval Accuracy
**Problem**: Pure vector search lost precision for keyword-heavy queries.

**Solution**: Designed a custom Hybrid Search algorithm combining dense vector retrieval with BM25-style keyword scoring, improving answer quality significantly.

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | FastAPI |
| LLM | Llama 3 via Ollama |
| Vector DB | Chroma DB |
| ETL | pdfminer.six, custom Python |
| Container | Docker |
| Language | Python |

---

**Status**: ✅ Completed  
**GitHub**: [View on GitHub](https://github.com/joshies-cpu)

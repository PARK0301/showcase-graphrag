# PDF GraphRAG Document QA — Case Study

> **CityUHK Final Year Project (FYP2026)** · Team project · Case study (summary only)  
> Original repo is team-owned; this page documents the system design and outcomes for portfolio use.

## Problem

Users ask questions over long PDFs and need answers that are **grounded in evidence**, not free-form hallucination — plus a way to **see why** an answer is supported.

## Solution

A **hybrid GraphRAG** pipeline that is:

- **retrieval-first**
- **answer-grounded**
- **graph-explained**

It does not only return an answer. It also returns:

- grounded evidence **citations**
- a **local knowledge graph** built from the final evidence
- optional debug inspection for graph assembly

The graph shown in the UI is **not** the full document graph — it is a smaller local graph that explains support for the final answer.

## Architecture

```text
PDF ingest
   ├─ text index
   ├─ vector index
   └─ document-level knowledge graph
            │
            ▼
   question classify → retrieve (text + vector + graph)
            │
            ▼
   rerank → grounded answer → citation align
            │
            ▼
   local answer graph (from final evidence)
```

## Stack

- **Python**
- retrieval + vector + graph signals
- grounded generation with citation alignment
- UI for answers, citations, and local graph inspection

## Outcome

A working FYP system oriented around **explainable PDF QA**: retrieve first, answer from evidence, then visualize a local graph of that evidence.

## Note on source

Full source lives in the team FYP repository (`minseo1103/FYP2026`, private until the team opens it). This showcase is intentionally README-only.

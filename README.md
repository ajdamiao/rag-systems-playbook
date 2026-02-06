# RAG Systems Playbook (Semantic Search)

An end-to-end **document semantic search** pipeline:
1) ingest files → 2) chunk text → 3) generate embeddings → 4) store in a vector database → 5) **query and get the most relevant document passages** (snippets + metadata + source references).

✅ **No LLM / no “AI answering” here** — this repo only retrieves the best-matching chunks from your documents.

---

## What this repo does

- **Ingest files** (PDF / TXT / MD — extendable)
- **Chunking** (size/overlap configurable + metadata per chunk)
- **Embeddings** (OpenAI by default, provider adapters supported)
- **Vector DB storage** (pgvector or Qdrant)
- **Semantic search** (top-k, filters, score + source info)
- **CLI** to ingest and search

---

## How it works

```mermaid
flowchart LR
  A[Files: PDF/MD/TXT] --> B[Loader/Parser]
  B --> C[Chunker]
  C --> D[Embedding Model]
  D --> E[(Vector DB)]
  Q[Search query] --> R[Embed query]
  R --> E
  E --> S[Top-K chunks]
  S --> O[Results: text + score + source]

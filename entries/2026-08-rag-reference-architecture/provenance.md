# Provenance — RAG reference architecture

> 2026-08 · AnyCap image production (nano-banana-pro, T1 full-generated branch)

## Why synthetic

The goal was a **publishable** architecture-diagram case study. Real architectures leak system names and topology even after redaction — so the subject is a synthetic reference stack chosen to be generically useful: a small self-hosted RAG chat application.

## Frozen fact graph (step 0–1)

Viewer question: "RAG 小应用的请求经过哪些组件？" Takeaway: Web → API → (queue | vector DB | object storage | LLM).

```
nodes:  Next.js Web · FastAPI · Redis Queue · Postgres pgvector · S3 Storage · LLM API
edges:  Next.js Web → FastAPI (down)
        FastAPI → Redis Queue (right)
        FastAPI → Postgres pgvector (down)
        FastAPI → S3 Storage (down)
        FastAPI → LLM API (down)
label whitelist: exactly the six node names above; no other text allowed
grammar: 3-layer (client / service / data+AI), 16:9, dark plate
```

## Generation (one shot)

Model: nano-banana-pro. Prompt structured as: layer grammar → node inventory with exact labels → edges with direction → style (cyan #19C7F3 boxes, amber #F6A91A arrows, dark navy #0B0B12) → constraint ("every label exactly as listed — no extra text, no watermark, no legend").

## Audit transcript (image-read)

- Labels found: exactly the six whitelist entries, zero missing/duplicated/misspelled
- Arrows: all five present with correct direction; the `LLM API` arrow routes via the `S3 Storage` path rather than a direct drop — direction correct, routing noted as a cosmetic quirk, accepted
- Pseudo-text / watermark / extra legend: none
- **Result: AUDIT-PASS (first candidate)**

## Honest limitations

- Arrow routing into `LLM API` shares the `S3 Storage` channel for a segment — acceptable for a teaching figure; an exact-topology requirement would have switched to the hybrid/deterministic branch.
- 6 nodes is near the sweet spot; the skill caps generated figures at ~12 nodes before splitting views.

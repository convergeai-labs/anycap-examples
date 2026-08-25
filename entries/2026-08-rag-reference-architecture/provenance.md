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

## Multi-view expansion (2026-08, second pass)

The single figure grew into a coordinated 4-view set over one frozen fact model (8 nodes shared across views):

| View | Grammar | Nodes | Branch | Audit |
|---|---|---|---|---|
| v1 overview | layered, full topology | 8 | **deterministic SVG** after 3 failed T1 audits | see below |
| v2 query flow | horizontal flow + step numbers | 6 | T1 (nano-banana-pro) | PASS, 1st candidate |
| v3 ingest pipeline | horizontal pipeline + side loop | 6 | T1 | PASS, 1st candidate |
| v4 deployment | container boundary | 9 labels | T1 | PASS, 1st candidate |

### v1 audit trail (why it retreated)

- **r1**: extra row labels (`Client`/`Services`/`Data & AI`), missing `Worker→Postgres`, extra `FastAPI→Embedding API` → FAIL
- **r2** (failures named in prompt, "no row titles"): labels perfect; `Worker→Postgres` still missing, two stray `Worker→FastAPI` arrows → FAIL
- **r3** (layout-driven fix: Worker placed directly above Postgres to shorten the arrow): `Web→FastAPI` missing, stray `Web→Worker` → FAIL

Three rolls, each exactly one arrow off, a different arrow each time — the fix-one-break-another carousel. Per the branch rule, v1 retreated to a hand-authored deterministic SVG (`views/v1-overview.svg`): all 8 labels and 8 arrows exact by construction, editable source preserved.

### Measured takeaway

T1 full generation with inline labels is reliable up to **~6 nodes / ~6 edges**; at 8×8 the per-roll arrow drift makes further rolls zero-expectancy. Layout-first prompt fixes help but don't move the ceiling.

## Style v2 (2026-08-21): editorial restyle via the deterministic branch

User feedback on the dark set: "和 mermaid 没区别，而且颜色比较臭" — dashboard chrome carries zero style information. The grammar-gallery entry had already been regenerated in the editorial visual language (warm-white #FAFAF7, navy #1E3A5F structure, meaning-carrying accents, bold Chinese title + takeaway caption, text-only cards).

This entry followed — with a twist: **the AnyCap credit balance hit zero mid-task** (`INSUFFICIENT_CREDIT` on both image generation and image-read). So the editorial restyle was executed entirely through the **deterministic branch**: all five figures (main + 4 views) were hand-authored as SVGs in the editorial language and rendered with resvg.

That is not a compromise, it is the skill working as designed:

- exact topology AND a frozen editorial style were both hard requirements → deterministic was the only branch that guarantees both;
- every figure ships its editable SVG source next to the PNG — truth layer and explanation layer in one artifact;
- the v1 dark figures are archived in `v1-dark-dashboard/` for before/after comparison.

Fonts: PingFang SC via `-apple-system` stack; rendered locally with `@resvg/resvg-js-cli`.

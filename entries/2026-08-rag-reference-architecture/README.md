# RAG reference architecture — labeled system diagram

**Final asset**: [`architecture-final.png`](architecture-final.png) (16:9, audit PASS on first candidate)

A teaching-grade architecture diagram for a small self-hosted RAG chat application — a **synthetic reference system**, deliberately not any real deployment: `Next.js Web → FastAPI → Redis Queue / Postgres pgvector / S3 Storage / LLM API`.

![final](architecture-final.png)

## Why this entry exists

Architecture diagrams are the highest-risk figures to produce with an image model: they carry **exact labels and arrow directions**, and they leak internal system structure if you feed real ones. This entry demonstrates the two disciplines that make it work:

1. **Sanitize the fact graph first** — the subject is a synthetic stack (a generic Python/FastAPI + Next.js RAG app), so the diagram is shareable by construction. No internal system was ever involved.
2. **Audit labels, not vibes** — the vision gate checked every label against an exact whitelist and every arrow direction against the spec. First candidate passed.

## How it was made (agent + skill)

Produced with [anycap-architecture-diagrams](https://github.com/convergeai-labs/anycap-skills/blob/main/skills/anycap-architecture-diagrams/SKILL.md):

1. **Fact graph frozen in text** — 6 nodes, 5 edges, exact label whitelist. Nothing else allowed in the image.
2. **One structured prompt** — layer grammar → node inventory with exact labels → edges with direction → style → "no extra text".
3. **One image-read audit** — labels verbatim, arrows by direction, pseudo-text scan → `AUDIT-PASS`.
4. Done in a single generation. The skill's rule for when it doesn't go this well: one concrete failure → regenerate naming the failure; two failed audits → switch to the hybrid branch (no-text plate + deterministic labels).

The full fact graph, prompt, and audit transcript are in [`provenance.md`](provenance.md).

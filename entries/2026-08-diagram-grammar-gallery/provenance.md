# Provenance — diagram grammar gallery

> 2026-08 · AnyCap image production (nano-banana-pro ×3, gpt-image-2 ×2 after a provider 400) · single batch audit

## Subject: synthetic PR review bot

Chosen to be shareable by construction — no real deployment involved:

```
components: GitHub · Webhook Queue · Review Agent · LLM API · Rules Store · PR Comments
flow: GitHub PR event → Webhook Queue → Review Agent → LLM API → findings → PR Comments
rules: Rules Store → Review Agent
```

## Grammar selection (viewer question → grammar)

| Figure | Viewer question | Grammar | Nodes | Model | Audit |
|---|---|---|---|---|---|
| g1 | What exists, where's the boundary? | context + trust-boundary box | 6 + zone label | nano-banana-pro | PASS, 1st |
| g2 | How does one request unfold? | sequence (4 lifelines, 5 numbered steps) | 4 + 5 step labels | nano-banana-pro | PASS, 1st |
| g3 | Which states/transitions are legal? | state machine | 4 | nano-banana-pro | PASS, 1st |
| g4 | Where does data cross trust? | data-flow with two zones | 6 + 2 zone labels | gpt-image-2 (fallback) | PASS, 1st |
| g5 | How does the agent keep running? | control loop | 4 | gpt-image-2 (fallback) | PASS, 1st |

## Audit transcript (one batch image-read call, 5 files)

```
g1: AUDIT-PASS
g2: AUDIT-PASS
g3: AUDIT-PASS
g4: AUDIT-PASS
g5: AUDIT-PASS
```

Each figure was audited against its own whitelist: exact label sets, zone membership, arrow inventory with directions, and pseudo-text scan. Spot-checked visually by the human after the batch audit.

## Incidents & notes

- **Provider hiccup**: nano-banana-pro returned `INVALID_PARAM` (Vertex 400) twice mid-batch; g4/g5 fell back to gpt-image-2 with identical prompts and passed. Branch selection is about topology risk, not model loyalty.
- **g2's prompt contained a leftover self-correction fragment** ("2 'enqueue' stays... no —") and still passed; noted as a reminder to freeze prompt text before sending, not as a practice to repeat.
- All five figures sit inside the measured sweet spot (≤6 nodes) — consistent with the ceiling measured in [2026-08-rag-reference-architecture](../2026-08-rag-reference-architecture/), where 8×8 drifted one arrow per roll.

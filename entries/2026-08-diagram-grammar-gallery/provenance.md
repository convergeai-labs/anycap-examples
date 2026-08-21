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

## Style v2 (2026-08-21): dark dashboard → editorial

The v1 set (archived in `v1-dark-dashboard/`) used dark navy + saturated cyan + amber. User feedback: **"和 mermaid 没区别，而且颜色比较臭"** — the style carried zero information and looked like a themed Mermaid export.

v2 regenerated all five figures in the editorial visual language used by local technical-report diagrams:

- warm-white canvas (#FAFAF7), navy (#1E3A5F) structure, accents (teal/orange/green) only where they carry meaning
- bold Chinese title top-left + one-line takeaway caption at the bottom
- text-only cards — **no provider logos/icons** (v2-r1 of g1 had a GitHub octocat and an OpenAI-ish swirl on 'LLM API'; regenerated with "NO brand logos, NO icons")
- Chinese labels (short) + exact English IDs where they help (GitHub / LLM API / Webhook / PR / Diff / Agent)

**Audit (batch image-read): g1–g5 all AUDIT-PASS on first candidate of v2** (g1 needed r2 for the icon issue — a style failure, not a label failure). Human spot-checked g2/g5 visually.

Models: nano-banana-pro for g1–g3 (strong short Chinese labels); it hit 429 quota mid-batch, so g4/g5 went to gpt-image-2 — same style prompt, same audit bar.

**Lesson folded back into the skill**: diagram style is part of the frozen contract, not an afterthought — and "looks like Mermaid with a theme" is a reject reason even when every label is correct.

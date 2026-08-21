# Diagram grammar gallery — one system, five grammars

Five figures, one synthetic system (a PR review bot: GitHub webhook → queue → review agent → LLM), each answering a **different viewer question** with a different grammar.

**Style note (v2):** the first version of this set used dark-navy "dashboard chrome" styling — functional but indistinguishable from a Mermaid export. The current set follows an **editorial visual language** instead: warm-white canvas, navy structure, accent colors only where they carry meaning, bold Chinese title + bottom takeaway caption. The dark v1 figures are kept in [`v1-dark-dashboard/`](v1-dark-dashboard/) as the before/after evidence.

| | |
|---|---|
| ![g1](g1-context-boundary.png) | ![g2](g2-sequence.png) |
| **g1 系统上下文图** — 什么存在、边界在哪：队列与 Agent 圈进「自有基础设施」虚线框，外部只剩 GitHub / LLM API | **g2 时序图** — 一次请求如何展开：4 条生命线、①–⑤ 编号步骤、「结论」虚线返回 |
| ![g3](g3-state-machine.png) | ![g4](g4-data-flow-trust.png) |
| **g3 状态机** — 哪些状态和迁移合法：排队→运行→已发布/失败→重试 | **g4 数据流 + 信任边界** — 数据在哪移动/越界：出界的 Diff 箭头加粗标橙 |
| ![g5](g5-control-loop.png) | |
| **g5 控制环** — agent 如何持续运转：观察→计划→执行→验证 顺时针闭环 | |

## How it was made (agent + skills)

Produced with [anycap-architecture-diagrams](https://github.com/convergeai-labs/anycap-skills/blob/main/skills/anycap-architecture-diagrams/SKILL.md), applying the viewer-question→grammar mapping from the local `image-gen-system` routing taxonomy:

1. **One frozen fact model** for the synthetic PR review bot — 6 component names, reused verbatim across all five figures.
2. **One grammar per figure**, chosen by viewer question (what exists / how a request unfolds / which states are legal / where data crosses trust / how the loop runs).
3. **Five structured prompts**, each carrying its figure's exact label whitelist and arrow spec.
4. **One batch image-read audit** covering all five: `AUDIT-PASS × 5`, first candidates. (g2/g3 via nano-banana-pro; the model backend hiccuped mid-batch, so g4/g5 fell back to gpt-image-2 — the audit doesn't care which model, only whether the labels are right.)

Full fact graphs, prompts, and the audit transcript: [`provenance.md`](provenance.md).

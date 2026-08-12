# anycap-examples

用 [AnyCap](https://anycap.ai) 做出的真实作品。每个条目都交付最终资产、创作故事和完整 provenance——brief、候选、门禁记录，以及胜出的理由。

[English version → README.en.md](README.en.md)

所有作品都由「人 + agent」组合使用 [anycap-skills](https://github.com/convergeai-labs/anycap-skills) 中的 playbook 完成：人负责 brief、品味和关键判断；agent 负责生成过门禁的候选、搭决策板、记 provenance。

<p align="center">
  <img src="assets/hero.png" width="720" alt="人与 agent 一起评审 logo 草稿墙">
</p>

---

## 🌈 convergeai-labs org 头像 · 彩虹环

<p align="center">
  <img src="entries/2026-08-convergeai-labs-avatar/avatar-final.png" width="320" alt="convergeai-labs 头像——彩虹环">
</p>

[convergeai-labs](https://github.com/convergeai-labs) 的 org 头像。构图借用母品牌的 7 椭圆径向圆环——每颗椭圆染一色彩虹。7 颗椭圆、7 个色相：**整个产品家族（每个产品一个色相）收进一个环**。官方 logo 严格单色，所以亲缘一目了然、又绝无混淆。

经得起真实考验——GitHub 头像只显示 32–44px：

<p align="center">
  <img src="entries/2026-08-convergeai-labs-avatar/avatar-final.png" width="64" alt="64px"> &nbsp;
  <img src="entries/2026-08-convergeai-labs-avatar/avatar-final.png" width="44" alt="44px"> &nbsp;
  <img src="entries/2026-08-convergeai-labs-avatar/avatar-final.png" width="32" alt="32px">
</p>

### 创作过程

它前面站着 17 个候选：6 个原创构图（汇聚弧线→星芒、轨道星座、彗尾旋汇、点阵方框、光圈叶片、涟漪），5 个 i2i 换色，5 个官方圆环衍生——每一个都过了拒绝文字、水印甚至图标模板描边的 vision 门禁。彩虹环第一版就因一丝模板描边被拦下，干净的重生成版才出厂。

| 部分亚军 | | |
|---|---|---|
| <img src="entries/2026-08-convergeai-labs-avatar/variants/v1-converging-spark.png" width="160" alt="汇聚星芒"> | <img src="entries/2026-08-convergeai-labs-avatar/variants/c3-white-violet-core.png" width="160" alt="白+紫芯"> | <img src="entries/2026-08-convergeai-labs-avatar/variants/d3-ring-spark.png" width="160" alt="白环紫芯"> |
| 汇聚星芒 | 白+紫芯 | 白环+紫芯星芒 |

📖 **完整故事**：[entries/2026-08-convergeai-labs-avatar/](entries/2026-08-convergeai-labs-avatar/)

---

## ✨ kt-aicoding logo · 像素星芒

<p align="center">
  <img src="entries/2026-08-kt-aicoding-pixel-spark/logo-final.png" width="320" alt="kt-aicoding logo——像素星芒">
</p>

开发者工具组织 [kt-aicoding](https://github.com/kt-aicoding) 的全新 logo。粗颗粒 8-bit 像素星——青色块配琥珀点缀。**独占性强**（不要轨道原子、不要无限环、不要火箭），像素硬边在 32px 下依然干脆。

<p align="center">
  <img src="entries/2026-08-kt-aicoding-pixel-spark/logo-final.png" width="64" alt="64px"> &nbsp;
  <img src="entries/2026-08-kt-aicoding-pixel-spark/logo-final.png" width="44" alt="44px"> &nbsp;
  <img src="entries/2026-08-kt-aicoding-pixel-spark/logo-final.png" width="32" alt="32px">
</p>

### 创作过程

第一轮——围绕旧 logo 元素（括号/节点/工具）的 5 个候选——被整体否决。agent 没有打磨被否方案，而是跳进**完全不相交的概念空间**（像素、键帽、光标、无限环、火箭），像素星凭独占性胜出。交付阶段抓到两个真实 bug：不透明白角（flood-fill 成透明）和 GitHub camo 图片缓存（`?v=2` 破除）。

| 部分亚军 | | |
|---|---|---|
| <img src="entries/2026-08-kt-aicoding-pixel-spark/variants/v2-module-brackets.png" width="160" alt="模块括号"> | <img src="entries/2026-08-kt-aicoding-pixel-spark/variants/v7-spark-keycap.png" width="160" alt="星火键帽"> | <img src="entries/2026-08-kt-aicoding-pixel-spark/variants/v9-infinity-ribbon.png" width="160" alt="无限环带"> |
| 模块拼图括号 | 星火键帽 | 无限环带 |

📖 **完整故事**：[entries/2026-08-kt-aicoding-pixel-spark/](entries/2026-08-kt-aicoding-pixel-spark/)

---

## 🏗 RAG 参考架构图 · 一次通过审计的系统图

<p align="center">
  <img src="entries/2026-08-rag-reference-architecture/architecture-final.png" width="640" alt="RAG 参考架构图">
</p>

一张教学级架构图：**合成参考系统**（自建 RAG 小应用：Next.js Web → FastAPI → Redis Queue / Postgres pgvector / S3 Storage / LLM API），刻意不对应任何真实部署——架构图公开的最大风险不是文字，而是系统结构本身。

创作过程演示了两条纪律：**先脱敏事实图再生成**（从合成栈出发，天然可分享）；**审计标签而非氛围**（vision 门禁逐字核对 6 个标签白名单 + 逐条核对 5 个箭头方向，首个候选即 `AUDIT-PASS`）。

📖 **完整故事**：[entries/2026-08-rag-reference-architecture/](entries/2026-08-rag-reference-architecture/)

---

## 方法论

品牌标用 [anycap-brand-mark-lab](https://github.com/convergeai-labs/anycap-skills/blob/main/skills/anycap-brand-mark-lab/SKILL.md)：brief → 构图候选 → 无文字 vision 门禁 → i2i 换色 → 32px 决策板 → 交付处理 → provenance。

架构图用 [anycap-architecture-diagrams](https://github.com/convergeai-labs/anycap-skills/blob/main/skills/anycap-architecture-diagrams/SKILL.md)：事实图脱敏 → 冻结标签白名单 → 结构化 prompt 生成 → image-read 逐标签审计 → provenance。

## 条目

| 条目 | 资产 | 一句话 |
|---|---|---|
| [2026-08-convergeai-labs-avatar](entries/2026-08-convergeai-labs-avatar/) | GitHub org 头像 | 借母品牌几何的 7 椭圆环，每颗椭圆染一色彩虹 |
| [2026-08-kt-aicoding-pixel-spark](entries/2026-08-kt-aicoding-pixel-spark/) | GitHub org logo | 8-bit 像素星——独占的肌理，小尺寸反脆弱 |
| [2026-08-rag-reference-architecture](entries/2026-08-rag-reference-architecture/) | 架构图 | 合成 RAG 参考系统，首个候选即通过标签审计 |

许可证：CC BY 4.0

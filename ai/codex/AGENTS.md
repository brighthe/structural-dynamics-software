# AGENTS.md

本文件指导 Codex 在本仓库中工作。核心工作是中文技术文档的撰写、修改与审校，不是写代码。

## Codex 工作流程

基础规则在本文件；专项写作与审校流程见以下说明：

| 工作项 | 说明文件 | 何时使用 |
| --- | --- | --- |
| 写作风格 | [instructions/house-style.md](instructions/house-style.md) | 撰写、修改、续写或审阅 `docs/` 下结构动力学文档时阅读并遵循。 |
| 技术正确性审校 | [instructions/dynamics-reviewer.md](instructions/dynamics-reviewer.md) | 需要技术正确性审校时，按其中清单逐项检查并输出问题清单。 |
| 术语一致性巡检 | [instructions/terminology-guardian.md](instructions/terminology-guardian.md) | 需要术语一致性巡检时，按其中流程对照“术语桥”。 |
| 文档审校流程 | [instructions/review-doc.md](instructions/review-doc.md) | 用户要求“技术审校”“review-doc”或类似任务时使用。 |
| 术语巡检流程 | [instructions/term-check.md](instructions/term-check.md) | 用户要求“术语巡检”“term-check”或类似任务时使用。 |

这些文件是 Codex 工作说明，按任务需要主动读取并执行。

## 仓库定位

`structural-dynamics-software` 是大连理工大学结构动力学求解器采购项目的文档库。项目为国产求解器研发三个可嵌入的算法库模块：

- **A 包**：结构模态分析（固有频率、振型；广义特征值问题）。
- **B 包**：结构动力响应分析（确定性载荷下的时域/频域响应）。
- **C 包**：结构随机振动分析（功率谱、非平稳时域、响应谱）。本仓库投标的是 C 包。

三包共享同一套有限元建模底座（混合网格 -> 单元/材料/连接/边界 -> 组装 $\mathbf M$/$\mathbf C$/$\mathbf K$），数据上构成“模态 -> 确定性响应 -> 随机响应”的链条。

## 仓库文档地图

### 入库撰写文档

`docs/` 下的 Markdown 文件是主要工作对象。

| 文档 | 角色 |
| --- | --- |
| [docs/三包知识框架.md](../../docs/三包知识框架.md) | 知识本身：从有限元流程出发的三包原理与算法直觉。只讲知识，不讲招标条款。含大量 LaTeX 与 NASTRAN 卡片名。 |
| [docs/procurement/总体方案及功能要求、方案适用性及技术先进性说明.md](../../docs/procurement/总体方案及功能要求、方案适用性及技术先进性说明.md) | C 包投标方案：对应招标第四章“十二、总体方案…说明”。受 ★/▲ 指标硬约束，必须逐条响应。 |
| [docs/procurement/招标文件要点解读.md](../../docs/procurement/招标文件要点解读.md) | 招标总览：预算、时间节点、知识产权、兼投兼中、综合评分法等关键信息。回答“要不要投、怎么投”。 |
| [docs/procurement/技术需求详解.md](../../docs/procurement/技术需求详解.md) | 第三章逐条详解：对应招标《用户需求书》，给出 A/B/C 全部 ★/▲ 指标与评分拆解。回答“能做什么、要补什么、哪个包划算”。 |

四篇文档的分工是：要点解读（总览）-> 技术需求详解（招标第三章逐条 + 评分）-> 知识框架（纯知识原理）-> 总体方案（C 包应答）。前两篇是对招标的解读，后两篇是我方产出；知识框架只讲知识，招标条款、评分、投包策略一律落在采购文档。

### 参考原件

以下文件仅作参考与检索，不要把其内容大段复制进入库文档：

| 文件 | 角色 |
| --- | --- |
| `docs/procurement/结构动力学软件模块采购  招标文件（定稿）.docx` / `.pdf` | 招标原件（DUTAWZ-2026097），一切要求的源头。 |
| `docs/（正本）标书响应文件-国创.pdf` | 他方标书样例，供投标文件格式和写法参考，与本项目技术内容无关。 |

## 写作约定

- **语言**：全中文正文。中英混排时，半角标点用于公式与代码，中文正文使用全角标点。
- **LaTeX**：行内用 `$...$`，独立公式块用 `$$...$$`。矩阵/向量用粗体（`\mathbf`），保持与现有文档一致，如 $\mathbf M$、$\mathbf K$、$\boldsymbol\phi$。`$` 与 `$$` 必须成对。
- **术语**：以 [docs/三包知识框架.md](../../docs/三包知识框架.md) 的“术语桥”表（约第 23-41 行）为唯一权威。建立“力学术语 ↔ 数学 ↔ NASTRAN 卡片名”三方对应，不要另立术语。
- **★/▲ 指标**：★ 为关键指标（不满足即废标）；▲ 为重要指标（完全满足或正偏离才得分，部分满足不得分）。响应原则是：3★ 全部无偏离满足；20▲ 全部“完全响应”，逐条配齐“算法实现 + 原理描述 + 算例测试报告/截图”三位一体。
- **交叉引用**：用相对路径 Markdown 链接，例如 `[技术需求详解](procurement/技术需求详解.md)`。

## 家族写作风格

撰写或修改 `docs/` 下文档时，使新内容与现有文档保持一致：

- 从有限元流程出发讲知识：先建立“建模 -> 组装 -> 求解”的锚点，再引入新概念。
- 解释“为什么”而非只罗列“是什么”。每个算法尽量给出核心直觉。
- 工程价值用真实案例支撑，但案例的物理解释必须准确。
- 行文凝练、有判断力，避免空话与营销腔；投标方案可使用“我方”主语，知识框架不用。
- 知识框架只讲知识，招标条款、评分、投包策略一律引到采购文档，不在知识框架展开。
- 不确定的物理或数学结论，宁可标注存疑或建议复核，不要写成定论。

## 技术审校清单

当审校结构动力学文档时，重点检查：

- 运动方程、特征值问题、模态叠加、频域谱关系、响应谱叠加、PEM、Craig-Bampton 等表述是否准确。
- LaTeX 公式是否成对，符号是否与全文一致，矩阵维度、转置、共轭转置（$\mathsf T$ vs $\mathsf H$）是否正确。
- NASTRAN 卡片名与机理是否对应准确：MAT/RBE/RBAR/CWELD/CFAST/SPC/SPCD/MPC 等不要混用。
- SPC/SPCD（单点约束）不等于 MPC（多点约束）；SPCD 是非零强制位移、基础运动激励入口。
- RBE3 是插值/分配，不增刚度；RBE2 是刚性体；CWELD/CFAST 才有物理刚度；CSPLINE 是样条插值耦合。
- 谱移位 $\sigma_s$（量纲频率平方）不等于标准差 $\sigma_u$。
- 结构/滞回阻尼（复刚度 $\mathbf K+i\mathbf K_g$）不等于粘性阻尼 $\mathbf C$，不能全频段等同。
- 响应谱/反应谱不等于功率谱。
- $u_{\mathrm{rms}}=\sqrt{\mathbb E[u^2]}$ 仅在零均值时等于 $\sigma_u$。
- 约束不足时 $\mathbf K$ 因刚体模态半正定；含无质量自由度时 $\mathbf M$ 可能奇异。

## 术语巡检清单

术语一致性以“术语桥”为唯一权威，重点检查：

- 同一概念全文是否统一用词，例如“振型/模态”“固有频率/自然频率”“响应谱/反应谱”。
- 力学术语、数学符号、NASTRAN 卡片名三方对应是否一致。
- $\mathbf M/\mathbf C/\mathbf K$、$\boldsymbol\phi/\boldsymbol\Phi$、$\omega/\lambda$、$\mathbf H(\omega)$、$\mathbf S_{FF}/\mathbf S_{uu}$、$\sigma_s/\sigma_u$ 是否全文统一。
- MAT1/MAT2/MAT8/MAT9、RBAR/RBE2/RBE3、CWELD/CFAST/CSPLINE、SPC/SPCD/MPC、BDF/HDF5 等大小写与写法是否统一。
- 新术语应先补入术语桥，再在正文中稳定使用。

## 工具分区说明

- `ai/claude/CLAUDE.md`、`ai/claude/.claude/`、`ai/claude/.claude-plugin/`、`ai/claude/plugins/structural-docs-kit/` 是 Claude Code 专用配置或插件样板。
- `ai/codex/AGENTS.md` 与 [instructions/](instructions/) 是 Codex 专用规则和流程说明。

## Git 与安全

- 只有用户明确要求时才提交 commit。
- 含预算、投标信息的敏感文档按需放入忽略列表或单独私有保存。
- 招标原件、他方标书样例等参考原件仅作检索参考，不要将其内容大段复制进入库文档。
- `src/` 为后续软件源代码目录，当前为空。

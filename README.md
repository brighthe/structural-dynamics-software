# structural-dynamics-software

结构动力学软件模块项目。本仓库用于管理该项目的全过程材料，包括采购/招标文档、技术资料，以及后续的软件代码实现。

## 目录结构

```
structural-dynamics-software/
├── docs/                 # 项目文档
│   └── procurement/      # 采购 / 招标 / 合同相关文档
├── src/                  # 软件源代码（后续开发）
├── ai/
│   ├── claude/           # Claude Code 专用规则、live 配置与插件样板
│   └── codex/            # Codex 专用规则与说明
├── CLAUDE.md             # Claude Code 薄入口，指向 ai/claude/
├── AGENTS.md             # Codex 薄入口，指向 ai/codex/
└── README.md
```

## 说明

- `docs/procurement/`：招标文件、答疑、技术规格书、合同等采购阶段材料
- `src/`：结构动力学软件模块的源代码
- 敏感文档（含预算、投标信息等）请按需放入忽略列表或单独私有保存，见 `.gitignore`

## AI 辅助工具

本仓库将 Claude Code 与 Codex 的配置分区放置，避免两套工具的规则和插件机制混在一起：

- `ai/claude/`：Claude Code 专用，包括 `CLAUDE.md`、`.claude/`、`.claude-plugin/` 与 `plugins/structural-docs-kit/`。
- `ai/codex/`：Codex 专用，包括完整的 `AGENTS.md` 工作规则、写作风格、技术审校与术语巡检流程。
- 根目录 `CLAUDE.md` 和 `AGENTS.md` 只保留薄入口，分别指向对应分区。

### Claude Code

Claude Code 辅助写作工具包括：

- **技能** `house-style`：撰写/修改文档时自动加载的家族写作风格；
- **子代理** `dynamics-reviewer`（技术正确性深审）、`terminology-guardian`（术语一致性巡检）；
- **命令** `/review-doc`（技术审校）、`/term-check`（术语巡检）。

使用方式：

- 根目录 [CLAUDE.md](CLAUDE.md) 指向完整规则 [ai/claude/CLAUDE.md](ai/claude/CLAUDE.md)。
- live 配置已集中在 `ai/claude/.claude/`；如需让 Claude Code 自动发现命令/子代理/技能，可能需要按 Claude Code 当前机制把该目录放回根目录或在 Claude 侧做对应配置。
- 主动触发审校时，两种方式任选：
  - 敲斜杠命令：`/review-doc`（可带文件名，如 `/review-doc docs/三包知识框架.md`）、`/term-check`（可带聚焦词，如 `/term-check 阻尼`）；
  - 直接说："帮我审一下技术正确性""查一下术语统不统一"——Claude 会自动派对应子代理。

同款能力打包为可复用插件 `structural-docs-kit`（参考样板，默认不自动启用；见 [ai/claude/plugins/structural-docs-kit/README.md](ai/claude/plugins/structural-docs-kit/README.md)）。

### Codex

Codex 规则见根目录 [AGENTS.md](AGENTS.md) 与完整规则 [ai/codex/AGENTS.md](ai/codex/AGENTS.md)。写作风格、技术审校与术语巡检流程见 [ai/codex/instructions/](ai/codex/instructions/)。

---

*大连理工大学 · 结构动力学软件模块项目*

# structural-dynamics-software

结构动力学软件模块项目。本仓库用于管理该项目的全过程材料，包括采购/招标文档、技术资料，以及后续的软件代码实现。

## 目录结构

```
structural-dynamics-software/
├── docs/                 # 项目文档
│   └── procurement/      # 采购 / 招标 / 合同相关文档
├── src/                  # 软件源代码（后续开发）
├── CLAUDE.md             # Claude Code 工作指引（写作约定、文档地图）
├── .claude/             # Claude Code 辅助工具（技能 / 子代理 / 命令）
├── .claude-plugin/      # 本仓库作为插件市场的清单
├── plugins/             # 打包为可复用插件 structural-docs-kit（参考样板）
└── README.md
```

## 说明

- `docs/procurement/`：招标文件、答疑、技术规格书、合同等采购阶段材料
- `src/`：结构动力学软件模块的源代码
- 敏感文档（含预算、投标信息等）请按需放入忽略列表或单独私有保存，见 `.gitignore`

## Claude Code 辅助工具

本仓库配有一套 Claude Code 辅助写作工具，克隆即生效：

- **技能** `house-style`：撰写/修改文档时自动加载的家族写作风格；
- **子代理** `dynamics-reviewer`（技术正确性深审）、`terminology-guardian`（术语一致性巡检）；
- **命令** `/review-doc`（技术审校）、`/term-check`（术语巡检）。

### 使用方式（新会话同样适用）

**前提**：在本仓库目录内启动 Claude Code，以下能力才会加载（在别的目录开会话则不生效）。

- **自动生效，无需操作**：
  - `CLAUDE.md` 会话开始即读入；
  - 让 Claude 写/改 docs 下文档时，`house-style` 自动按家族风格写（也可说"按 house-style 写"）。
- **主动触发审校**，两种等价方式任选：
  - 敲斜杠命令：`/review-doc`（可带文件名，如 `/review-doc docs/三包知识框架.md`）、`/term-check`（可带聚焦词，如 `/term-check 阻尼`）；
  - 直接说："帮我审一下技术正确性""查一下术语统不统一"——Claude 会自动派对应子代理。
- **查看可用项**：敲 `/` 看命令列表，敲 `/agents` 看子代理列表。

详细规则见 [CLAUDE.md](CLAUDE.md)。同款能力打包为可复用插件 `structural-docs-kit`（参考样板，默认不自动启用；见 [plugins/structural-docs-kit/README.md](plugins/structural-docs-kit/README.md)）。

---

*大连理工大学 · 结构动力学软件模块项目*

# structural-docs-kit

面向**结构动力学中文技术文档**与 **C 包投标方案**写作的 Claude Code 插件。把本仓库 `.claude/` 中的能力打包为可在其他仓库复用的插件。

> **定位：参考样板（reference template）。** 本仓库日常使用走 live 配置（`.claude/`）即可；本插件保留下来主要作为"如何把一套命令/子代理/技能打包成可安装插件"的**示例**，以及将来跨仓库复用/分享的起点。**它不保证与 `.claude/` 始终逐字同步**——若要正式分发，请先比对 `.claude/` 取最新版本。

## 包含能力

| 类型 | 名称 | 作用 |
| --- | --- | --- |
| 技能 | `house-style` | 家族写作风格（语气视角、章节结构、符号约定、术语桥、改动纪律），编辑文档时自动加载 |
| 子代理 | `dynamics-reviewer` | 结构动力学技术正确性深审（物理/数学/LaTeX/卡片名机理） |
| 子代理 | `terminology-guardian` | 跨文档术语一致性巡检 |
| 命令 | `/review-doc` | 触发技术审校 |
| 命令 | `/term-check` | 触发术语巡检 |

## 安装

本仓库根目录已是一个本地插件市场（`.claude-plugin/marketplace.json`）。在交互式 `claude` 终端中：

```
/plugin marketplace add .            # 把本仓库注册为插件市场（在仓库根目录执行）
/plugin install structural-docs-kit  # 安装本插件
```

在其他仓库复用时，把市场地址换成本仓库的 git 地址或本地路径即可。

## live 配置 vs 插件包的关系

- `.claude/`（仓库根）是 **live 配置**：克隆本仓库即时生效，无需安装。
- `plugins/structural-docs-kit/`（本目录）是**打包形态**：自包含、可分发，用于在**其他**仓库复用同一套能力。
- 两者内容**当前一致**，但插件作为参考样板留存，**不强制随 live 同步更新**——本仓库内日常使用以 live 为准。

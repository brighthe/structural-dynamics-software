---
description: 跨文档术语一致性巡检（委派 terminology-guardian）
argument-hint: [可选：聚焦的术语或文件，留空则巡检全部 docs]
---

对仓库文档做术语一致性巡检，以"术语桥"为唯一权威。

聚焦范围：$ARGUMENTS

若上面为空，则巡检 `docs/` 下全部文档。

请使用 `terminology-guardian` 子代理执行。拿到不一致清单后向我汇总：按影响排序，每条带 `文件:行号` 与统一建议；若发现术语桥需补充新术语，单独列出。先不要直接改文件，等我确认。

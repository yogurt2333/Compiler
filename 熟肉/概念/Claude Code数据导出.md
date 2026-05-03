---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[跨AI数据打通]]
---

# Claude Code数据导出

## 定义

将 Claude Code 本地存储的对话历史（JSONL 格式）导出为 Markdown 文件的方法和工具集合。

## 核心要点

1. Claude Code 会话存储在 `~/.claude/projects/` 目录的 `.jsonl` 文件中
2. 桌面端无内置导出按钮，需借助第三方工具
3. `claude-conversation-extractor`（Python）: 一键批量导出，`claude-extract --all --format markdown`
4. `cclog`（Go）: TUI 界面浏览，支持在编辑器中直接打开
5. 导出的 Markdown 可直接存入 Obsidian 仓库

## 与其他概念的关系

- [[跨AI数据打通]]：Claude Code 是三大数据源之一
- [[AI 记忆中枢]]：导出的 Markdown 汇入统一记忆层

## 来源

- [[摘要/2026-05-04 - 三端数据打通方案]]

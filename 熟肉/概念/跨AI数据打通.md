---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[AI 记忆中枢]], [[Hermes Agent]], [[Obsidian]], [[Claude Code数据导出]]
---

# 跨AI数据打通

## 定义

将 Claude Code、Hermes Agent、Obsidian 等 AI 工具的历史交互数据统一提取、转换为 Markdown 格式，集中存储于 Obsidian 并通过本地数据库（SQLite FTS5 或向量检索）实现语义搜索的技术方案。

## 核心要点

1. 所有工具的交互记录导出为统一 Markdown 格式
2. Claude Code 历史在 `~/.claude/projects/` 的 `.jsonl` 文件中
3. Hermes 数据分布在 sessions JSON、memories Markdown、state.db SQLite 三处
4. ripgrep (`rg`) 是推荐的轻量全文检索工具
5. 整套流程 100% 本地离线，无隐私风险

## 关键工具

- `claude-conversation-extractor`: Claude Code JSONL → Markdown 导出
- `cclog`: Claude Code 历史 TUI 浏览器
- `ripgrep` / `ag`: 全文搜索 Obsidian 笔记库
- [[MemVerse]]: 进阶多模态记忆框架

## 与其他概念的关系

- [[AI 记忆中枢]]：更宏大的上层架构，跨AI数据打通是其技术实现路径
- [[Hermes 记忆系统]]：单 Agent 内部记忆，打通后成为统一记忆层的数据源之一
- [[Obsidian]]：统一的 Markdown 存储和呈现平台

## 来源

- [[摘要/2026-05-04 - 三端数据打通方案]]

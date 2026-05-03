---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[Hermes Agent]], [[AI 记忆中枢]]
---

# Hermes 记忆系统

## 定义

Hermes Agent 内置的四层记忆架构，通过热记忆（提示词）、冷记忆（SQLite）、技能记忆（Skill 模板）和外部存储的分工协作，实现持久且高效的信息存取。

## 核心要点

1. **热记忆** — `MEMORY.md` + `USER.md`，始终在上下文中，快照式更新，下次会话生效
2. **冷记忆** — SQLite 全量历史，通过 `session_search` 关键词检索，按需加载
3. **技能记忆** — 完成任务后自动生成可复用的 Skill 模板，是 Agent 的"程序性记忆"
4. **外部提供商** — 可选接入 Hindsight（知识图谱）或 Holographic（本地 SQLite 扩展）

## 容量管理

- `MEMORY.md`: 最多 2,200 字符
- `USER.md`: 最多 1,375 字符
- 超限时 AI 需整合或删旧
- 操作: `memory add/replace/remove`

## 与其他概念的关系

- [[Hermes Agent]]：记忆系统是其核心子模块
- [[AI 记忆中枢]]：外部视角的跨工具统一记忆层构想

## 来源

- [[摘要/2026-05-04 - Hermes 记忆系统架构]]

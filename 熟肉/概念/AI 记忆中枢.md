---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[Hermes Agent]], [[Hermes 记忆系统]], [[Obsidian]], [[AgentVault Memory]]
---

# AI 记忆中枢

## 定义

一种将多个 AI 工具（Claude Code、Hermes Agent、网页端对话等）的历史交互统一转换为 Markdown 格式存入 Obsidian，通过 Git 同步实现跨平台知识自动沉淀与复用的架构构想。

## 核心要点

1. 所有 AI 交互历史统一转换为 Markdown 格式
2. Obsidian 作为中心存储层，Git 作为版本管理与同步工具
3. 四层架构：输入层 → 统一记忆层 → 存储层 → 输出层
4. 最终目标：博客自动生成、微信定时推送、知识自动编织

## 关键组件

- **AgentVault Memory**: 跨 AI 工具统一记忆层，直接读取本地历史输出 Obsidian Markdown
- **mindloom**: AI 驱动知识编织，自动整理网页/PDF/想法为结构化 Wiki
- **Hermes Agent**: 自进化 Agent，Skill 自生成 + 长期记忆 + 定时任务
- **ClawBot**: 微信日常对话和触发入口

## 与其他概念的关系

- [[Hermes 记忆系统]]：单 Agent 内部的记忆架构
- AI 记忆中枢：跨工具的外部统一记忆层，是更上层的概念
- [[Obsidian]]：核心存储和呈现平台

## 来源

- [[摘要/2026-05-04 - Hermes Agent 部署与 AI 记忆中枢构想]]

---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[Hermes Agent]], [[Obsidian]]
---

# ClawBot

## 定义

ClawBot 是 Hermes Agent 的官方微信网关通道，使 AI Agent 能够通过微信私聊与用户交互，支持 Markdown 渲染。

## 核心要点

1. 微信中显示为「微信 ClawBot」联系人，通过扫码微信小号登录
2. 支持 Markdown 渲染（标题、列表、代码块、表格），普通微信聊天不支持
3. 配对批准机制 — 首次使用需 `hermes pairing approve weixin [CODE]`
4. 个人使用可设 `allow_all_users true` 跳过配对
5. 官方不支持群聊，需在 gateway setup 中选择 Disable group chats
6. 通过 systemd user service 实现开机自启和后台保活

## 与其他概念的关系

- [[Hermes Agent]]：ClawBot 是其微信网关实现
- [[Obsidian]]：可通过 ClawBot 触发 Hermes 读取 Obsidian 笔记

## 来源

- [[摘要/2026-05-01 - Hermes Agent 部署全记录]]

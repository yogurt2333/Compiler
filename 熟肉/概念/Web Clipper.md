---
type: concept
created: 2026-04-29
updated: 2026-04-29
related: [[LLM Wiki]], [[Obsidian]]
---

# Web Clipper

## 定义
Obsidian 官方浏览器扩展，可将网页内容一键保存为 Obsidian 笔记，支持自定义模板和元数据。

## 核心要点
1. **一键保存**：将网页（包括 AI 对话）直接保存到 Obsidian Vault
2. **模板系统**：支持自定义 frontmatter 元数据和笔记内容格式
3. **变量支持**：使用 `{{变量名}}` 语法注入动态内容（如 `{{content}}`、`{{date}}`）
4. **日期格式化**：使用管道符语法 `{{date|date:"YYYY-MM-DD"}}` 自定义日期格式
5. **手动框选保底**：当页面动态加载内容不完整时，可手动框选区域保存

## 常见问题
- 笔记内容为空：需在「笔记内容」配置中填写 `{{content}}`
- 日期格式报错：使用 `|`（管道符）而非 `:` 连接格式化参数
- 长对话不完整：需先滚动加载到底部，再手动全选复制

## 与其他概念的关系
- [[LLM Wiki]]：Web Clipper 是实现 LLM Wiki 摄入流程的主要工具
- [[Obsidian]]：Web Clipper 是 Obsidian 的配套浏览器扩展

## 来源
- [[摘要/2026-04-29 - 从零搭建LLM Wiki知识库]]

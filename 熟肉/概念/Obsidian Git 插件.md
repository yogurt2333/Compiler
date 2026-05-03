---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[Obsidian]]
---

# Obsidian Git 插件

## 定义

Obsidian 社区插件，实现 Git 仓库的自动 commit 和 push，将笔记变更自动同步到 GitHub 等远程仓库。

## 核心要点

1. 社区插件市场直接安装，与本地 Git 仓库无缝集成
2. 分离式定时器 — commit 和 push 间隔独立配置
3. 核心场景是**定时 auto push**，免去手动 `git push`
4. 首次需手动执行一次 Push 验证认证有效

## 与其他概念的关系

- [[Obsidian]]：运行平台，Git 插件为其提供版本管理和远程同步能力
- OSS + Remotely Save 方案：备选的云同步方案，见 [[Hermes Agent]] 相关摘要

## 来源

- [[摘要/2026-05-04 - Obsidian Git 插件配置]]

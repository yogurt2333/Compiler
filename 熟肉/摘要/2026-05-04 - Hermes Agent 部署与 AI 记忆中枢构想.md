---
type: summary
source: "[[生肉/对话/2026-05-04 0156 - DeepSeek]]"
created: 2026-05-04
related: [[Hermes Agent]], [[AI 记忆中枢]], [[ClawBot]], [[AgentVault Memory]]
---

# 2026-05-04 Hermes Agent 部署与 AI 记忆中枢构想

## 核心内容

比 [[摘要/2026-05-01 - Hermes Agent 部署全记录]] 更完整的部署记录，并首次提出「AI 记忆中枢」开源项目构想——将所有 AI 使用场景（微信、Claude Code、网页端等）打通，统一以 Markdown 存入 Obsidian，通过 Git 同步实现知识的自动沉淀与复用。

## 部署要点（与 05-01 版补充）

- 安全组增加 3000 端口备用
- ClawBot 支持 Markdown 渲染（标题/列表/代码块/表格）
- 终端命令执行需 `/approve` 确认

## AI 记忆中枢构想

**架构**: 输入层（微信/Claude Code/网页端）→ 统一记忆层（AgentVault Memory / Hermes）→ 存储层（Obsidian + Git）→ 输出层（博客/微信推送）

**关键开源组件**:
- AgentVault Memory: 跨 AI 工具统一记忆层（2026年4月发布）
- mindloom: AI 驱动的知识编织，自动整理成结构化 Obsidian Wiki
- Hermes（已部署）: 自进化 Agent
- 微信 ClawBot: 日常对话入口

**建议项目名**: AgentWeaver / MindLoom-Claw / MemOS

## 下一步
1. Obsidian 同步配置
2. 编写 `daily-diary` Skill
3. 探索 AgentVault Memory 接入 Claude Code 历史
4. 博客自动发布

---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[TAVILY_API_KEY]], [[产出/2026-05-04 - Hermes Agent web_search 修复]]
---

# Hermes Agent

## 定义

Hermes Agent 是一个开源的 AI Agent 框架，由 Nous Research 开发。可以在终端、微信、Telegram 等平台运行，支持工具调用、技能学习、记忆持久化、定时任务等。

## 核心特点

1. 模型无关 -- 支持 15+ 推理提供商
2. 平台网关 -- 同一 Agent 可在微信、Telegram、Discord 等平台运行
3. 自改进 -- 通过 Skills 机制积累工作流程
4. 持久记忆 -- 记忆跨会话保留

## 配置要点

- 主配置: `~/.hermes/config.yaml`
- API密钥: `~/.hermes/.env`
- **坑**: Hermes 启动时不会自动加载 `.env` 到进程环境变量，需要手动调用 `reload_env()`

## 相关

- [[产出/2026-05-04 - Hermes Agent web_search 修复]] -- 解决 .env 不生效的问题

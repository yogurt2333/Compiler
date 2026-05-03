---
type: concept
created: 2026-05-04
updated: 2026-05-04
related: [[ClawBot]], [[Hermes 记忆系统]], [[AI 记忆中枢]], [[TAVILY_API_KEY]], [[产出/2026-05-04 - Hermes Agent web_search 修复]]
---

# Hermes Agent

## 定义

Hermes Agent 是一个开源的 AI Agent 框架，由 Nous Research 开发。可以在终端、微信、Telegram 等平台运行，支持工具调用、技能学习、记忆持久化、定时任务等。

## 核心特点

1. 模型无关 -- 支持 15+ 推理提供商
2. 平台网关 -- 同一 Agent 可在微信、Telegram、Discord 等平台运行
3. 自改进 -- 通过 Skills 机制积累工作流程
4. 持久记忆 -- 四层记忆架构跨会话保留，详见 [[Hermes 记忆系统]]

## 部署要点

- **环境**: Ubuntu 22.04，内存 >= 2GB
- **安装**: `curl -fsSL https://res1.hermesagent.org.cn/install.sh | bash`
- **模型**: 推荐 DeepSeek V4 Flash（响应快、输出 2元/百万 token）
- **网关**: [[ClawBot]] 微信通道，systemd user service 后台保活
- **保活**: `sudo loginctl enable-linger $USER`

## 配置要点

- 主配置: `~/.hermes/config.yaml`
- API密钥: `~/.hermes/.env`
- 会话存档: `~/.hermes/sessions/`
- 核心记忆: `~/.hermes/memories/`（USER.md、MEMORY.md）
- 元数据: `~/.hermes/state.db`（SQLite）
- **坑**: Hermes 启动时不会自动加载 `.env` 到进程环境变量，需要手动调用 `reload_env()`

## 常用管理命令

| 用途 | 命令 |
|------|------|
| 健康检查 | `hermes doctor` |
| 测试对话 | `hermes` |
| 查看日志 | `journalctl --user -u hermes-gateway -f` |
| 重启网关 | `systemctl --user restart hermes-gateway` |
| 管理配对 | `hermes pairing list/approve/revoke` |

## 相关

- [[产出/2026-05-04 - Hermes Agent web_search 修复]] -- 解决 .env 不生效的问题
- [[摘要/2026-05-01 - Hermes Agent 部署全记录]] -- 完整部署流程
- [[摘要/2026-05-04 - Hermes Agent 部署与 AI 记忆中枢构想]] -- 部署 + 记忆中枢构想
- [[Hermes 记忆系统]] -- 四层记忆架构详解

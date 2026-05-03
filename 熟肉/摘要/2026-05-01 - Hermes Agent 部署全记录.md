---
type: summary
source: "[[生肉/对话/2026-05-01 1934 - DeepSeek]]"
created: 2026-05-04
related: [[Hermes Agent]], [[ClawBot]], [[Obsidian]]
---

# 2026-05-01 Hermes Agent 部署全记录

## 核心内容

在阿里云 ECS 上从零部署 Hermes Agent，接入微信（ClawBot）作为交互界面，打造具备长期记忆和个人助理能力的 AI 助手。

## 部署流程

1. **ECS 环境**: Ubuntu 22.04，内存 >= 2GB，安全组开放 22（SSH，限制来源 IP）、18789（WebUI）
2. **安装**: `curl -fsSL https://res1.hermesagent.org.cn/install.sh | bash`
3. **模型配置**: DeepSeek V4 Flash（响应快、价格低），配置 provider/base_url/api_key
4. **微信网关**: 通过 ClawBot 通道，扫码登录微信小号，配对批准
5. **后台保活**: systemd user service + `loginctl enable-linger`

## 踩坑记录
- `hermes: command not found` → `source ~/.bashrc`
- API 401 → Key 无效或余额不足
- 微信无回复 → 未批准配对
- 22 端口暴露 → 限制来源 IP

## 下一步
- 配置联网搜索（Tavily/Exa API Key）
- Obsidian 同步（阿里云 OSS + Remotely Save）
- 定时推送和日记自动生成

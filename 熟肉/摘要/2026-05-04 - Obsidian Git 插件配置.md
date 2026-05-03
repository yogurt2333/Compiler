---
type: summary
source: "[[生肉/对话/2026-05-04 0246 - DeepSeek]]"
created: 2026-05-04
related: [[Obsidian]], [[Obsidian Git 插件]]
---

# 2026-05-04 Obsidian Git 插件配置

## 核心内容

在 Obsidian 中配置 Git 插件实现自动定时 push 到 GitHub。

## 配置步骤

1. 确保本地 Git 仓库已关联 GitHub 远程并认证正常
2. 社区插件市场安装 **Obsidian Git** 并启用
3. 手动验证 Push 可用（Ctrl+P → `Git: Push`）
4. 开启自动推送：
   - 勾选 `Split automatic commit and push timers`（分离提交和推送控制）
   - 设置 `Auto push interval` 为 30 或 60 分钟
5. 插件按设定间隔自动 push，无需手动操作

## 关键配置项

- `Split automatic commit and push timers`: 独立控制 commit 和 push 间隔
- `Auto push interval (minutes)`: 核心需求是定时 push

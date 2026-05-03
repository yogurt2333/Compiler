# Compiler

一个 Obsidian 知识库，用于编译 AI 对话中的信息碎片为结构化知识。

## 结构

```
Compiler/
├── 生肉/               # 原始素材（只读，AI 写入）
│   └── 对话/           # Web Clipper 或 Hermes 保存的原始对话
├── 熟肉/               # 编译后知识（只读，Claude 维护）
│   ├── 摘要/           # 每份资料的核心摘要
│   ├── 概念/           # 核心概念，用 [[wiki-links]] 互联
│   ├── 实体/           # 人物、项目、工具
│   ├── 综合/           # 跨页面综合分析
│   └── 产出/           # 踩坑记录、技术总结
├── index.md            # 目录
├── log.md              # 操作日志
└── CLAUDE.md           # AI 管家行为规则
```

## 工作流

1. **生肉入库** — 日常对话或 Web Clipper 保存到 `生肉/`
2. **知识编译** — 本机 Claude Code 每周跑一次，把生肉编译到 `熟肉/`
3. **同步** — 通过 Git 跨设备同步

## 维护者

- [yogurt2333](https://github.com/yogurt2333) — 库主
- Hermes Agent（服务器端）— 生肉写入 + git 定时拉取
- Claude Code（本机）— 熟肉编译

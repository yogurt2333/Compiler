---
type: concept
created: 2026-05-17
updated: 2026-05-17
related: [[Transformer]], [[Attention]], [[LLM]]
---

# QKV（Query / Key / Value）

## 定义

QKV 是 Transformer Self-Attention 机制的三大核心向量：「Query（当前词的问题）」「Key（所有词的标签/暗号）」「Value（所有词的内容）」。三者协同工作，让模型知道「每个上下文词对当前词的重要性」。

## 对应关系

```
Query  → 问问题：「谁跟我有关系？」
Key    → 对暗号：「我有这个名字，我对这个主题有信息」
Value  → 给内容：「这是我的实际数值」
```

## 数学过程

1. 输入向量 → 分别乘三个权重矩阵 Wq, Wk, Wv → 得到 Q, K, V
2. 相似度计算：Q × K^T（点积越大越相关）
3. 缩放：除以 √d_k（防止 Softmax 梯度消失）
4. Softmax 归一化 → 得到注意力权重
5. 加权求和：权重 × V → 输出 Context Vector

## 多头注意力

- N 个平行 QKV 子空间（如 8 头、16 头）
- 每个头学不同关系（语法、语义、位置等）
- 最后拼合 → 乘 Wo 降回原维度

## 来源
- [[熟肉/概念/Transformer]]

---
type: concept
created: 2026-05-17
updated: 2026-05-17
related: [[Transformer]], [[QKV]], [[LLM]]
---

# Attention（注意力机制）

## 定义

Attention 机制的核心思想是：**在处理一个位置时，让它「关注」到整个序列中最重要的位置**，而不是像 RNN 一样只能按顺序一步步传递信息。

## 一句话

Attention 就是「让模型学会在哪个词上用力」。

## Attention vs Self-Attention

- **Attention（通用）**：Decoder 看 Encoder 的输出，也叫 Cross-Attention
- **Self-Attention（自注意力）**：序列看自己，每个位置跟所有位置算相似度

## 数学本质

```
Attention(Q, K, V) = softmax(Q × K^T / √d_k) × V
```

- Q × K^T：算当前词跟所有词的相关度
- Softmax：转成「注意力分配」权重
- × V：用权重加权每个词的内容

## 来源
- [[熟肉/概念/Transformer]]
- [[熟肉/概念/QKV]]

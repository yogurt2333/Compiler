---
type: concept
created: 2026-05-17
updated: 2026-05-17
related: [[Attention]], [[QKV]], [[LLM]], [[Hallucination]]
---

# Transformer

## 定义

Transformer 是 2017 年 Google 提出的「Attention Is All You Need」架构，核心思想是**完全抛弃 RNN/CNN，只用 Attention 机制**处理序列数据。目前所有主流 LLM（GPT、Claude、DeepSeek）的基础架构。

## 核心要点

### 1. 自注意力机制（Self-Attention）

一句话：**让每个词先看一遍上下文，知道跟谁关系近、跟谁关系远，再决定自己该记住什么。**

### 2. QKV 三件套

```
Q（Query）—— 当前词问问题
K（Key）—— 所有词的「暗号」（你是谁？）
V（Value）—— 所有词的内容（你身上有什么信息？）
```

**流程：**
1. 当前词的 Q 问问题 → 跟所有词的 K 对暗号
2. 算相似度 → Softmax 归一化 → 得到**注意力权重**
3. 用权重去加权 V → 得到**加权后的上下文向量（Context Vector）**

> 比喻：Q 是你在图书馆问「有没有讲注意力的书？」→ K 是每本书的书名标签 → V 是书的内容。注意力权重告诉你哪本书最相关。

### 3. 多头注意力（Multi-Head Attention）

- 不是只用一套 QKV，而是做 8/12/16 套平行的 QKV
- 每个头学到不同的「子空间」——有的头关注语法关系，有的关注语义距离，有的关注位置
- 最后拼回去，相当于「8 个专家分别看一遍，汇总意见」

### 4. 位置编码（Positional Encoding）

Transformer 没有 RNN 的时序概念，所以需要用位置编码给每个词打上「位置标签」。原始论文用正弦/余弦函数，现在常用 RoPE（旋转位置编码）。

## 训练三阶段

1. **Pre-training（预训练）**— 海量无监督数据，学语言规律
2. **Fine-tuning（微调）**— 指令数据 + RLHF，对齐人类偏好
3. **Inference（推理）**— 用到生成任务

## 局限：Hallucination（幻觉）

Transformer 本质是**输入 → 统计规律 → 最可能的下一 token**，没有「真的理解」或「事实核查」机制。

**统一解法：**
- **RAG（检索增强）** — 生成前去知识库搜一次，把原文塞进上下文
- **结构化输出** — 用 JSON Schema/Regex 限定输出格式
- **温度控制** — 降低 `temperature` 参数减少随机性

## 与其他概念的关系
- [[LLM]]：Transformer 是所有现代 LLM 的基石
- [[Attention]]：Attention 机制是 Transformer 的核心组件
- [[Hallucination]]：Transformer 的统计本质导致幻觉问题

## 来源
- [[摘要/2026-05-17 - AI×Web3 School 预习]]

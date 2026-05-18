---
type: concept
created: 2026-05-11
updated: 2026-05-11
related: [[async await 并发]], [[DeepSeek]]
---

# LLM API 调用三技巧

## 定义

调 LLM API 时控制输出的三种手段，从软到硬依次是：System Prompt（建议）→ Few-shot（示范）→ Structured Output（强制）。

## 核心要点

### 1. System Prompt（角色设定）

- 通过 `system` 角色消息设定 AI 的身份和行为规则
- 相当于组件的 props / 全局配置
- **软约束**——LLM 可能不遵守，尤其在需要精确格式化时

```
system: "你是一个资深前端面试官，回答要简洁"
```

### 2. Few-shot（示例驱动）

- 在 messages 里给出输入→输出的例子，LLM 会自动推断模式
- **示范性约束**——比 system prompt 强，但在格式复杂时仍可能偏差
- 关键技巧：给一个结构完整的例子，比写十行描述更管用

```python
# 给一个例子，LLM 就会照着同样的 JSON 结构输出
{"role": "user", "content": "MacBook Air M2..."},
{"role": "assistant", "content": '{"name": "MacBook Air M2", "price": 6000}'},
{"role": "user", "content": "iPhone15 Pro Max..."}
```

### 3. Structured Output（硬约束）

- 通过 `response_format.json_schema` + `strict: true` 强制 LLM 按 JSON Schema 输出
- **原理**：grammar-based sampling，在 token 采样层实时计算"当前哪些 token 合法"，不合法的概率直接归零
- 生产环境必备，后端可直接 `json.loads()`，无需防御性解析

```python
payload = {
    "response_format": {
        "type": "json_schema",
        "json_schema": {
            "name": "product",
            "strict": True,
            "schema": {
                "type": "object",
                "properties": {
                    "name": {"type": "string"},
                    "price": {"type": "number"}
                },
                "required": ["name", "price"],
                "additionalProperties": False
            }
        }
    }
}
```

## 三种技巧对比

| 技巧 | 力度 | 适用场景 |
|------|------|---------|
| System Prompt | 建议性 | 设定角色、语气约束 |
| Few-shot | 示范性 | 引导模式、少样本学习 |
| Structured Output | 强制性 | 生产环境、系统对接 |

## 与第1周的关系

- 第1周学的 [[async await 并发]] 负责"怎么发 HTTP 请求"
- 第2周学的是"发请求时传什么参数来控制输出"
- 两者结合 = 一套完整的 LLM API 调用能力

## 来源

- 2026-05-11 Hermes 教学会话
- [[DeepSeek]] V4 API 文档：`deepseek-v4-flash` / `deepseek-v4-pro`

---
type: concept
created: 2026-05-06
updated: 2026-05-06
related: [[aiohttp]], [[pydantic]]
---

# async/await 并发

## 定义

Python 中通过 `asyncio.gather` 实现多个异步任务并发执行，而不是一个等一个串行跑。

## 核心要点

### 1. 并发 vs 同步

| 方式 | 代码 | 耗时 | 类比前端 |
|------|------|------|---------|
| 同步 `await` | 一个一个等 | T = t1 + t2 + t3 | `await fetch()` 串行 |
| **并发 `gather`** | 一口气全发 | T ≈ max(t1, t2, t3) | `Promise.all()` |
| 限流 `Semaphore` | 限制同时跑的数量 | 折中 | 自定义并发池 |

### 2. asyncio.gather

```python
tasks = [ask_api(session, q) for q in questions]
answers = await asyncio.gather(*tasks)   # *tasks 解包列表
```

- `gather` 接收的是**多个参数**，不是列表 → 用 `*tasks` 解包
- 返回结果顺序 = 传入顺序（不按返回快慢排）

### 3. Semaphore 限流

```python
sem = asyncio.Semaphore(3)    # 最多3个并发

async def ask_with_limit(session, q):
    async with sem:            # 超过3个就排队等
        return await ask_api(session, q)
```

### 4. 分批处理

```python
for i in range(0, len(questions), batch_size):
    batch = questions[i:i+3]
    answers = await asyncio.gather(*[ask(s, q) for q in batch])
    await asyncio.sleep(1)    # 休息1秒再发下一批
```

## 注意事项

- API 有速率限制（RPM/TPM），并发太多会 429
- 不依赖顺序的任务才能并发（如果第二步需要第一步的结果，只能串行）
- Jupyter 里直接用 `await gather(...)`，不要 `asyncio.run()`

## 与其他概念的关系

- [[aiohttp]] — 异步 HTTP 请求的基础工具，配合 gather 做并发
- [[pydantic]] — 用结构化模型接收并发返回的结果

## 来源

- 2026-05-06 Hermes Agent 前端转AI第1周第3节

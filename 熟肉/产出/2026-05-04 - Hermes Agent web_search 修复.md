---
type: output
created: 2026-05-04
related: [[Hermes Agent]], [[TAVILY_API_KEY]]
---

# Hermes Agent web_search 修复记录

## 问题现象

配置了 `TAVILY_API_KEY` 到 `~/.hermes/.env` 后，`/reset` 多次 `web_search` 工具仍然不可用。

## 根因

Hermes **启动时不会自动把 `~/.hermes/.env` 的内容加载进进程环境变量 (`os.environ`)**

- `TAVILY_API_KEY=tvly-dev-xxx` 在 `.env` 文件里 (有)
- 但 Web 工具注册的 `check_fn` 用的是 `os.getenv("TAVILY_API_KEY")` (返回 None)
- `reload_env()` 函数负责从 .env 读入 `os.environ`，但只在 `/reload` 命令中被调用，**启动流程里根本没调它**
- 所以 web 工具集一直以为没有 API key，默默不注册

## 修复

### 1. 源码修复（两处）

**gateway/run.py** -- gateway（微信端）启动时自动加载 .env
```python
try:
    from hermes_cli.config import reload_env
    count = reload_env()
    if count:
        logger.info("Reloaded %s var(s) from ~/.hermes/.env", count)
except Exception:
    logger.debug("reload_env() failed at gateway startup", exc_info=True)
```

**hermes_cli/main.py** -- CLI 启动时自动加载 .env
```python
try:
    from hermes_cli.config import reload_env
    reload_env()
except Exception:
    pass
```

### 2. 当前会话热修复（不需要重启）

```python
from hermes_cli.config import reload_env
reload_env()

from tools.registry import invalidate_check_fn_cache
invalidate_check_fn_cache()
```

- `reload_env()` -- 把 .env 里的变量写入 `os.environ`
- `invalidate_check_fn_cache()` -- 清除工具注册的检查缓存，让 web 工具重新评估可用性

## 关键文件位置

| 文件 | 作用 |
|------|------|
| `~/.hermes/.env` | API 密钥存储 |
| `~/.hermes/hermes-agent/tools/web_tools.py` | Web 搜索工具实现 |
| `~/.hermes/hermes-agent/tools/registry.py` | 工具注册 + check_fn 缓存 |
| `~/.hermes/hermes-agent/hermes_cli/config.py` | `reload_env()` / `load_env()` 函数 |
| `~/.hermes/hermes-agent/gateway/run.py` | Gateway 启动入口 |
| `~/.hermes/hermes-agent/hermes_cli/main.py` | CLI 启动入口 |

## 经验

下次遇到 Hermes 的环境变量不生效，先检查：
1. `.env` 文件里是否有 Key
2. 当前进程的 `os.environ` 里是否加载到了
3. 如果没加载到，让助手执行 `reload_env()` + `invalidate_check_fn_cache()`

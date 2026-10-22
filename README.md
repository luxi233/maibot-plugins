# MaiBot 插件合集（修复版 fork 集合）

个人维护的 MaiBot 插件仓库集合。每个插件是独立 git 仓库（MaiBot 限制：一仓库 = 一插件），本仓库用 submodule 聚合，方便统一查找和拉取。

## 插件列表

| 插件 | 仓库 | 版本 | 相对上游的修复 |
|---|---|---|---|
| 万能链接解析器 | [maibot-platform-parser](plugins/maibot-platform-parser) | v1.7.5 | `_is_at_me` 补充 `target_user_id` 字段，修复 `require_at_in_group` 开启时群聊 @ 识别失效、所有群消息被静默跳过 |
| 好友申请处理 | [friend-request-handler](plugins/friend-request-handler) | v1.3.1 | LLM 审核 `max_tokens` 64 → 2048，修复推理模型思考 token 耗尽限额导致所有申请被默认拒绝 |

上游来源：

- `tidain/maibot-platform-parser`（解析核心移植自 Zhalslar/astrbot_plugin_parser，框架基于 Color2333/maibot-multi-platform-parser）
- `whitefox20011120/friend-request-handler`

## 安装方式（MaiBot WebUI）

插件管理 → 安装插件 → 从仓库安装，填对应插件仓库地址：

```
https://github.com/luxi233/maibot-platform-parser
https://github.com/luxi233/friend-request-handler
```

分支 `main`。装好后「已安装」页的更新按钮即 `git pull` 本 fork。

> 注意：`maibot-platform-parser` 与官方市场版同插件 ID（`tidain.maibot-platform-parser`），同一台 MaiBot 只能装一份——装本 fork 就不要再从市场装官方版。从市场页点更新会装回官方版（config.toml 会保留）。

## 拉取全部插件源码

```bash
git clone --recursive https://github.com/luxi233/maibot-plugins
# 已克隆则：
git submodule update --init --recursive
```

## 更新所有 submodule 到各自最新 main

```bash
git submodule update --remote
```

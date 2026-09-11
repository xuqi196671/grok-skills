---
name: 全网触达
description: >-
  用户要全网调研、搜索、查某平台讨论，或给出小红书/推特/B站/Reddit/YouTube/GitHub/雪球/RSS 等链接时用：按
  agent-reach 路由只读抓取；先 doctor 再按平台 reference 执行，不做发帖点赞
---
# Agent Reach — 互联网能力路由器

改编自官方 [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) 的 `agent-reach` 技能。
15 平台、多后端。**本技能存在时，访问这些平台优先用它，不要自己发明抓取方案。**

本技能只负责从互联网**获取**内容（搜、读、拉），不负责写报告/分析/翻译加工；不做发帖/评论/点赞等写操作。已有专门技能的平台，先用专门技能。

详细分平台命令见同目录 `references/*.md`（安装时从上游同步）。上游更新：https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/update.md

## 常驻规则

1. **动手前先体检**：多后端/登录态平台（小红书/Reddit/B站/Twitter/Facebook/Instagram）先跑 `agent-reach doctor --json`。`active_backend` 有值按它选命令；为 `null` 表示 Doctor 未做实时探测，不代表没有后端。仅当任务明确需要该平台时，再用对应 reference 的只读命令验证。
2. **声明你在用什么**：开始前说一句「使用 agent-reach 的 X 平台 / Y 后端」。
3. **失败按 references 重试链处理**，不要瞎猜命令。
4. **全网调研**：可组合多平台并行收集再汇总（网页搜索 + 社交讨论 + 中文平台视角）。
5. **替用户盯版本**：较大多平台任务收尾可跑 `agent-reach check-update`；有新版在汇报里附一句提示，不中断当前任务去更新。

若本机没有 `agent-reach` 命令，先按上游安装指南安装 CLI：https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md  
没有 CLI 时，仍可走下方「零配置」里不依赖它的命令（如 `curl` Jina、`gh`），并说明哪些渠道不可用。

## 路由表

| 用户意图 | 分类 | 详细文档 |
| --- | --- | --- |
| 网页搜索/代码搜索 | search | references/search.md |
| 小红书/推特/B站/V2EX/Reddit/Facebook/Instagram | social | references/social.md |
| 招聘/职位/LinkedIn | career | references/career.md |
| GitHub/代码 | dev | references/dev.md |
| 网页/文章/RSS | web | references/web.md |
| YouTube/B站/播客字幕 | video | references/video.md |
| 雪球/股票行情 | finance | references/finance.md |

## 零配置快速命令

```bash
# Exa 网页搜索（需 mcporter + Exa）
mcporter call exa.web_search_exa query="query" numResults=5

# 通用网页阅读
curl -s "https://r.jina.ai/URL"

# GitHub 搜索
gh search repos "query" --sort stars --limit 10

# YouTube 字幕（B站不要用 yt-dlp，见 video.md）
yt-dlp --write-sub --write-auto-sub --skip-download -o "/tmp/%(id)s" "URL"

# V2EX 热门
curl -s "https://www.v2ex.com/api/topics/hot.json" -H "User-Agent: agent-reach/1.0"

# B站搜索（bili-cli，无需登录）
bili search "query" --type video -n 5
```

## 需登录态的平台（按 doctor 的 active_backend 选）

Twitter：`agent-reach configure twitter-cookies` 的 Cookie 主要供 doctor 检查；直接跑 `twitter` 前须在子进程环境提供 `TWITTER_AUTH_TOKEN` 与 `TWITTER_CT0`，且不回显密钥。

小红书：不替用户登录、不擅自读浏览器 Cookie；优先用户已有 Chrome 会话经 OpenCLI；否则用 Cookie-Editor 手工导出再配。

```bash
twitter search "query" -n 10
opencli reddit search "query" -f yaml
opencli xiaohongshu search "query" -f yaml
opencli facebook search "query" -f yaml
opencli instagram search "query" -f yaml
opencli instagram user USERNAME -f yaml
```

## 环境检查

```bash
agent-reach doctor --json
```

## 工作区规则

临时输出用 `/tmp/`；持久配置用 `~/.agent-reach/`。不要把大段抓取结果堆进工作区仓库。

## 与本应用其它技能

- 「现成优先」「搜索优先」：流程与选型；本技能是多平台抓取路由
- 「先复述再动手」：大调研开干前仍先短复述确认
- 「可逆直做」：本技能默认只读；若某命令会写入平台，先问用户
- 交付给用户的摘要用简体中文（「能中则中」）

---
name: github-skill-sync
description: >-
  把本地自定义技能和 GitHub xuqi196671/grok-skills
  做并集同步。只给不适合当前这一边的技能打标，适合两边的不标。推送必须用本地全文，禁止截短。永不恢复
  seedance、grok-shipin。触发含：同步技能、合并技能。
---
# 技能合并同步

仓库 https://github.com/xuqi196671/grok-skills  
Grok 本地 `/home/workdir/.grok/skills/`；Grok Bot 本地 `/home/box/agent-data/workflows/`（用技能写入）  
只处理自定义技能。GitHub 连接器不是技能，是账号授权；本技能靠它读写仓库。

永不恢复、不上传 `seedance`、`grok-shipin`。

## 并集

- 一边多出来且适合那一边，就补上
- 不删任何一边独有的
- 内容打架交给用户，不要擅自覆盖

## 怎么打标（只标「这边不适合」）

不要标「只给 Grok / 只给 Bot」。只标**当前这一边用不了**的：

- 在 Grok 上同步：装不了、也写不出有用提示词的，才标 `audience: bot`（意思是「Grok 这边不适合」），仓库保留，本地不装
- 在 Bot 上同步：Bot 完全用不上的，才标 `audience: grok`（意思是「Bot 这边不适合」）
- 两边都能用的**不标**。写提示词、人设卡、版面、视频时间线的技能默认两边都能用
- 不要因为会调用 Imagine / 出图组件就标成 Grok 专用
- 不要预先给所有技能贴标。第一次判断才标「这边不适合」

## 推送

- 以本地全文为准覆盖仓库对应文件，字节数应对得上
- 禁止只推半截 SKILL.md
- 改完本技能也要推进仓库，让 Bot 用同一套规则

## 节奏

每天第一次相关任务做一次同步。本地改完可共用的技能后 push。

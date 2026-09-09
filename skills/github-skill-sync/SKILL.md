---
name: github-skill-sync
description: Sync custom Grok skills with the public GitHub repo xuqi196671/grok-skills. On the first task of each calendar day, pull the repo and make local skills match. After local skill edits, push back. Never sync seedance or grok-shipin. Triggers include 同步技能, GitHub技能仓库, 每天第一次任务, grok-skills.
---

# GitHub 技能正本

正本仓库 https://github.com/xuqi196671/grok-skills（公开，默认分支 main）。
本地目录 `/home/workdir/.grok/skills/`。
不同则以仓库为准，拉齐本地。本地改完技能后推回仓库。

## 每天第一次任务

1. 看本地标记文件 `/home/workdir/.grok/skills/.last-github-sync` 是否已是今天。
2. 已是今天则跳过同步。
3. 还不是今天则读仓库 `skills/` 写回本地。
4. 永久不恢复 seedance、grok-shipin。
5. 写 `.last-github-sync` 为当天日期。

## 不管 Grok Bot

Bot 要另写「先读这个仓库」。

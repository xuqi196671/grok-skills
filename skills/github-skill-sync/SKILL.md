---
name: github-skill-sync
description: Merge custom skills between local and GitHub xuqi196671/grok-skills. Union both sides. If two skills look similar but text differs, show both to the user and wait. Never restore seedance or grok-shipin. Triggers include 同步技能, 合并技能, GitHub技能仓库, 每天第一次任务.
---

# 技能合并同步

仓库 https://github.com/xuqi196671/grok-skills
本地 /home/workdir/.grok/skills/

目标是并集。谁多出来的就补到缺的那边，不删对方独有的。
两边同名但正文不同，或两个名字不同但作用明显同类：停下来把两边要点发给用户，等用户决定留哪个。
永不恢复 seedance、grok-shipin。
不管 Grok Bot。

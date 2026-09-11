# grok-skills

Grok / Grok Bot 自定义技能正本（并集）。

## 本地路径

- Grok：`/home/workdir/.grok/skills/`
- Grok Bot：`/home/box/agent-data/workflows/`（用技能写入）

## 同步规则

见 `skills/github-skill-sync/SKILL.md`。

- 并集：两边独有都保留，不互相删
- 只装适合当前端的；当前端用不了的才标 `audience: bot` / `audience: grok`；共用的不标
- 不同步 / 不恢复 `seedance`、`grok-shipin`
- 内容冲突交用户决定
- 推送用本地全文，禁止截短
- 不自动同步；用户说「同步技能」「合并技能」时再跑

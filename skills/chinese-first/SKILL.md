---
name: chinese-first
description: Default all user-facing text to Simplified Chinese. Use for replies, skills, prompts, stories, roleplay, docs, plans, and any prose. If the app will show English UI the model cannot change, first explain in Chinese what that UI is and what a click will do. Triggers include 中文优先, 用中文, 默认中文, 中文交流, 写技能, 提示词, 角色扮演.
---

# 中文优先

所有面向用户的文字默认简体中文。先中文，只有本来就该是别的语言的片段才留原文。

## 必须用中文

- 对用户的回复、解释、确认、追问
- 新写或改写的技能正文（说明、步骤、规则）
- 文生视频 / 图生视频提示词（用户没指定别的语言时）
- 故事、角色扮演、玩法文案、策划、方案、清单、备忘
- 文档标题、段落、表格说明、幻灯片文案
- 提交说明、PR 描述、issue、注释里的自然语言

## 可以（或必须）不用中文

- 用户明确要求跟他当前用的非中文走
- 代码、API、CLI、文件名、环境变量、协议字段
- 官方产品名、人名、地名、论文标题、不可译商标
- 必须保持原文的引用、歌词、法条、错误信息原文
- 技能 frontmatter 的 `name` 等机器字段
- 用户指定「这段用英文/日文/原文」

句子用中文，专有名词可留原文。不要整段改成英文装专业。

## 改不了的英文界面

客户端工具条、Running、按钮、授权卡片上的英文，模型改不了。遇到这种情况必须：

- 先在回复里用中文说明「下面可能出现什么英文、那是什么意思」
- 说明点下去会做什么、不点会怎样
- 不要默认用户认识那些英文

## 冲突时

1. 用户本轮明确指定语言优先
2. 内容本身的本来语言优先于强行翻译
3. 其余默认简体中文

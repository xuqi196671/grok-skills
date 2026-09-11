---
name: 本地缓存优先
description: '当任务会反复用到数据、大段工具输出或跨会话事实时用：先读/写本地记忆盘（E:\\ai-local-memory），再上网拉取；聊天只回短摘要并指向文件'
audience: bot
---
# 本地缓存优先（文件系统当 AI 记忆）

改编自 filesystem-context 思路。

## 目标

把本地磁盘当外置大脑：常用数据和大段工具输出落在文件里，聊天只带短摘要和路径，省时间和 token。

## 默认根目录

用户 PC 上的 `E:\ai-local-memory`（`ListMachines` 取 machineId）。

A 股数据：`E:\ai-local-memory\datasets\ashare-kline-store`。

## 步骤

1. 先查本地是否已有可用缓存
2. 有则读盘、短摘要回复；没有再拉网并写入本地
3. 大结果落文件，聊天只给路径与要点
4. 写入时注明来源与更新时间

## 不要

- 把大段原始数据贴进聊天
- 明明本地有还重复全量拉取

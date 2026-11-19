# Vue 3 + TypeScript + .NET 8 + SQL Server

一套给 AI 编码用的最小约束包：让 AI 每次只做一个功能、知道去哪里读代码、做完必须给证据。

## 文件

- `AGENTS.md`：长期约束，复制到项目根目录。
- `CURRENT.md`：当前任务卡，每次新功能重写。

## 用法

1. 把 `AGENTS.md` 放到项目根目录（或让 Codex 读取）。
2. 把 `CURRENT.md` 放到项目根目录，每次新功能重写一遍。
3. 每个功能新开一个会话，先把 `CURRENT.md` 发给 AI。
4. 让 AI 用自己的话复述目标，并列出准备读/改的文件；确认后再动手。
5. 一次只做一步，跑 `verify`，贴输出或截图；通过后再下一步。
6. 同一个错误出现两次，才写进 `AGENTS.md`；出现三次，做成 lint/test/script。

## 为什么

长上下文会遗忘、混淆和编造。约束不靠更长的提示词，而靠：

- 代码和文件路径作为规格；
- 一次一个可验证单元；
- 重复错误才升级为检查；
- `CURRENT.md` 作为外部工作记忆，上下文变长就重开会话。

这些做法来自 Poteto 的公开演讲和 pstack：

- 演讲：https://www.youtube.com/watch?v=O_zcc6Xl12g
- 原帖：https://x.com/poteto/status/2111133080526495985
- pstack：https://github.com/cursor/plugins/tree/main/pstack

目录名和命令请按实际项目调整。

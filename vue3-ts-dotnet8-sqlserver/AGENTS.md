# 项目约束

Vue 3 + TypeScript 前端，.NET 8 Web API，SQL Server 仅内网可连。

## 工作方式

- 一次只做一个功能；不顺手重构无关代码。
- 先读相关文件再改；回答中引用具体文件路径。
- 不确定就问；不编造 API、字段、包名、配置。
- 每个功能新开会话，从 `CURRENT.md` 开始。
- 上下文变长，或同一个问题两次没修好：停止，更新 `CURRENT.md`，新开会话。
- 用中文解释；代码、命令、标识符保持原文。

## 命令

- 本地验证：`./verify.ps1`（必须通过）
- 前端生成 API：`pnpm --dir frontend gen:api`
- 数据库迁移：`dotnet ef migrations add <Name> --project src/Infrastructure --startup-project src/Api`

## 代码位置

- 前端入口：`frontend/src/main.ts`
- 前端功能：`frontend/src/features/<feature>`
- API：`backend/src/Api`
- 应用层：`backend/src/Application`
- 数据层：`backend/src/Infrastructure`

按实际目录调整；改代码前先确认路径存在。

## 硬规则

1. 不手写 API 类型；使用生成的 client。
2. 组件不直接 `fetch`/`axios`；统一走 `src/api`。
3. Controller 不直接使用 `DbContext`；DTO 出入边界。
4. 不加新依赖，除非我明确同意。
5. DB 变更必须有迁移和 `migrations.sql`；内网跑过之前不说“已验证”。
6. 破坏性迁移（DROP、改类型、改可空性）必须先问我。
7. 没有 `verify` 输出或截图/内网报告，不说“完成”。

## 升级规则

- 第一次犯错：在当前会话纠正。
- 第二次犯错：写进本文件。
- 第三次犯错：做成 lint/test/script，然后删掉对应文字。

## 完成标准

- `verify` 通过，并贴出输出。
- UI 改动附截图或录屏。
- DB 改动附迁移文件和内网测试结果。

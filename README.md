# Mira Shiyan

拾言（Shiyan）的默认内容 Destination。

本仓库用于保存用户确认后正式投递的 Markdown 内容及其 Git 历史。

## 唯一真相

本仓库**不是**拾言产品、任务状态、数据模型或流程的真相源。

唯一真相位于 `dangjingtao/uichat-mira-mobile` 的 `dev` 分支：

- 产品基线：`docs/shiyan/PRD.md`
- 技术基线：`docs/shiyan/TECHNICAL_DESIGN.md`
- 跨仓库治理：`docs/shiyan/README.md`
- GitHub Destination 合同：`docs/shiyan/GITHUB_DESTINATION_CONTRACT.md`

Canonical directory:

https://github.com/dangjingtao/uichat-mira-mobile/tree/dev/docs/shiyan

## Destination 内容约定

MOB-022 的正式内容目录保持稳定且可推导：

```text
entries/YYYY/MM/<captureTaskId>.md
```

`YYYY/MM` 使用 Final Draft `confirmedAt` 的 UTC 年月；文件名固定使用 CaptureTask UUID，不使用标题 slug，避免用户改标题或网络重试时生成第二篇文档。

正式 Markdown 的最小 Frontmatter：

```yaml
---
title: "..."
shiyan_task_id: "..."
shiyan_final_draft_id: "..."
published_at: "2026-08-29T03:00:00.000Z"
---
```

Frontmatter 后正文是用户确认后的 Final Draft Markdown。本仓库不附带完整 Transcript、Provider 原始响应、Cloud Secret 或内部错误信息。

同一投递重试必须复用同一路径。若目标文件已经存在且内容完全一致，可视为此前写入成功后的恢复；若同一路径存在不同正式内容，则由 Cloud 返回冲突，不在这里自动覆盖，也不通过随机文件名制造重复文档。

## 边界

- 本仓库保存已经确认并投递的内容。
- Git commit history 作为已投递文档的可信历史。
- 不把本仓库当作 CaptureTask 数据库。
- 不把本仓库当作 Transcript / AI Draft / Final Draft 的唯一存储。
- 不在这里独立定义拾言产品行为或技术合同。
- 投递成功后由 Cloud 保存并返回真实文件 URL 与 commit SHA，供拾言历史任务展示 canonical link。
- GitHub credential 只属于 Cloud Secret；本仓库不保存 PAT、token 或其他投递密钥。

如果内容目录、Frontmatter、文件命名或投递语义等修改会影响拾言产品或跨仓库合同，必须先更新并评审 Mobile canonical truth，再修改本仓库。

修改完成后需对照 `PRD.md`、`TECHNICAL_DESIGN.md`、`GITHUB_DESTINATION_CONTRACT.md` 与治理 `README.md` 做一致性检查。

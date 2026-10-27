---
name: github-publisher
description: GitHub 发布生产线。把本地文件发布为新仓库或更新已有仓库：建仓、上传文件、配简介和 topics、验证，全程 gh api 不依赖 git push。触发词：发 GitHub、发布到 GitHub、建个仓库、传上去、更新 README、改简介、加 topics。
---

# GitHub 发布生产线（GitHub Publisher）

## 角色定位

你是发布操作员，把用户的本地文件可靠地发布到 GitHub。核心承诺：**零试错**——下面每条硬规则都来自真实踩坑，照做就能一次发成功。

## 环境硬约束（已验证的坑，必须遵守）

1. **git push 可能被 TLS 拦截**（Go TLS/SNI 问题导致超时/失败）→ 一律不走 git，全部用 `gh api` 走 Git Contents API
2. **PowerShell 工具可能吞 stdout**（exit 0 但无输出）→ 关键输出 `Out-File` 落盘后用 Read 验证，或用 Bash 里的 `gh api` 回读验证
3. **Bash shim 可能缺 coreutils**（base64/head/ls/cp 不可用）→ base64 编码用 PowerShell `[Convert]::ToBase64String`，复制文件用 `Copy-Item`
4. **删除仓库需要 delete_repo scope**，遇 403 直接引导用户网页手动删（Settings → Danger Zone），不要反复重试

## 发布新仓库（标准四步）

### 1. 建仓库

```
gh repo create {owner}/{name} --public --description "{简介}"
```

已存在会报错，忽略后继续上传即可。

### 2. 上传文件（每个文件一次 PUT）

- URI：`https://api.github.com/repos/{owner}/{repo}/contents/{path}`，方法 PUT
- Body：`{message, content}`，content = 文件字节的 base64
- 子目录文件直接把路径写进 URL（如 `popup-layer-ui/SKILL.md`），目录自动创建，不需要提前建目录
- PowerShell 编码：`$content = [Convert]::ToBase64String([System.IO.File]::ReadAllBytes($file))`
- Headers：`Authorization="token (gh auth token)"`、`Accept='application/vnd.github+json'`
- Body 用 UTF-8 字节传：`[System.Text.Encoding]::UTF8.GetBytes(($body | ConvertTo-Json))`

### 3. 配 topics

`PUT /repos/{owner}/{repo}/topics`，Body `{names: [...]}`，全小写、连字符，至少 5 个：内容领域词 + 生态词（claude-code / cursor / codex / agent-skills 等）。

### 4. 验证

- `GET /repos/{owner}/{repo}/contents` 列文件清单
- `GET /repos/{owner}/{repo}/commits` 看最新提交信息
- 简介和 topics 用 `GET /repos/{owner}/{repo}` 回读

## 更新已有文件（必须先取 sha）

1. `GET /repos/{owner}/{repo}/contents/{path}` 取返回的 `.sha`
2. PUT 同一 URL，Body 额外带 `sha` 字段
3. 不带 sha 更新会失败（404/409），先 GET 再 PUT，没有例外

## 交付规范

- 新仓库默认三件套：README.md（写清定位和用法）+ LICENSE（协议先与用户确认，系列仓库统一 CC BY-NC 4.0，链接 https://creativecommons.org/licenses/by-nc/4.0/legalcode）+ 核心内容文件
- 系列仓库的成员 README 顶部加一行导流："本 xx 是 [系列仓库] 的一员，更多看那边"
- 简介 = 一句话是什么 + 关键能力 + 兼容平台，别只写"我的仓库"
- 本地文件 UTF-8 无 BOM：`New-Object System.Text.UTF8Encoding($false)`
- 发完向用户报告：仓库链接、文件清单、简介和 topics，以及本地副本路径

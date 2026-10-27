# github-publisher

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

AI Agent GitHub 发布生产线 —— **建仓库、传文件、配简介 topics、验证，全程 `gh api`，不依赖 git push。**

它把一次"发 GitHub"拆成标准四步（建仓 → 上传 → topics → 验证），并把真实踩过的坑全部内置成硬规则：

- git push 被 TLS 拦截 → 改走 Contents API
- Agent 工具吞 stdout → 输出落盘再验证
- Bash 环境缺 coreutils → base64 编码和复制改用 PowerShell
- 更新已有文件必须先取 sha，没有例外
- 删仓库需要 delete_repo 权限，403 时引导用户手动处理

装上之后，对 Agent 说"把这个发 GitHub"，一次成功，零试错。

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/github-publisher
```

### 方式二：WorkBuddy

将 `SKILL.md` 所在的 `github-publisher` 文件夹放入技能目录：

```
~/.workbuddy/skills/github-publisher/SKILL.md
```

### 方式三：Claude Code / Codex / Cursor 等

没有独立技能目录的 Agent，把 `SKILL.md` 的内容追加到项目的 Agent 规则文件里即可：

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/github-publisher.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——它本身就是一份几分钟读完的规范，评审与使用时当 checklist 用。

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

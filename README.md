# moyan-skills 🧰

墨言的 AI Agent Skill 系列 —— 模型无关、平台无关，兼容 Agent Skills 开放规范（SKILL.md 格式），适配 Claude Code / Cursor / Codex / Copilot / WorkBuddy 等任意编码助手。

> 持续更新中。每个 skill 独立成目录，可单独安装、单独取用。

## 系列目录

| Skill | 类别 | 一句话简介 | 安装 |
| --- | --- | --- | --- |
| [popup-layer-ui](./popup-layer-ui) | 质量规范 | 弹出层（Tooltip / Toast / Alert / Popconfirm / Modal / Drawer）选型决策与硬性设计规则 | `npx skills add MoYan1638/moyan-skills/popup-layer-ui` |
| [strategic-advisor](./strategic-advisor) | 思维决策 | 战略参谋模式：身份对调、主动提问、挑战漏洞，把混乱理成可落地的行动方案 | `npx skills add MoYan1638/moyan-skills/strategic-advisor` |

## 为什么是这两类

- **质量规范类**：让 AI 的输出更好，而不是更快 —— 没有规范 AI 也能写界面，但会写出按钮乱套、层级混乱的界面
- **思维决策类**：改变 AI 与你的协作方式 —— 不产出代码，产出判断

工具提效类 skill 竞品一搜一大把，规范与思维是踩坑换来的，最难被抄。

## 安装方式

1. **通用 Skills CLI（推荐）**：见上表安装命令
2. **任意 Agent 平台**：把对应目录下 `SKILL.md` 的内容追加到你的 Agent 规则文件（CLAUDE.md / AGENTS.md / .cursor/rules/ 等）
3. **WorkBuddy**：复制到 `~/.workbuddy/skills/<skill-name>/`
4. **人类阅读**：每个 SKILL.md 单独可读，3 分钟读完当 checklist 用

## License

MIT

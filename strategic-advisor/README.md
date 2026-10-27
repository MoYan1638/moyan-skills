# strategic-advisor

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

AI Agent 战略参谋 Skill —— **身份对调、主动提问、挑战漏洞，产出可落地的行动方案。**

普通 AI 助手习惯"有问必答"，你问什么它答什么；这个 skill 让 AI 换个身份当你的参谋：它主动向你提问、摸清你的真实底牌（技能 / 时间 / 损失承受力 / 真实诉求），发现你逻辑有漏洞或自我美化时直接点破，最后交付一份固定五段式的行动方案（含第一周清单）。

## 适合场景

- "帮我理清思路，我该从哪个方向开始"
- "A 和 B 两个方案该选哪个"
- "这件事该怎么开始做"

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/strategic-advisor
```

### 方式二：WorkBuddy

将 `SKILL.md` 所在的 `strategic-advisor` 文件夹放入技能目录：

```
~/.workbuddy/skills/strategic-advisor/SKILL.md
```

### 方式三：Claude Code / Codex / Cursor 等

没有独立技能目录的 Agent，把 `SKILL.md` 的内容追加到项目的 Agent 规则文件里即可：

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/strategic-advisor.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——它本身就是一份几分钟读完的规范，评审与使用时当 checklist 用。

## 核心设计

- 每轮只问 2-3 个最关键的问题，禁止问题清单轰炸
- 每轮结束一句话小结已掌握的信息 + 标注还缺什么
- 四条退出条件全打勾才许输出方案：目标一句话说清 ✓ 硬约束一句话说清 ✓ 分歧点收敛 ✓ 用户对上述总结无异议 ✓
- 方案固定五段式：现状一句话 → 分阶段步骤 → 第一周清单（具体到周一做什么）→ 风险与止损线 → 留给你的问题
- 四条禁区：不写万能废话 / 不超过 5 轮 / 方案给出后不追问 / **不替用户拍板**（只给选项 + 倾向 + 理由，决定权在你）

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

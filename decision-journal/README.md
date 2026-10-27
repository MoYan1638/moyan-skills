# decision-journal 决策日志

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

给每个重要决定装"行车记录仪"的 Agent Skill。人做决定时逻辑清楚，但记忆只保留结论、不保留理由——两周后你只剩"当时定了先上静态版"，忘了为什么，于是开始怀疑、摇摆、推翻重做。决策日志在**拍板那一刻**留档：背景、备选项、理由、以及"当时赌了什么结果"，日后一句"当时为什么这么定"即可原样调出。

## 解决什么

- **理由丢失**：决定当时很清楚，两周后忘了理由只剩结论
- **事后脑补**：结果好觉得"我当时想得周全"，结果坏觉得"我蠢"——两种都是幻觉，只有当时写下的原始理由是真相
- **决策复盘没有原料**：项目走偏了，分不清"决定本身错了"还是"执行走样了"

## 记录格式

每条 6 个字段，30 秒填完：

```
## 📌 决策 #003 | 2026-10-24 | 恋爱人格小程序
- 决定：第一版不带实时 AI，只上静态预生成解读
- 背景：个人主体，第一次做小程序，12月前想上线
- 备选项：A. 纯静态　B. 静态+引导式AI　C. 直接实时AI
- 理由：审核风险最低，先跑通"上线→流量主"全流程；AI 层接口预留
- 预期：3 个月内 UV 破 1000 则证明瓶颈不在 AI 功能
```

**预期字段是灵魂**——以后回头看，你是拿"当时的预测"对照"实际结果"，而不是拿结果反推理由。

## 硬规则

1. 只记"分岔点"：做反了会返工/改变方向的才记
2. 预期字段必填，没有可验证预期就是流水账
3. 理由必须写"为什么不是 B"，只写"为什么是 A"等于没写
4. 回查时保持中立，调出原始判断，不加工不美化
5. 推翻旧决定不改旧条目，记新条目并注明"推翻 #00X"

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/decision-journal
```

### 方式二：WorkBuddy

将 `SKILL.md` 所在的 `decision-journal` 文件夹放入技能目录：

```
~/.workbuddy/skills/decision-journal/SKILL.md
```

### 方式三：Claude Code / Codex / Cursor 等

没有独立技能目录的 Agent，把 `SKILL.md` 的内容追加到项目的 Agent 规则文件里即可：

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/decision-journal.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——它本身就是一份几分钟读完的规范，评审与使用时当 checklist 用。

## 适用场景

- 项目决策留档（技术选型、功能取舍、上线节奏）
- 副业/创业决策（方向选择、报价策略）
- 与复盘类 skill 串联：复盘时先翻日志，定位问题层级

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

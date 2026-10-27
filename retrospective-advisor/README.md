# retrospective-advisor

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

AI Agent 复盘参谋 —— **固定四问挖出真实偏差，输出一页复盘卡。**

复盘的目的不是总结感受，是找出下次能用的具体动作。这个 skill 把复盘收敛成固定流程：

**固定四问**：预期 vs 实际 / 第一个偏差点在哪 / 下次保留什么 / 下次砍掉什么

**一页复盘卡**：结论一句话 + 有效动作 + 无效动作 + 下次保留 + 下次砍掉 + **一个**可执行改动

与 [strategic-advisor](../strategic-advisor) 配套：一个管出发前想清楚，一个管到达后学到位。

## 硬性规则

- 产出动作，不收感受——"下次多努力"无效，"下次先写提纲再动笔"有效
- 一页封顶，每类最多 3 条
- "一个改动"只能有一个
- 不翻旧账、不指责，偏差归因到流程不归因到人品
- 顺利的也要复盘：结果好≠流程对，运气和实力分开记

## 安装

```bash
npx skills add MoYan1638/moyan-skills/retrospective-advisor
```

或把本目录 `SKILL.md` 的内容追加到你的 Agent 规则文件（CLAUDE.md / AGENTS.md / .cursor/rules/ 等）。

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

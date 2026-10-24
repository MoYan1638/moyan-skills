# moyan-skills

墨言的 AI Agent Skill 系列（持续更新）。Agent Skills 开放格式，适配 Claude Code / Cursor / Codex / WorkBuddy 等任意编码助手。

## Skill 目录

| Skill | 类别 | 简介 | 安装命令 |
|---|---|---|---|
| popup-layer-ui | 质量规范 | 弹出层（Tooltip/Toast/Alert/Modal/Drawer）选型决策与硬性设计规则 | `npx skills add MoYan1638/moyan-skills/popup-layer-ui` |
| liquid-glass-ui | 质量规范 | 液态玻璃界面生产工艺：五步玻璃工艺 + 背景三原则 + 实测避坑，附完整模板 | `npx skills add MoYan1638/moyan-skills/liquid-glass-ui` |
| review-precheck | 质量规范 | 小程序/App 提审前五项合规预检，产出"可提/改完再提/提了也拒"判定 | `npx skills add MoYan1638/moyan-skills/review-precheck` |
| strategic-advisor | 思维决策 | 战略参谋模式：身份对调、主动提问、挑战漏洞，产出可落地行动方案 | `npx skills add MoYan1638/moyan-skills/strategic-advisor` |
| retrospective-advisor | 思维决策 | 复盘参谋：固定四问挖真实偏差，输出一页复盘卡（一个可执行改动） | `npx skills add MoYan1638/moyan-skills/retrospective-advisor` |
| decision-journal | 思维决策 | 决策日志：拍板瞬间留档（背景/备选/理由/预期），日后原样回查防事后脑补 | `npx skills add MoYan1638/moyan-skills/decision-journal` |
| github-publisher | 工具提效 | GitHub 发布生产线：建仓→上传→配 topics→验证，内置踩坑硬规则 | `npx skills add MoYan1638/moyan-skills/github-publisher` |
| infra-ledger | 工具提效 | 基建台账：域名/服务器/证书/映射关系登记与查询，到期自动预警 | `npx skills add MoYan1638/moyan-skills/infra-ledger` |

## 为什么是这三类

- **质量规范类**：让 AI 的输出更好，而不是更快——没它 AI 也能写，但会写出不合格的界面/踩审核红线
- **思维决策类**：改变 AI 和你的协作方式——strategic-advisor 管事前想清楚，decision-journal 管拍板留档，retrospective-advisor 管事后学到位，构成完整决策闭环
- **工具提效类**：把重复劳动自动化——发布流程和资产台账，做一次流程化，之后一句话完成

三类共同点：都从真实踩坑经验里长出来，不是空想模板。

## 安装方式

单个安装用上表命令；也可把对应目录下的 `SKILL.md` 内容直接复制进你所用 Agent 的规则文件（`CLAUDE.md` / `AGENTS.md` / `.cursor/rules/` 等）。

## 持续更新

系列会持续扩充，新 skill 以表格新增一行。

## 许可

本系列采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh) 协议：个人学习与二次创作免费，需署名并附原仓库链接；**禁止商业用途（含倒卖、打包进付费产品）**，商用授权请联系作者。

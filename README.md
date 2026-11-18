# moyan-skills

墨言的 AI Agent Skill 系列（持续更新）。Agent Skills 开放格式，适配 Claude Code / Cursor / Codex / WorkBuddy 等任意编码助手。

## Skill 目录

| Skill | 类别 | 简介 | 安装命令 |
|---|---|---|---|
| ui-patterns | 质量规范 | 界面设计规范八合一：导航（侧边栏分组/选中态/折叠）+ 表单（13 种组件选型/校验时机/报错文案）+ 反馈（七种弹出层/七种加载组件/动效配方）+ 质感细节（色阶层次/暗色字重/排版防抖/输入法与滚动细节）+ 微交互动效（点赞爆粒子/提交三连变/果冻开关/长按确认配方与可运行示例）+ 效果决策与提示词库（18 个 UI 效果的场景决策表/AI 提示词/实现要点）+ 特殊控件八件套（徽标/数字输入框/时间轴/翻页器/边框流光/骨架屏/开关/走马灯的选型/硬规则/参数速查，附八控件全交互示例）+ 消除 AI 味（8 项体检扫描/九刀精修顺序/验收 5 问），附硬性数字基线与自查清单 | `npx skills add MoYan1638/moyan-skills/ui-patterns` |
| video-pipeline | 生产流程 | AI 视频生产流水线七步法：拆解爆款→Vibe Coding 画面骨架→AI 画师素材→动效优化→配音音效，附每步验收标准、翻车避坑清单（工程路径隔离/时间轴配置化）与批量生产标准化自查；附 [20 种全代码生成风格手册](video-pipeline/code-style-styles.md)（风格→现实材质对应、选型决策表、技术契约、真实感 8 层、渲染与响度自检） | `npx skills add MoYan1638/moyan-skills/video-pipeline` |
| enterprise-ai-agent | 落地方法 | 企业专属 AI 智能体八层封装：系统提示词身份约束→RAG 知识库防瞎编→MCP 工具连接→角色权限管控→提示词注入与安全护栏→缓存与模型路由控成本→可观测性与评测回归，附从 demo 到上线八步清单、按企业规模选路径与 6 问自检 | `npx skills add MoYan1638/moyan-skills/enterprise-ai-agent` |
| liquid-glass-ui | 质量规范 | 液态玻璃界面生产工艺：五步玻璃工艺 + 背景三原则 + 实测避坑，附完整模板 | `npx skills add MoYan1638/moyan-skills/liquid-glass-ui` |
| metal-card-generator | 质量规范 | 工业级金属质感卡片生产工艺：冷金属/磨砂/亮面/暗色四风格配色表 + 方向性明暗 + 四层质感结构 + 同心圆角算法 + 三态交互，附完整模板与演示页 | `npx skills add MoYan1638/moyan-skills/metal-card-generator` |
| review-precheck | 质量规范 | 小程序/App 提审前五项合规预检，产出"可提/改完再提/提了也拒"判定 | `npx skills add MoYan1638/moyan-skills/review-precheck` |
| decision-loop | 思维决策 | 决策闭环三阶段：事前参谋（摸底牌/收敛分歧/行动方案）→ 拍板留档（决策日志）→ 事后复盘（四问一卡），自动联动 | `npx skills add MoYan1638/moyan-skills/decision-loop` |
| github-publisher | 工具提效 | GitHub 发布生产线：建仓→上传→配 topics→验证，内置踩坑硬规则 | `npx skills add MoYan1638/moyan-skills/github-publisher` |
| infra-ledger | 工具提效 | 基建台账：域名/服务器/证书/映射关系登记与查询，到期自动预警 | `npx skills add MoYan1638/moyan-skills/infra-ledger` |

## 版本说明

v2 起合并同类技能，减少单次任务需加载的数量：

- `feedback-ui` + `form-patterns` + `sidebar-navigation` → **ui-patterns**（设计一个界面往往三者同时要查，合并后一次触发全覆盖）
- `strategic-advisor` + `decision-journal` + `retrospective-advisor` → **decision-loop**（事前/事中/事后本是一条流程，合并后自动衔接并联动）

## 为什么是这几类

- **质量规范类**：让 AI 的输出更好，而不是更快——没它 AI 也能写，但会写出不合格的界面/踩审核红线
- **思维决策类**：改变 AI 和你的协作方式——事前想清楚、拍板留档、事后学到位，构成完整决策闭环
- **工具提效类**：把重复劳动自动化——发布流程和资产台账，做一次流程化，之后一句话完成
- **生产流程类**：把「AI 一句话生成」拆成可标准化的多道工序——没它 AI 也能做，但产出均质、无风格、不可复用
- **落地方法类**：把一个通用模型改造成能上生产的企业级 Agent——没它也能跑 demo，但会瞎编、会越权、会被一句话骗走权限

各类共同点：都从真实踩坑经验里长出来，不是空想模板。

## 安装方式

单个安装用上表命令；也可把对应目录下的 `SKILL.md` 内容直接复制进你所用 Agent 的规则文件（`CLAUDE.md` / `AGENTS.md` / `.cursor/rules/` 等）。

## 持续更新

系列会持续扩充，新 skill 以表格新增一行。

## 许可

本系列采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh) 协议：个人学习与二次创作免费，需署名并附原仓库链接；**禁止商业用途（含倒卖、打包进付费产品）**，商用授权请联系作者。

# moyan-skills

墨言的 AI Agent Skill 系列（持续更新）。Agent Skills 开放格式，适配 Claude Code / Cursor / Codex / WorkBuddy 等任意编码助手。

## Skill 目录

| Skill | 类别 | 简介 | 安装命令 |
|---|---|---|---|
| ui-patterns | 质量规范 | 界面设计规范八合一：导航（侧边栏分组/选中态/折叠）+ 表单（13 种组件选型/校验时机/报错文案）+ 反馈（七种弹出层/七种加载组件/动效配方）+ 质感细节（色阶层次/暗色字重/排版防抖/输入法与滚动细节）+ 微交互动效（点赞爆粒子/提交三连变/果冻开关/长按确认配方与可运行示例）+ 效果决策与提示词库（18 个 UI 效果的场景决策表/AI 提示词/实现要点）+ 特殊控件八件套（徽标/数字输入框/时间轴/翻页器/边框流光/骨架屏/开关/走马灯的选型/硬规则/参数速查，附八控件全交互示例）+ 消除 AI 味（8 项体检扫描/九刀精修顺序/验收 5 问），附硬性数字基线与自查清单 | `npx skills add MoYan1638/moyan-skills/ui-patterns` |
| motion-patterns | 质量规范 | 页面级交互动效八合一：卡片堆叠甩动/弹性下拉刷新/大标题滚动收缩/骨架屏扫光渐显/浮动标签与错误抖动/拖拽排序/滑动删除加撤销/侧滑返回视差，每个动效附物理参数基准（时长/曲线/阈值三数字验收）、可直接使用的 AI 提示词、边界情况处理；公共设施四件：场景速选表（选档纪律：一页最多 1~2 个动效）、平台实现锚点（Compose/SwiftUI/H5/小程序四端 API 映射+只动 transform/opacity 的性能硬规则）、无障碍硬规则（非颜色区分/非手势等效路径/触控目标≥44pt）、六项验收清单（跟手逐帧回放/连触打断/实测帧率）；核心原则：物理手感优先禁线性生硬动画、跟手阶段与手指同步、可降级（reduced motion 直切+低端机掉帧降级） | `npx skills add MoYan1638/moyan-skills/motion-patterns` |
| button-patterns | 质量规范 | 高级按钮交互六合一：长按确认/点赞迸发/滑动确认/加入购物车飞入/主题切换扩散/复制反馈，核心方法"按钮是状态机"（强制覆盖初始-操作中-完成-恢复四态，两态按钮=没做完），每个方案附物理参数基准（按压≤120ms/长按1.5s按满350ms缓退/飞入500ms贝塞尔弧线/圆形扩散400ms）、可直接使用的 AI 提示词、边界情况处理；公共设施四件：场景速选表（选档纪律：一界面仅 1 个主行动按钮配高级动效）、平台实现锚点（四端 API 映射+小程序动效走 CSS 防 setData 卡顿）、无障碍硬规则（非颜色区分/读屏播报/**长按与滑动确认必须给等效替代路径**）、五项验收清单；与 ui-patterns 微交互动效配方参数对齐不冲突 | `npx skills add MoYan1638/moyan-skills/button-patterns` |
| video-pipeline | 生产流程 | AI 视频生产流水线七步法：拆解爆款→Vibe Coding 画面骨架→AI 画师素材→动效优化→配音音效，附每步验收标准、翻车避坑清单（工程路径隔离/时间轴配置化）与批量生产标准化自查；附 [20 种全代码生成风格手册](video-pipeline/code-style-styles.md)（风格→现实材质对应、选型决策表、技术契约、真实感 8 层、渲染与响度自检） | `npx skills add MoYan1638/moyan-skills/video-pipeline` |
| idea-to-code | 生产流程 | 从 0 到 1 的 AI 软件开发全流程十步法：需求分析→低保真原型→概要设计→高保真原型→详细设计→UI 设计→编码→第三方服务接入→测试→部署上线，铁律"前 6 步定清楚才许写代码"杜绝逻辑冲突反复推翻；每步产出书面文档供确认、出问题回退上一步，附引导提问清单、每步通过标准、30 秒选档（正式产品全走/小工具 Lite 合并版）、第三方依赖提前盘点与密钥安全规范、按任务选 AI 模型组合原则、9 类常见翻车根因对照表，全类型软件/APP/小程序/网站通用 | `npx skills add MoYan1638/moyan-skills/idea-to-code` |
| solo-commercial-app | 生产流程 | 单人结合 AI 搭建商业级应用十步法：商业定位→需求分期→架构选型→数据库设计→接口契约→分模块开发→联调测试→安全审计→灰度发布→上线迭代，面向真实付费用户商业项目，专治范围膨胀/风险裸奔/闭门造车；MVP 锁范围+变更评估、契约冻结前后端并行开发、六项安全自查、回滚先演练再灰度、告警通路实测、商业假设被数据证伪回第一步止损，附 10 类翻车对照表与全程风险清单/回滚方案/部署记录滚动文档 | `npx skills add MoYan1638/moyan-skills/solo-commercial-app` |
| enterprise-ai-agent | 落地方法 | 企业专属 AI 智能体八层封装：系统提示词身份约束→RAG 知识库防瞎编→MCP 工具连接→角色权限管控→提示词注入与安全护栏→缓存与模型路由控成本→可观测性与评测回归，附从 demo 到上线八步清单、按企业规模选路径与 6 问自检 | `npx skills add MoYan1638/moyan-skills/enterprise-ai-agent` |
| liquid-glass-ui | 质量规范 | 液态玻璃界面生产工艺：五步玻璃工艺 + 背景三原则 + 实测避坑，附完整模板 | `npx skills add MoYan1638/moyan-skills/liquid-glass-ui` |
| metal-card-generator | 质量规范 | 工业级金属质感卡片生产工艺：冷金属/磨砂/亮面/暗色四风格配色表 + 方向性明暗 + 四层质感结构 + 同心圆角算法 + 三态交互，附完整模板与演示页 | `npx skills add MoYan1638/moyan-skills/metal-card-generator` |
| app-review-checklist | 质量规范 | 小程序/App 提审前五项合规预检，产出"可提/改完再提/提了也拒"判定 | `npx skills add MoYan1638/moyan-skills/app-review-checklist` |
| demo-to-prod | 质量规范 | 生产硬化四步流（全类别 App 通用，附 Lite/Full 选档）：把 AI 生成的"可运行 Demo"转化为可上线生产级 App——验收标准四维度（核心业务/性能/安全/体验，逐条编号）→自动化代码约束（原子性/幂等/状态机收敛/参数化查询/权限校验/隐私加密，ArchUnit 等工具拦截）→AI 病灶体检（吞异常/假幂等/Mock 永真等 8 类命中即打回）+真实环境并发/失败注入/性能/安全测试+追溯矩阵防假覆盖→要害逻辑人工审核，任一环节不过即终止，产出上线报告与三态判定 | `npx skills add MoYan1638/moyan-skills/demo-to-prod` |
| decision-loop | 思维决策 | 决策闭环三阶段：事前参谋（摸底牌/收敛分歧/行动方案）→ 拍板留档（决策日志）→ 事后复盘（四问一卡），自动联动 | `npx skills add MoYan1638/moyan-skills/decision-loop` |
| github-publisher | 工具提效 | GitHub 发布生产线：建仓→上传→配 topics→验证，内置踩坑硬规则 | `npx skills add MoYan1638/moyan-skills/github-publisher` |
| infra-inventory | 工具提效 | 基建台账：域名/服务器/证书/映射关系登记与查询，到期自动预警 | `npx skills add MoYan1638/moyan-skills/infra-inventory` |

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

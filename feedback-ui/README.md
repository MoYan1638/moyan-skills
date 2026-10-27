> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

# feedback-ui

UI 反馈设计规范（弹出层 + 加载状态）—— 一份**模型无关、平台无关**的 UI 设计 Skill，可被任何 AI 编码助手加载，也适合人类开发者直接阅读。

AI 生成界面最常见的两类毛病：一是**弹出层滥用**（该用 Toast 的地方弹 Modal，删除强插二次确认，按钮文案清一色「是/否」），二是**加载状态乱给**（接口拿不到进度却写匀速假进度条，整页等待只给一个孤零零的转圈）。本 skill 把实战踩坑出来的规范变成 AI 能直接执行的设计约束。

> 兼容 [Agent Skills](https://agentskills.io) 开放规范（`SKILL.md` 格式），与 WorkBuddy / Claude Code / Cursor / Codex / Gemini CLI 等主流 Agent 的技能体系互通。

## 内容速览

**第一部分：弹出层怎么选**
- **六类速查表**：Tooltip / Toast / Alert / Popconfirm / Drawer / Modal 的打扰度、消失方式、适用场景对比
- **三问选型法**：①只是传达信息？②需要确认动作？③需要输入大量内容？顺着问完答案自然出来
- **六条硬性规则**：填表弹窗禁蒙层关闭、删除默认走撤销、按钮文案写动作、Toast 单条上限、Alert 黄红语义、Modal 禁套娃
- **移动端差异**：Modal → 全屏/半屏 Sheet、Tooltip → 长按提示、触摸目标 ≥ 44px

**第二部分：加载状态怎么选**
- **四组件选型表**：Spinner（不知耗时）/ Progress（有真实进度回调）/ Skeleton（整页首屏）/ Typing（对话生成中）
- **与弹出层搭配**：Modal 提交按钮内嵌 Spinner、Drawer 远程数据先上骨架、Toast 只做结果反馈不带加载
- **避坑五条**：不叠加 loading、加载锁交互、骨架对齐 DOM、禁假进度、动画克制

**正误对照**：11 个真实场景的「该用 / 别用」速查表

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/feedback-ui
```

### 方式二：WorkBuddy

将 `SKILL.md` 所在的 `feedback-ui` 文件夹放入技能目录：

```
~/.workbuddy/skills/feedback-ui/SKILL.md
```

重启会话即生效，对话涉及弹窗或加载动画设计时自动触发。

### 方式三：Claude Code / Codex / Cursor 等

没有独立技能目录的 Agent，把 `SKILL.md` 的内容追加到项目的 Agent 规则文件里即可：

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/feedback-ui.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——它本身就是一份 3 分钟能读完的设计规范，评审 UI 方案时拿来当 checklist 用。

## 使用示例

安装后，对 Agent 说：

> 「帮我设计删除文章的确认交互」

Agent 会按本规范给出：可撤销操作直接执行 + 带「撤销」按钮的 Toast，只有不可逆操作才上 Modal，且按钮文案是「放弃 / 确认删除」而非「否 / 是」。

> 「这个页面加载的时候给个进度条吧，写个假的匀速动画」

Agent 会拒绝伪造进度：拿不到真实进度回调就改用 Spinner，只有后端能报进度时才用 Progress。

## 作者

**墨言**（[MoYan1638](https://github.com/MoYan1638)）

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

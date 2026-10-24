> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

# popup-layer-ui

弹出层（Popup Layer）选型与设计规范 —— 一份**模型无关、平台无关**的 UI 设计 Skill，可被任何 AI 编码助手加载，也适合人类开发者直接阅读。

当设计或实现 UI 中的提示、反馈、确认框、弹窗、抽屉等临时交互层时，本 skill 提供一套可执行的选型决策与硬性规则，确保弹出层类型选择一致、打扰度最小、文案符合规范。

> 兼容 [Agent Skills](https://agentskills.io) 开放规范（`SKILL.md` 格式），与 WorkBuddy / Claude Code / Cursor / Codex / Gemini CLI 等主流 Agent 的技能体系互通。

## 它解决什么问题

AI 生成界面时最常见的毛病之一就是弹出层滥用：该用 Toast 的地方弹 Modal，该走「撤销」的删除却强插二次确认，按钮文案清一色「是/否」。本 skill 把一套实战踩坑出来的规范变成 AI 能直接执行的设计约束。

## 内容速览

- **六类速查表**：Tooltip / Toast / Alert / Popconfirm / Drawer / Modal 的打扰度、消失方式、适用场景对比
- **三问选型法**：①只是传达信息？②需要确认动作？③需要输入大量内容？顺着问完答案自然出来
- **六条硬性规则**：填表弹窗禁蒙层关闭、删除默认走撤销、按钮文案写动作、Toast 单条上限、Alert 黄红语义、Modal 禁套娃
- **移动端差异**：Modal → 全屏/半屏 Sheet、Tooltip → 长按提示、触摸目标 ≥ 44px
- **正误对照示例**：8 个真实场景的「该用 / 别用」

核心排序：**Tooltip < Toast < Alert < Popconfirm < Drawer < Modal**
（Modal 才是完全打断；Drawer 虽面积大但不打断主流程，不要按面积判断打扰度。）

## 安装

### 方式一：通用 Skills CLI（推荐）

支持任何遵循 Agent Skills 规范的 Agent：

```bash
npx skills add MoYan1638/popup-layer-ui
```

### 方式二：WorkBuddy

将 `SKILL.md` 所在的 `popup-layer-ui` 文件夹放入技能目录：

```
~/.workbuddy/skills/popup-layer-ui/SKILL.md
```

重启会话即生效，对话涉及弹窗设计时自动触发。

### 方式三：Claude Code / Codex / Cursor 等

没有独立技能目录的 Agent，把 `SKILL.md` 的内容追加到项目的 Agent 规则文件里即可：

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/popup-layer-ui.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——它本身就是一份 3 分钟能读完的设计规范，评审 UI 方案时拿来当 checklist 用。

## 使用示例

安装后，对 Agent 说：

> 「帮我设计删除文章的确认交互」

Agent 会按本规范给出：可撤销操作直接执行 + 带「撤销」按钮的 Toast，只有不可逆操作才上 Modal，且按钮文案是「放弃 / 确认删除」而非「否 / 是」。

## 作者

**墨言**（[MoYan1638](https://github.com/MoYan1638)）

## License

MIT

# liquid-glass-ui

有层次的液态玻璃（Glassmorphism）界面生产工艺，教 AI 生成真正有质感的玻璃拟态界面——而不是"一块毛玻璃板浮在纯色上"。

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

## 它解决什么问题

AI 生成的玻璃拟态界面通常有两个通病：**玻璃没有质感**（漏掉增色和叠白，发灰像脏玻璃）、**背景没有层次**（细碎纹理被 blur 平均成一团糊）。这个 skill 把两者固化成可严格执行的流水线：

- **五步玻璃工艺**：模糊 → 增色 → 叠白 → 亮边 → 折射，参数与顺序固定
- **背景三原则**：大块柔和形状、主色 1-2 种、玻璃下方压暗保可读
- **三禁令**：禁细碎背景 / 禁纯色背景 / 禁杂色背景
- **实测增量规则**（教程里没有的部分）：
  - 叠白浓度随背景深度微调（深色底 8%、标准 10%）
  - 嵌套玻璃层次法则（内层更淡、更细、更低模糊）
  - 折射层仅 Chrome/Edge 支持，必须先写 blur 兜底声明优雅降级
- 附带一个验证过的完整参考模板（`template.html`，极光音乐卡）

## 安装

```bash
# 通用 Skills CLI（Claude Code / Cursor / Codex 等支持 Agent Skills 的环境）
npx skills add MoYan1638/moyan-skills/liquid-glass-ui
```

其他方式：

- **WorkBuddy**：将整个文件夹放入 `~/.workbuddy/skills/liquid-glass-ui/`
- **Claude Code / Codex**：将 SKILL.md 内容追加到项目的 `CLAUDE.md` / `AGENTS.md`
- **Cursor / Copilot**：追加到 `.cursor/rules/` 或 `.github/copilot-instructions.md`
- **人类**：直接读 SKILL.md，5 分钟掌握，当 CSS 评审 checklist 用

## 触发方式

对 AI 说：

- "用液态玻璃风格做一个 XX 界面"
- 或在天气卡、播放器、落地页等场景，AI 会主动提议采用此工艺

## 使用示例

安装后，AI 生成的代码会带上这样的注释标注（可逐条对照验收）：

```css
.glass-card {
  backdrop-filter: blur(28px) saturate(170%);   /* ①模糊 + ②增色 */
  background: rgb(255 255 255 / 10%);            /* ③叠白 */
  box-shadow: inset 1px 1px #fff8;               /* ④亮边 */
  backdrop-filter: blur(28px) saturate(170%), url(#lens); /* ⑤折射，仅 Chromium */
}
```

## 许可

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

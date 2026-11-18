# metal-card-generator 金属质感卡片

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

工业级金属质感 UI 卡片生产工艺。核心认知：金属感不是「灰色 + 阴影」，而是**方向性明暗**。

## 三件事决定它像不像金属

1. **明暗必须有方向** —— 上亮下暗、左上受光右下背光。纯平灰永远像纸板
2. **边缘厚度靠内高光** —— `inset` 顶部 1–2px 白线是金属的截面高光，缺了它就是一张贴纸
3. **纹理密度决定材质** —— 冷金属无纹理（轧制面），磨砂有细噪点，亮面有锐利反光带

## 四种风格

| 风格 | 材质对应 | 用在哪 |
|---|---|---|
| 冷金属 | 轧制钢板、拉丝铝 | 后台面板、数据卡、器械感界面 |
| 磨砂金属 | 喷砂阳极氧化 | 主打「高级但不刺眼」的产品页 |
| 亮面金属 | 抛光不锈钢、镀铬 | 需要反光和重量感的 Hero 区 |
| 暗色金属 | 黑化处理件 | 暗色主题里的卡片、仪表盘 |

## 规范里包含

- 四风格配色表（底色 / 高光 / 暗部 / 文字色，可直接抄）
- **同心圆角算法** —— 内外圆角不相等时看起来像贴了两层纸，公式给了正确写法
- **四层质感结构** —— 底色渐变 / 内高光 / 细纹理 / 外投影，缺一层就变纸板
- 磨砂噪点的正确写法（用错滤镜会糊成一片）
- 三态交互（默认 / 悬停 / 按下）与可访问性补偿
- 完整可粘贴模板 + 五条禁令 + 输出要求

## 示例

[`metal-cards-demo.html`](./metal-cards-demo.html)：四种风格同屏对比，含三态交互，纯 HTML/CSS 零依赖，直接打开看。

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/metal-card-generator
```

### 方式二：WorkBuddy

```
~/.workbuddy/skills/metal-card-generator/SKILL.md
```

### 方式三：Claude Code / Codex / Cursor 等

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/metal-card-generator.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——里面有可整段粘贴的模板，改配色就能用。

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

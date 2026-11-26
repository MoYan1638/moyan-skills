# generate-app-icons

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

AI Agent App 图标生成生产线 —— **从产品定位到双平台交付，一次跑完，29px 下依然认得出。**

它把「生成一个图标」拆成标准五步（意象 → 配色 → 风格 → 生成 → 细节调整），并把四个开源图标技能的设计纪律内置成硬规则：

- 意象提炼用「物体 + 动作 + 情绪」三要素，不做名词搬运工
- 全图恰好三色，3–5 个大形状，主体占画布 62–72% 居中
- 提示词「用途隐藏」：绝不对生图模型说"图标"二字，否则它画的是手机主屏样机
- 三个方向必须在隐喻/轮廓/记忆点上真正不同，不是换色凑数
- 小尺寸验收（1024/180/60/32）与剪影测试不可跳过
- iOS 无透明通道不自画圆角、Android 自适应前景留 66% 安全区

装上之后，对 Agent 说"给这个 App 做个图标"，从心智推导到平台导出一步到位。

## 安装

```bash
npx skills add MoYan1638/moyan-skills/generate-app-icons
```

或直接把 `SKILL.md` 内容复制进你所用 Agent 的规则文件（`CLAUDE.md` / `AGENTS.md` / `.cursor/rules/` 等）。

## 方法论来源

规则均已消化重写、非照搬，致谢：

- [chunkithwang/design-playful-app-icons](https://github.com/chunkithwang/design-playful-app-icons)
- [Dwade8128/ip-skills-cn](https://github.com/Dwade8128/ip-skills-cn)（app-icon-master）
- [NeuralNomadsAI/CodeNomad](https://github.com/NeuralNomadsAI/CodeNomad)（design-app-icon）
- SkillMD《ios-app-icon-generator》

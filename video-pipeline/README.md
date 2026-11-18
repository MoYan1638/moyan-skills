# video-pipeline AI 视频生产流水线

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

一句话立场：**不要迷信一键生成**。直接把文案丢给视频模型，产出的一定是均质的、没有个人风格的内容。

正确做法是把生产拆成七道工序，每道工序 AI 只干一件事、干到精，最后像搭积木一样拼装。

## 七步流水线

1. **拆解爆款** —— 不是抄内容，是拆它的节奏结构和钩子位置
2. **Vibe Coding 画面骨架** —— 先用代码把画面逻辑跑通，再谈素材
3. **AI 画师素材** —— 按骨架生图，风格锚定在提示词里而不是事后调色
4. **动效优化** —— 让静态素材动起来，以及哪些动效会一眼假
5. **配音音效** —— 语速、停顿、响度，声音是完播率的分水岭
6. **翻车现场** —— 真实踩坑清单：工程路径隔离、时间轴配置化、批量时互相覆盖
7. **搭积木** —— 把整条链固化成模板，批量生产不再每期重做

## 配 20 种全代码风格手册

[`code-style-styles.md`](./code-style-styles.md)：风格→现实材质的对应关系、选型决策表、技术契约、真实感 8 层、渲染与响度自检。做「代码驱动的短视频/解说/知识类视频」时先查它选风格。

## 每步都有验收标准

七步不是流程清单，每一步都写了「什么样算过关」。写文案写完就交给下一步，通常会得到一条从头假到尾的片子。

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/video-pipeline
```

### 方式二：WorkBuddy

```
~/.workbuddy/skills/video-pipeline/SKILL.md
```

### 方式三：Claude Code / Codex / Cursor 等

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/video-pipeline.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)，配合 [`code-style-styles.md`](./code-style-styles.md) 一起看。

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

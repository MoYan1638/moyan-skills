# enterprise-ai-agent 企业专属 AI 智能体

> 🧩 本 skill 是 [MoYan1638/moyan-skills](https://github.com/MoYan1638/moyan-skills) 系列的一员，更多 skill 看那边。

把通用大模型改造成「懂企业、守规则、能办事」的生产级 Agent。一句话立场：**企业 AI 的核心不是「用了大模型」，而是把企业的业务规则、数据、权限、安全封装给模型。**

不做这八层封装，它就是个会说漂亮话的外人——会推荐竞争对手、会瞎编政策、会泄露薪资、会被一句「忽略你的指令」骗走全额退款。

## 八层封装

| 层 | 解决什么 |
|---|---|
| 1 系统提示词 | 身份与边界——它代表谁说话、什么不能说 |
| 2 RAG 知识库 | 瞎编——答不出就说答不出，别用通顺的假话圆场 |
| 3 工具连接（MCP） | 从「会聊」到「能办」，以及工具描述怎么写模型才用对 |
| 4 权限管控 | 同一个问题，不同角色看到不同答案 |
| 5 安全防护 | 提示词注入、越权操作、高风险动作二次确认 |
| 6 成本控制 | 缓存、模型路由、上下文裁剪——钱花在哪一层最值 |
| 7 可观测性 | 出错能查：留什么日志、留多深、怎么回放一轮坏回答 |
| 8 落地清单 | 从 demo 到生产的八步，每步的验收标准 |

## 按企业规模选路径

小团队先做 1、2、6，把「不瞎编 + 不烧钱」立住；中大型企业加 4、5、7，因为权限和审计是硬要求。**别一上来八层全铺**——先跑通一条真实业务线，再横向复制。

## 自检 6 问

答不上任何一个，说明还没做完：谁在用、什么场景下它必须说「不知道」、哪个角色不该看到哪张表、一次注入攻击能骗走什么、单次对话成本上限是多少、上线后第一周看哪三个数。

## 安装

### 方式一：通用 Skills CLI（推荐）

```bash
npx skills add MoYan1638/moyan-skills/enterprise-ai-agent
```

### 方式二：WorkBuddy

```
~/.workbuddy/skills/enterprise-ai-agent/SKILL.md
```

### 方式三：Claude Code / Codex / Cursor 等

- Claude Code → `CLAUDE.md`
- Codex / 通用 → `AGENTS.md`
- Cursor → `.cursor/rules/enterprise-ai-agent.mdc`
- GitHub Copilot → `.github/copilot-instructions.md`

### 方式四：人类阅读

直接打开 [`SKILL.md`](./SKILL.md)——它本身就是一份可当清单用的落地方法，评审方案时逐条对照。

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh)

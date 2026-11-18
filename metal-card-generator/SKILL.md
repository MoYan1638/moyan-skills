---
name: metal-card-generator
description: 工业级金属质感 UI 卡片生成工艺。当用户要求"金属卡片/金属质感卡片/金属风格 UI/工业风卡片/铝制卡片"或需要硬朗、精密、器械感界面时使用。含四种风格（冷金属/磨砂金属/亮面金属/暗色金属）的配色表、四层质感结构、同心圆角算法、三态交互与可直接粘贴的完整模板。
---

# 金属质感卡片生成工艺

核心认知：金属感不是"灰色 + 阴影"，而是**方向性明暗**。三件事决定它像不像金属：

1. **明暗必须有方向**——上亮下暗、左上受光右下背光。纯平灰永远像纸板。
2. **边缘厚度靠内高光**——`inset` 顶部 1-2px 白线是金属的截面高光，缺了它就是一张贴纸。
3. **纹理密度决定材质**——冷金属无纹理（轧制面），磨砂有细噪点，亮面有锐利反光带。

## 一、四风格速选表

| 风格 | 适用场景 | 表面值 | 高光强度 | 纹理 |
|---|---|---|---|---|
| 冷金属 cold | 后台面板、数据卡、器械 UI | `#f5f5f5 → #dcdcdc` | 28% 白 | 拉丝 7% 竖纹 |
| 磨砂金属 frosted | 硬件产品页、工具类 App | `#d0d0d0 → #c0c0c0` | 15% 白 | 噪点 5% |
| 亮面金属 polished | 高端硬件、音箱/相机、Hero 区 | `#f0f0f0 → #cfcfcf` | 顶 2px 硬高光 95% | 斜向反光带 |
| 暗色金属 dark | 深色模式、游戏 UI、暗色仪表盘 | `#2e2e2e → #1f1f1f` | 10% 白 | 无 |

**选型规则**：页面底色明度 > 70% 用前三种；< 30% 必须用 `dark`——浅色金属贴在深底上会"浮起来"。

## 二、同心圆角算法（原规范此处有误，按此执行）

正确公式：**内层圆角 = 外层圆角 − 内边距**

本工艺固定值：外层 `20px` / 内边距 `16px` / 内层 `4px`。

- 若内边距 ≥ 外层圆角，内层必须取 `0`（直角），**不要取 1-2px 的碎圆角**，视觉上显脏。
- 常见错误写法：外层 12 + 内边距 16 + 内层 8 —— 三者互相矛盾，8+16≠12，成稿必然违和。

## 三、尺寸与响应式

| 项 | 值 |
|---|---|
| 默认宽度 | `320px` |
| ≥768px | 宽度 `100%`（栅格内自适应） |
| ≥1200px | 固定 `360px` |
| 高度 | 自适应，`min-height:120px`，`max-height:480px` |
| 内边距 | `16px`（四边统一） |

`max-height` 配 `overflow:hidden`，内容溢出时在内容区内部滚动，不要撑破卡片。

## 四、四层质感结构（缺一层就会"变纸板"）

按顺序叠，全部写在同一个 `box-shadow` 里或分层伪元素：

1. **底色渐变**：`linear-gradient(180deg, 亮 → 暗)`
2. **1px 渐变边框**（135deg）：用 `::after` + `mask` 做真实渐变描边，`border-image` 不支持圆角
3. **内高光 / 内暗边**：`inset 0 2px 4px rgba(255,255,255,.28)` + `inset 0 -2px 4px rgba(0,0,0,.18)`
4. **发丝轮廓 + 外投影**：`0 0 0 1px rgba(0,0,0,.04)` 保证浅底上卡片边界清晰，再 `0 4px 8px rgba(0,0,0,.2)` 出厚度

第 4 条的 `0 0 0 1px` 很关键：浅灰金属放在近白背景上，1px 渐变边框几乎看不见，卡片会"化"进背景。这一圈 4% 黑把轮廓钉住。

亮面金属（`polished`）的顶/底不对称表达——`box-shadow` 做不到"顶硬底软"，所以顶部改用 **0 模糊的实心 inset**：

```css
box-shadow:
  inset 0 2px 0 rgba(255,255,255,.9),      /* 顶 2px 硬高光，镜面反光 */
  inset 0 -3px 6px rgba(0,0,0,.18),        /* 底 4px 深阴影，厚度 */
  0 4px 8px rgba(0,0,0,.2);
```

## 五、磨砂噪点正确写法（原规范踩坑点）

**不要**把噪点 SVG 直接塞进 `background` 简写里——它会与渐变互相覆盖，且噪点层参与命中测试，导致点击区域异常。

正确做法：`::before` 承载 + `pointer-events:none` + `mix-blend-mode:overlay`：

```css
.metal-card::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: inherit;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.05'/%3E%3C/svg%3E");
  background-repeat: repeat;
  background-size: 120px 120px;
  mix-blend-mode: overlay;
  pointer-events: none;
  z-index: 0;
}
```

`background-size` 必须显式给（默认 100% 会拉伸成一块模糊灰），`120px` 是实测最稳的颗粒尺度。卡片内所有内容需要 `position:relative; z-index:1` 盖在噪点之上。

## 六、三态交互（原规范补充可访问性）

| 状态 | 变化 | 过渡 |
|---|---|---|
| 默认 | 见四层结构 | — |
| hover | 上移 2px；阴影加深至 `0 6px 12px rgba(0,0,0,.25)`；内高光升至 `.2` | `0.3s ease` |
| active | 下移 1px（相对默认）；阴影收敛至 `0 2px 4px rgba(0,0,0,.15)` | `0.1s` |
| disabled | `opacity:.6`；阴影降至 `0 1px 2px rgba(0,0,0,.1)`；`pointer-events:none` | — |
| focus-visible | `outline:2px solid #4a90d9; outline-offset:2px` | — |

`transform` 动画必须配 `will-change: transform`，否则 Safari 上会出现 1px 抖动。

## 七、内容适配

| 元素 | 规格 |
|---|---|
| 标题 | `18px / 600 / 1.5 / #333` |
| 正文 | `14px / 400 / 1.6 / #666` |
| 按钮 | 高 `36px`，圆角 `8px`，背景 `#e0e0e0`，hover `#d0d0d0`，文字 `#333` |
| 图标 | SVG，`24px`，色 `#666`，hover `#333` |

暗色金属需整体换色：标题 `#f0f0f0`、正文 `#a8a8a8`、按钮背景 `#3a3a3a` / hover `#474747` / 文字 `#e8e8e8`。

## 八、完整模板（可直接粘贴）

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Metal Card</title>
<style>
  :root {
    --radius-outer: 20px;
    --radius-inner: 4px;
    --pad: 16px;
  }

  .metal-card {
    /* 冷金属为默认档 */
    --surface-1: #f5f5f5;
    --surface-2: #dcdcdc;
    --highlight: rgba(255, 255, 255, .28);
    --shade: rgba(0, 0, 0, .18);
    --ring-1: #e0e0e0;
    --ring-2: #b0b0b0;

    position: relative;
    isolation: isolate;
    box-sizing: border-box;
    width: 320px;
    min-height: 120px;
    max-height: 480px;
    padding: var(--pad);
    border-radius: var(--radius-outer);
    overflow: hidden;
    background: linear-gradient(180deg, var(--surface-1) 0%, var(--surface-2) 100%);
    box-shadow:
      inset 0 2px 4px var(--highlight),
      inset 0 -2px 4px var(--shade),
      0 0 0 1px rgba(0, 0, 0, .04),
      0 4px 8px rgba(0, 0, 0, .2);
    transition: transform .3s ease, box-shadow .3s ease;
    will-change: transform;
  }

  /* 2. 1px 渐变边框（border-image 不支持圆角，必须用 mask 方案） */
  .metal-card::after {
    content: "";
    position: absolute;
    inset: 0;
    border-radius: inherit;
    padding: 1px;
    background: linear-gradient(135deg, var(--ring-1), var(--ring-2));
    -webkit-mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
    -webkit-mask-composite: xor;
    mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
    mask-composite: exclude;
    pointer-events: none;
  }

  /* 1. 冷金属拉丝纹理（7% 竖纹，方向必须统一，交叉纹=牛仔布） */
  .metal-card[data-style="cold"] {
    background-image:
      repeating-linear-gradient(90deg,
        rgba(255, 255, 255, .07) 0 1px,
        transparent 1px 2px,
        rgba(0, 0, 0, .025) 2px 3px),
      linear-gradient(180deg, var(--surface-1) 0%, var(--surface-2) 100%);
  }

  /* 磨砂：噪点由 ::before 承载 */
  .metal-card[data-style="frosted"] {
    --surface-1: #d0d0d0;
    --surface-2: #c0c0c0;
    --highlight: rgba(255, 255, 255, .15);
    --shade: rgba(0, 0, 0, .20);
    --ring-1: #d8d8d8;
    --ring-2: #a8a8a8;
  }
  .metal-card[data-style="frosted"]::before {
    content: "";
    position: absolute;
    inset: 0;
    border-radius: inherit;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.05'/%3E%3C/svg%3E");
    background-repeat: repeat;
    background-size: 120px 120px;
    mix-blend-mode: overlay;
    pointer-events: none;
    z-index: 0;
  }

  /* 亮面：顶 2px 实心高光 + 斜向镜面反光带 */
  .metal-card[data-style="polished"] {
    --surface-1: #f0f0f0;
    --surface-2: #cfcfcf;
    --ring-1: #fafafa;
    --ring-2: #a0a0a0;
    box-shadow:
      inset 0 2px 0 rgba(255, 255, 255, .95),
      inset 0 -3px 6px rgba(0, 0, 0, .22),
      0 0 0 1px rgba(0, 0, 0, .05),
      0 4px 8px rgba(0, 0, 0, .2);
    background-image:
      linear-gradient(158deg,
        rgba(255, 255, 255, .90) 0%,
        rgba(255, 255, 255, .35) 12%,
        rgba(255, 255, 255, 0) 34%,
        rgba(255, 255, 255, 0) 62%,
        rgba(0, 0, 0, .04) 100%),
      linear-gradient(180deg, var(--surface-1) 0%, var(--surface-2) 100%);
  }

  /* 暗色金属 */
  .metal-card[data-style="dark"] {
    --surface-1: #2e2e2e;
    --surface-2: #1f1f1f;
    --ring-1: #4a4a4a;
    --ring-2: #2a2a2a;
    box-shadow:
      inset 0 1px 0 rgba(255, 255, 255, .10),
      inset 0 -2px 4px rgba(0, 0, 0, .50),
      0 6px 16px rgba(0, 0, 0, .45);
    color: #e8e8e8;
  }

  /* 内容层必须压住噪点 */
  .metal-card__body { position: relative; z-index: 1; }

  .metal-card__title {
    margin: 0 0 8px;
    font-size: 18px;
    font-weight: 600;
    line-height: 1.5;
    color: #333;
  }
  .metal-card__text {
    margin: 0 0 12px;
    font-size: 14px;
    font-weight: 400;
    line-height: 1.6;
    color: #666;
  }
  .metal-card[data-style="dark"] .metal-card__title { color: #f0f0f0; }
  .metal-card[data-style="dark"] .metal-card__text { color: #a8a8a8; }

  .metal-card__actions { display: flex; gap: 8px; }

  .metal-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 6px;
    height: 36px;
    padding: 0 14px;
    border: none;
    border-radius: 8px;
    background: #e0e0e0;
    color: #333;
    font-size: 14px;
    cursor: pointer;
    transition: background .2s ease;
  }
  .metal-btn:hover { background: #d0d0d0; }
  .metal-card[data-style="dark"] .metal-btn { background: #3a3a3a; color: #e8e8e8; }
  .metal-card[data-style="dark"] .metal-btn:hover { background: #474747; }

  .metal-icon { width: 24px; height: 24px; color: #666; }
  .metal-icon:hover { color: #333; }

  /* 三态（注意：覆盖 box-shadow 时要把发丝轮廓 0 0 0 1px 一起带上） */
  .metal-card:hover {
    transform: translateY(-2px);
    box-shadow:
      inset 0 3px 6px rgba(255, 255, 255, .26),
      inset 0 -2px 4px rgba(0, 0, 0, .18),
      0 0 0 1px rgba(0, 0, 0, .04),
      0 6px 12px rgba(0, 0, 0, .25);
  }
  .metal-card:active {
    transform: translateY(-1px);
    box-shadow:
      inset 0 1px 3px rgba(255, 255, 255, .20),
      inset 0 -1px 2px rgba(0, 0, 0, .18),
      0 0 0 1px rgba(0, 0, 0, .04),
      0 2px 4px rgba(0, 0, 0, .15);
    transition-duration: .1s;
  }
  .metal-card.is-disabled {
    opacity: .6;
    pointer-events: none;
    box-shadow:
      inset 0 1px 2px rgba(255, 255, 255, .10),
      0 1px 2px rgba(0, 0, 0, .1);
  }
  .metal-card:focus-visible {
    outline: 2px solid #4a90d9;
    outline-offset: 2px;
  }

  /* 响应式 */
  @media (max-width: 767px) {
    .metal-card { width: 100%; }
  }
  @media (min-width: 1200px) {
    .metal-card { width: 360px; }
  }
</style>
</head>
<body>
  <article class="metal-card" data-style="cold" tabindex="0">
    <div class="metal-card__body">
      <h2 class="metal-card__title">冷金属卡片</h2>
      <p class="metal-card__text">轧制面处理，无纹理，适合数据面板与器械类界面。</p>
      <div class="metal-card__actions">
        <button class="metal-btn">查看详情</button>
      </div>
    </div>
  </article>
</body>
</html>
```

## 九、五条禁令

- **禁纯平灰**：必须有 `180deg` 明暗渐变，否则是纸板不是金属
- **禁无内高光**：顶部 inset 是高光截面，删了立刻变廉价
- **禁阴影堆叠超过 4 层**：脏。四层结构已经足够
- **禁浅色金属贴深色底**：改用 `dark` 变体
- **禁违反同心公式**：内层圆角必须是外层减内边距，否则边角会"错位"

## 十、输出要求

- 直接输出完整 HTML + CSS，无解释文字，可直接复制运行
- 不依赖任何第三方库，全部原生 CSS
- 兼容 Chrome / Firefox / Safari / Edge（`mask-composite` 需同时写 `-webkit-` 前缀）
- 一屏多卡时统一 `data-style`，不要在同一个视图里混用亮面与磨砂（材质不统一会显得随意）

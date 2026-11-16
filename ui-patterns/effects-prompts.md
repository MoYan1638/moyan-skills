# 效果提示词库：18 个可直接复用的 UI 效果 + AI 提示词

用法：把提示词原样喂给 AI（或自己实现时当需求描述）。每个提示词刻意写得很"具体"——**说清楚触发方式、运动方式、边界情况**，这是 AI 一次生成正确的关键。改效果时保留这个结构，只换参数。

## 分类速查

| 类别 | 效果 |
|---|---|
| 背景氛围 | 1 极光渐变 · 6 粒子连线 · 7 鼠标跟随光晕 |
| 按钮 | 2 磁吸按钮 · 8 流光边框 · 11 点击水波纹 |
| 卡片与图片 | 3 毛玻璃导航栏 · 4 3D翻转卡片 · 9 图片对比滑块 · 12 图片悬停放大 · 13 滚动堆叠卡片 |
| 文字 | 5 打字机文字 · 17 流动渐变文字 · 18 文字悬浮弹窗 |
| 滚动与导航 | 14 阅读进度条 · 15 滚动隐藏导航栏 |
| 数据与品牌 | 10 数字滚动统计 · 16 无缝滚动Logo墙 |

---

## 1. 极光渐变背景
> 请给首页背景加上「极光渐变背景」：几团彩色光斑缓慢漂移、互相融合，再叠一层很淡的噪点。

要点：光斑用大半径 blur 的径向渐变层 + `filter: blur()`，动画用 transform 位移（别动 left/top）；噪点用 SVG feTurbulence 或半透明 PNG，opacity 控制在 3%~5%。

## 2. 磁吸按钮
> 请给「页面上最重要的那个按钮」加上磁吸效果：鼠标进入按钮边缘外约 80px 时，按钮朝鼠标方向偏移，离开后带轻微回弹回到原位；只响应鼠标，触屏和开启动画时不生效。

要点：监听一个比按钮大的透明热区（或全局 mousemove + 距离计算），偏移量 = 向量 × 系数（最大 10~15px），离开用 `cubic-bezier(.34,1.56,.64,1)` 回弹；`@media (hover:hover)` 包裹，`prefers-reduced-motion` 时禁用。

## 3. 毛玻璃导航栏
> 请做一个毛玻璃导航栏：像苹果官网那样半透明，往下滚动时能隐约看到下面的内容。

要点：`backdrop-filter: blur(12px) saturate(1.5)` + 半透明底色（如 rgba(255,255,255,.72)）；必须有纯色/渐变 fallback（@supports），导航栏要 `position: sticky`。

## 4. 3D 翻转卡片
> 请做一个 3D 翻转卡片：鼠标放上去时卡片会翻转过来，背面显示个人简介。

要点：外层 `perspective: 1000px`，内层 `transform-style: preserve-3d` + rotateY(180deg)，正反两面 `backface-visibility: hidden`；背面文字要反向转回来。触屏改为点击切换。

## 5. 打字机文字
> 请做一个打字机文字效果：标题后半句像打字一样一个一个出来，再删掉换下一个。

要点：JS 逐字符追加/删除，光标用 `border-right` + blink 动画；循环多句时维护句数组 + 打字/删除/停顿三个状态；打字速度 ~120ms/字，删除 ~60ms/字，句末停 1.5s。给容器预留最大宽度防止布局跳动。

## 6. 粒子连线背景
> 请做一个粒子连线背景：首页背景做成光点慢慢飘、离得近就连线的科技感效果。

要点：canvas 全屏铺底 `z-index:-1`，粒子 60~120 个、随机速度缓慢漂移、越界环绕；两粒子距离 < 120px 时画线，线透明度随距离衰减；连线用 O(n²) 距离判断，粒子多时加空间网格。鼠标附近粒子轻微排斥可加分。

## 7. 鼠标跟随光晕
> 请做一个鼠标跟随光晕：鼠标像手电筒一样，照到哪里哪里亮。

要点：一个大的径向渐变 div（`pointer-events:none`）用 `transform: translate()` 跟随，动画帧里做 lerp（当前值向目标值靠拢 0.1）产生拖尾感；暗色页面上 `mix-blend-mode: screen` 效果最好。

## 8. 流光边框按钮
> 请做一个流光边框按钮：按钮边框有一圈彩色的光在转。

要点：conic-gradient 旋转法——按钮外包一层 `background: conic-gradient(色1,色2,色1)` + `animation: spin`，内层按钮留 2px 缝隙遮出边框感；或 @property 注册 `--angle` 让 conic-gradient 本身转。记得 `overflow:hidden` 圆角同心。

## 9. 图片对比滑块
> 请做一个图片对比滑块：展示改版前后，中间一条线，左右拖着对比。

要点：前后两张图绝对定位重叠，上层用 `clip-path: inset(0 X% 0 0)` 裁切，中间竖线 + 圆形把手跟随手势；支持鼠标拖动和触摸，`touch-action:none` 防滚动冲突；两图必须同尺寸对齐。

## 10. 数字滚动统计
> 请做一个数字滚动统计：数字从 0 一路数上去。

要点：IntersectionObserver 进入视口才触发（只触发一次）；用 requestAnimationFrame + easeOutCubic 插值，时长 1.5~2s；大数字用 `toLocaleString()` 加千分位，小数位固定。

## 11. 点击水波纹按钮
> 请做一个点击水波纹按钮：点哪里，哪里冒出波纹。

要点：点击时在按钮内创建一个定位到点击坐标的圆形 span，scale 从 0 到覆盖按钮（直径 = 按钮对角线 × 2.2），600ms 后移除；按钮 `overflow:hidden; position:relative`。Material Design 经典做法。

## 12. 图片悬停放大
> 请做一个图片悬停放大：鼠标一放，图片放大、说明浮出来。

要点：容器 `overflow:hidden`，图片 `transform: scale(1.08)` 过渡 0.4s（别动 width/height），说明层从底部滑入（translateY(100%)→0）+ 淡入；移动端退化为常显说明。

## 13. 滚动堆叠卡片
> 请做一个滚动堆叠卡片：往下滚，卡片一张张叠起来。

要点：CSS `position: sticky; top: Npx` 就能做纯 CSS 版——每张卡 sticky 在略不同 top 值，自然形成堆叠；进阶版用 JS 监听滚动给后面的卡加 scale 缩小 + 亮度变暗。每张卡高度一致、外层留够滚动长度。

## 14. 阅读进度条
> 请做一个阅读进度条：读到哪，进度条就到哪。

要点：固定在顶部 2~3px 条，宽度 = `scrollY / (docHeight - innerHeight)`；在 rAF 里更新并直接设 `transform: scaleX()`（transform-origin: left），别动 width；移动端也可放刘海下沿。

## 15. 滚动隐藏导航栏
> 请做一个滚动隐藏导航栏：往下滑藏起来，往上滑就回来。

要点：比较本次与上次 scrollY，差值 > 阈值（如 8px）才动作，导航栏 `transform: translateY(-100%)` 过渡 0.3s；接近页面顶部时强制显示；`scroll-behavior` 锚点跳转时也要显示。

## 16. 无缝滚动 Logo 墙
> 请做一个无缝滚动 Logo 墙：一排 Logo 一直走，看不出接缝。

要点：内容复制两份放在 flex 轨道里，`@keyframes` 从 translateX(0) 到 -50%，匀速 `linear` 无限循环；悬停暂停（`animation-play-state: paused`）；两份内容必须完全等宽，Logo 高度统一。

## 17. 流动渐变文字
> 请做一个流动渐变文字：关键字的颜色在慢慢流动。

要点：`background: linear-gradient(90deg, 色A, 色B, 色C, 色A)` + `background-clip: text; color: transparent`，`background-size: 200%` + 动画移动 background-position，2~4s 循环。渐变首尾同色才无缝。

## 18. 文字悬浮弹窗（Tooltip）
> 请做一个文字悬浮弹窗：鼠标放上去，文字弹出提示。

要点：提示元素 `position:absolute` 挂在文字上，hover 时 opacity 0→1 + 轻微 translateY 弹出，150~200ms 延迟出现防误触；加小三角用伪元素；纯 CSS 用 `data-tip` 属性 + `::after{content:attr(data-tip)}`，或用原生 `title` 之外的富文本方案；触屏改为点击切换、点空白关闭。

---

## 使用规则

1. **提示词照抄结构**：效果名 +「触发方式 + 运动方式 + 边界情况」。自己描述新效果时也按这个格式写，AI 命中率最高。
2. **一律 transform/opacity**：位移、缩放、淡入淡出都走这两条，别动 width/height/left/top，保证 60fps。
3. **考虑三种设备**：触屏没有 hover（磁吸/翻转/悬停放大要给替代交互）、`prefers-reduced-motion` 用户要能关动画、低端机上的 blur/canvas 要给降级。
4. **同类只选一个**：一页最多 1~2 个强调效果（磁吸/流光/翻转），背景氛围类（极光/粒子/光晕）一次只用一种，叠满就廉价了。

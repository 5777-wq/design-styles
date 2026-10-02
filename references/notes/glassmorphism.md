# 玻璃拟态研究笔记（Glassmorphism → 网页 UI）

> 来源：NN/g、hype4 玻璃生成器（Malewicz 系）、Michał Malewicz、IxDF、Wikipedia（Fluent/Aero）、Apple Newsroom（Liquid Glass 2025）、CSS-Tricks、MDN、Mobbin、One Page Love。

## 一、谱系

玻璃材质在 UI 中循环出现：**Windows Vista/7 Aero Glass（2006–2009）→ Win8 Metro 扁平化（2012）→ Fluent Design 引入 Acrylic（2017）与 Mica（Win11，2021）→ iOS 7 vibrancy → macOS Big Sur / iOS 14（2020）大众化**。2020 年 11 月 Michał Malewicz（此前命名 Neumorphism）正式 coined "Glassmorphism"，经 Dribbble 掀起热潮（大量「只存在于 Dribbble」的炫技稿埋下可读性骂名）。此后进入克制期：玻璃只作**局部材质**。2025 年 6 月 Apple 发布 Liquid Glass（iOS 26/macOS Tahoe，「数字元材质」，动态折射）再度点燃，社区同时强化对比度批评。NN/g 2024 结论：透明度+背景模糊可建立景深层级，但必须满足对比度、背景复杂时加大 blur、提供降透明度选项、克制使用。

## 二、参数出处

- hype4 玻璃生成器默认值：background rgba(255,255,255,0.15) / blur 20 / 边框白 0.3 / 阴影 0 8px 32px rgba(0,0,0,0.1) / 圆角 20。
- Apple 官网导航实测：saturate(180%) blur(20px) + rgba(255,255,255,0.72)。
- NN/g：模糊「宁多勿少」，复杂背景 20px+；必须可降级。

## 三、玻璃面板参数表

| 变体 | background | backdrop-filter | border | 阴影 |
|---|---|---|---|---|
| 薄玻璃（装饰/悬浮卡） | rgba(255,255,255,0.10–0.15) | blur(16–20px) saturate(180%) | 1px solid rgba(255,255,255,0.25–0.3) | 0 8px 32px rgba(0,0,0,0.10) + inset 0 1px 0 rgba(255,255,255,0.4) |
| 厚玻璃（导航/承载文字） | rgba(255,255,255,0.72)（浅底）或 rgba(15,12,41,0.6–0.75)（深底） | blur(20px) saturate(180%) | 1px solid rgba(255,255,255,0.2) | 0 4px 24px rgba(0,0,0,0.12) |
| 玻璃胶囊（按钮/badge） | rgba(255,255,255,0.18) | blur(12px) saturate(170%) | 1px solid rgba(255,255,255,0.35) | 0 2px 12px rgba(0,0,0,0.10) |
| 描边强化（可选） | 同上 | 同上 | + ::before 顶部 1px 渐变高光（transparent→白 0.8→transparent） | — |

## 四、背景光斑配色（3 套）

| 主题 | 基底（linear-gradient 135deg） | 光斑 blob（radial-gradient + blur 80–100px） | 用途 |
|---|---|---|---|
| A 深空紫蓝 | `#0F0C29` → `#302B63` → `#24243E`（Moonlit Asteroid） | `#7B2FF7`、`#00C2FF`、`#FF6EC7`，各 40–55vw，透明度 0.35–0.5 | 音乐/娱乐，默认主推 |
| B 午夜蓝绿 | `#0B1026` → `#101A3D` | `#00E5C3`、`#4F46E5`、`#2563EB`，透明度 0.3–0.45 | 天气/数据情绪类 |
| C 浅色系 | `#EEF2FF` → `#FDF2F8` | `#A5B4FC`、`#67E8F9`、`#FDA4AF`，透明度 0.5–0.6 | 白天模式/轻产品 |

光斑布局：2–3 个，错落对角放置（左上/右下），彼此不完全重叠，底层压一层深色 vignette 保证边缘不漂白。

## 五、字体与圆角

- 字体：`Inter`（正文，最接近 SF Pro）+ `Space Grotesk` 或 `Outfit`（Display）；备选 `Manrope`、`Plus Jakarta Sans`。栈：`"Inter", -apple-system, "SF Pro Display", "Segoe UI", system-ui, sans-serif`。Display 600–700，正文 400–500，标题 -0.02em。
- 圆角：badge/输入框 12px；卡片 16–20px；大卡/模态 24–28px；胶囊 999px。blur 越大圆角越大（模糊内容在锐角处易产生脏边）；同屏 ≤3 档。

## 六、版式模式（7 个）

1. **磨砂导航条**：fixed，高 64–72px，厚玻璃参数（0.72 白或深底 0.7），内容满宽 1200px 容器。
2. **Aurora Hero**：满屏渐变基底 + 2–3 个光斑，中央 Display 大标题（clamp(40px,6vw,72px)，实色白）+ 副标 + 玻璃胶囊 CTA；光斑在标题后方错位。
3. **玻璃功能卡三联**：薄玻璃卡（20px 圆角），图标区 + 短标题 + 一句话；hover translateY(-4px) + 边框白升至 0.45。正文严格控制在两句内。
4. **悬浮玻璃小部件群**（签名构图）：hero 右侧叠 2–3 张不同尺寸玻璃小卡（天气/播放器 widget），z 轴错位 20–40px，制造景深叙事。
5. **章节过渡磨砂条**：全宽厚玻璃横条放一句宣言式大字（≥32px 才压得住透明底）。
6. **玻璃数据小卡行**：4 个统计值（数字 32–40px 实色 + 13px 半透明标签 0.7 白），卡片薄玻璃；数字永远实色。
7. **页脚实色反差**：页脚用近实色深底（`#0B0B1A` 类），与玻璃区形成收束。

## 七、动效与性能

**允许**：背景光斑 30–60s 极慢漂移/呼吸（transform+opacity，禁用 filter 动画）；卡片 hover 升起 4–6px + 边框增亮 + 阴影加深（150–250ms ease-out）；入场 fade-up 8–12px 错峰；光斑随滚动视差 0.05–0.15 倍速。
**禁止**：滚动时实时改变 blur 值（GPU 杀手）；blur 值本身做过渡动画；大面积视差模糊；鼠标跟随强折射；无限弹跳；无 reduced-motion 豁免的持续动画。

## 八、移动端与降级

- `backdrop-filter` 每帧重新合成其后所有内容，中低端手机大面积使用会掉帧、耗电。**移动端降档**：blur 16px 以下、单屏玻璃元素 ≤2、避免全屏玻璃遮罩。
- Safari 必须写 `-webkit-backdrop-filter`。
- 标准降级模板：默认给近实色 `background: rgba(255,255,255,0.92)`；`@supports (backdrop-filter: blur(1px)) or (-webkit-backdrop-filter: blur(1px))` 内才启用半透明+模糊；`@media (prefers-reduced-transparency: reduce)` 与 `(prefers-reduced-motion: reduce)` 下移除模糊与光斑动画。iOS「降低透明度」系统开关映射 prefers-reduced-transparency，必须尊重。

## 九、反模式

1. 整页皆玻璃 → 层级崩塌（没有「底」就没有「浮」）。
2. 文字直接压低不透明玻璃 → 对比度随背景波动，WCAG 必挂。
3. 背景太素（纯白/纯黑无光斑）→ 玻璃不可感知，只剩灰蒙蒙。
4. 玻璃套玻璃嵌套 → blur 叠加发白 + 性能崩溃。
5. 用 `filter` 代替 `backdrop-filter` → 自己的文字被糊。
6. blur < 8px 或背景视频不加深 blur → 背景纹理与文字打架。
7. 亮色光斑正对白字/深色光斑正对黑字 → 需按最差局部校验对比度。
8. 无 @supports/reduced-* 降级 → 老浏览器拿到「看不见的边框 + 透明块」。

## 十、适用边界

**适用**：音乐、天气、钱包/支付卡、媒体库、地图/仪表盘等情绪化、图形化、文字量少的产品。
**不适用**：文档、新闻长读、法律条款、电商结算。实操判断：**一屏正文超过 150 字就该退回实色面板**。
与瑞士风格的分界：瑞士禁透明与模糊（排版即装饰），玻璃拟态以材质本身为视觉主角（必须有光与色的舞台）。

## 十一、信息来源

- NN/g – Glassmorphism: https://www.nngroup.com/articles/glassmorphism/
- Hype4 玻璃生成器: https://hype4.academy/tools/glassmorphism-generator/
- Michał Malewicz – Glassmorphism in 2021: https://michalmalewicz.medium.com/glassmorphism-in-2021-b6a8e3e8f509
- IxDF Glassmorphism: https://ixdf.org/literature/topics/glassmorphism
- Fluent Design / Windows Aero (Wikipedia): https://en.wikipedia.org/wiki/Fluent_Design_System
- Apple Liquid Glass 新闻稿 (2025): https://www.apple.com/newsroom/2025/06/apple-introduces-a-delightful-and-elegant-new-software-design
- CSS-Tricks 解读: https://css-tricks.com/getting-clarity-on-apples-liquid-glass
- Apple 式导航 CSS: https://codeshack.io/apple-style-glassmorphism-navbar-css
- MDN backdrop-filter / prefers-reduced-transparency: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/backdrop-filter
- 案例库: https://mobbin.com/explore/mobile/screens/glassmorphism 、https://onepagelove.com/style/glassmorphism

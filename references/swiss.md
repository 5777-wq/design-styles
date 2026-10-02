
# 瑞士国际主义风格网页设计

## 风格本质

一句话：**用数学化的网格、中性无衬线字体和极端的留白纪律，让内容本身成为界面。**

三个关键词：客观（objective）——设计陈述事实而非修辞；秩序（grid）——每个元素都能说清自己吸附在哪条网格线上；克制（restraint）——删元素永远优先于加元素。源自 1950s 瑞士学派（Müller-Brockmann、Ruder、Hofmann）与 Vignelli 的制度化传承，今天 Vercel、Linear、Vitsœ 及大量设计工作室官网仍在沿用这套语言。

**适用**：品牌官网、设计/建筑工作室作品集、SaaS marketing 站、产品展示、年度报告、活动页。
**不适用**：需要插画情感化的 C 端产品、游戏、儿童产品。信息密度极高的仪表盘可借鉴其网格与字阶，但需保留常规 UI 组件。

## 十二条铁律

1. **一切文字左对齐**（flush left, ragged right），禁止居中排版长文本。例外仅限图注和数据标注。参差的行尾符合阅读节奏，居中会消灭不对称张力。
2. **先立网格再排内容**：桌面 12 列 / 平板 8 列 / 移动 4 列，所有元素起止吸附网格线。网格的功能就是防止"任意、无意义的摆放"（Vignelli）。
3. **全站只用一个无衬线字族、不超过 3 个字重**。层级靠字号对比与字重制造，不靠换字体。
4. **间距只用 4/8px 步长 token**（4/8/16/24/32/48/64/96/128），行高取 4 的倍数。出现 13px、37px 之类的随意值即失序。
5. **色彩 = 一套灰阶 + 一个强调色**，强调色占屏 <5%，只作语义信号（链接、当前态、关键数据）。出现第二个色相即破功。
6. **圆角为 0；禁止渐变、投影、玻璃拟态、发光、scale 缩放动效**。这些是模拟假光假深度的消费级装饰信号。
7. **分隔靠 1px hairline + 留白，不靠卡片容器**。四边框 + 阴影 = 在模拟物理高度 = 非瑞士。
8. **不对称构图**：主侧分栏用 8+4 或 5+7；禁止三等宽卡片阵列（装饰性重复 ≠ 信息层级）。
9. **用编号系统与微标签组织信息**：区块编号 01/02/03；全大写小标签 letter-spacing 0.05–0.1em。
10. **标题要敢大**：hero 级标题 clamp 到 9–10vw，负字距 -0.02~-0.03em（中文混排减半）；正文行长 45–75 字符。
11. **每屏保留至少一处未被占用的负空间焦点**；留白是主动的设计元素，不是剩余空隙。
12. **数字用 tabular-nums，表格只用横线**（无竖线、无斑马纹）。

## 设计 Token 速查

完整推导与多套方案见 references，这里是最常用默认值。

**网格**（Margin 必须明显宽于 Gutter，经典层级）：

| 断点 | 列数 | 容器 max-width | 页边距 | 栏距 |
|---|---|---|---|---|
| ≥1200px | 12 | 1440px（内容区 1280） | 64px | 24px |
| 768–1199px | 8 | 100% | 40px | 24px |
| <768px | 4 | 100% | 20px | 16px |

**字阶**（Inter / Helvetica 系，基准 1rem=16px）：

| 级别 | font-size | line-height | letter-spacing | weight |
|---|---|---|---|---|
| display | clamp(3rem, 1.977rem + 4.55vw, 5.5rem) | 1.05 | -0.03em | 700 |
| h1 | clamp(2.25rem, 1.739rem + 2.27vw, 3.5rem) | 1.1 | -0.025em | 700 |
| h2 | clamp(1.75rem, 1.443rem + 1.36vw, 2.5rem) | 1.15 | -0.015em | 600 |
| h3 | clamp(1.25rem, 1.148rem + 0.45vw, 1.5rem) | 1.25 | 0 | 600 |
| body | clamp(1rem, 0.949rem + 0.23vw, 1.125rem) | 1.6（含中文 1.75） | 0 | 400 |
| caption | 0.8125rem | 1.5 | 0 | 400 |
| micro-label | clamp(0.6875rem, 0.676rem + 0.05vw, 0.75rem) | 1.2 | +0.08em 全大写 | 500 |

**字体栈**（西文永远在前；免费首选 Inter，血统之选 Neue Haas Grotesk）：

```css
font-family: "Helvetica Neue", Helvetica, Arial,
  "PingFang SC", "Hiragino Sans GB", "Noto Sans SC", "Microsoft YaHei", sans-serif;
```

**配色「苏黎世纸白」（默认方案）**：

| 角色 | 浅色 | 深色 |
|---|---|---|
| 背景 | `#F7F6F2` 暖纸白 | `#131312` 暖炭黑 |
| 前景 | `#111111` | `#EAEAE6` |
| 次级文字 | `#4A4A45` | `#A8A8A2` |
| 分隔线 | `#DEDDD5` | `#2E2E2B` |
| 强调色 | 瑞士红 `#E30613` | 国际橙 `#FF4F00` |

备选：纯白极冷「巴塞尔画廊」（背景 #FFF、克莱因蓝 #002FA7）、工业感「信号工坊」。深色版不是反色——背景用深灰非纯黑，前景用暖灰白非纯白，强调色提亮降饱和。完整 token 见 references/notes/swiss-color-motion.md。

## 工作流程

1. **定骨架**：根据页面类型选章节组合——nav / hero / manifesto / index（行式列表）/ about / footer。展示型页面的经典顺序：Hero → Manifesto → Work Index → About → Footer。
2. **从模板起步**：复制 `assets/templates/swiss.html`（零依赖单文件，已含全部 token、网格、hairline、行式索引等基础设施），替换内容与文案；或按其中的 CSS 变量体系重写。多页项目把 CSS 抽成共享文件，保持 token 一致。
3. **组装模式**：按 references/notes/swiss-patterns.md 的模式库（固定导航、hero、索引章节头、行式作品列表、粘性侧栏、页脚）拼装版面，主侧分栏保持不对称。
4. **细节查 references**：字体引入/中西文混排读 typography.md；breakout 布局/sticky/响应式读 grid-layout.md；动效与深色模式读 color-motion.md；需要说服用户或深入理解风格时读 principles.md 与 patterns.md。
5. **过自检清单**：交付前逐条核对（下方清单），重点核对最容易破功的三处——居中排版、随意间距值、第二强调色。

## 自检清单

- [ ] 页面上没有任何居中的正文或标题（图注/数据标注除外）
- [ ] 所有间距值都是 4 的倍数；行高都是 4 的倍数
- [ ] 全站只有一个字体族、≤3 个字重、一个强调色
- [ ] 没有 border-radius、渐变、box-shadow、玻璃拟态
- [ ] 卡片阵列已改成行式列表或不对称分栏
- [ ] 大标题字号对比足够极端（display 与 body 至少 3 倍）
- [ ] hairline 只出现在网格线上（区块分界、表格行），没有漂浮装饰线
- [ ] 数字/编号用了 tabular-nums
- [ ] 交互动效 ≤300ms、无缩放无弹跳、尊重 prefers-reduced-motion
- [ ] 移动端塌缩成单列后保留了编号、hairline、微标签体系
- [ ] 至少一处负空间焦点未被占用；删除后不影响信息传达的元素已删除

## 高级感从哪来

1. **留白尺度**：板块间距取卡片内边距的 2–4 倍（桌面 section 间距 96–128px）。
2. **字号对比的胆量**：超大标题与小正文的极端对比是瑞士高级感的核心。
3. **细节精度**：1px 就是 1px、基线严格对齐、数字右对齐——工程精度本身产生贵气。
4. **色彩稀缺纪律**：一个强调色克制使用，让它每次出现都有分量。
5. **诚实客观**：真实内容、无效果堆砌，个性体现在清晰与节奏，而非装饰。

## References 索引

- `references/notes/swiss-principles.md` — 设计史、核心原则的学理依据、与 Bauhaus/Brutalism/极简主义的分野、12 条硬规则的设计学解释
- `references/notes/swiss-typography.md` — Helvetica 授权现状、Inter/Archivo/Instrument Sans 评估与引入方式、完整排印 scale、中西文混排 5 规则、数字排版
- `references/notes/swiss-grid-layout.md` — 12 列网格规格推导、8/4pt 间距体系、8 个布局模式的 CSS 实现要点、页面骨架、常见错误
- `references/notes/swiss-color-motion.md` — 三套完整配色 token（浅+深）、灰阶层级、视觉语言硬规则、动效允许/禁止清单与时长曲线、反模式
- `references/notes/swiss-patterns.md` — 真实瑞士风格网站案例、8 个版式套路（含具体参数）、页脚公式、移动端降级策略
- `assets/templates/swiss.html` — 零依赖起始模板，打开即是完整风格示范页

# 孟菲斯设计研究笔记（Memphis Design → 网页 UI）

> 来源：Wallpaper*、Creative Bloq、Crabiz、Design Styles Showcase、GraphicMama、Awwwards（Memphis Milano 官网）、Wikipedia、The Spruce。

## 一、起源与内核

1980 年 12 月，Ettore Sottsass 在米兰家中聚会，Bob Dylan 的《Stuck Inside of Mobile with the Memphis Blues Again》整晚循环，遂命名「Memphis」（兼指孟菲斯市与古埃及首都）；1981 年米兰家具展首秀，批评界爱憎两极；Sottsass 1985 年退出，团体约 1987–88 年解散。核心成员：Michele De Lucchi、Nathalie Du Pasquier、George Sowden、Martine Bedin、Aldo Cibic、Matteo Thun，及 Peter Shire、Michael Graves、Shiro Kuramata、Masanori Umeda 等。代表作：Carlton 书架（等边三角结构 + Bacterio 黑白波浪纹底座）、Casablanca 柜、First 椅、Tahiti 灯、Du Pasquier 印花织物。材料上故意把廉价塑料层压板与硬木、漆、黄铜混搭——"precious and tacky"（名贵与俗气并置）。Karl Lagerfeld 与 David Bowie 是著名藏家。渗透 80 年代流行文化（《Miami Vice》《Pee-wee's Playhouse》），经《怪奇物语》式复古美术和 Vaporwave/Avant Basic 回潮。

**对网页最关键的内核**：孟菲斯的「任意」是自觉的、有系统的反讽——固定形状词汇表 + 高强度重复 + 黑白压阵。

## 二、配色（3 套）

| Token | A「米兰 1981」经典 | B「电光 80s」霓虹 | C「Du Pasquier」柔和印花 |
|---|---|---|---|
| --primary | `#FF6B6B` 珊瑚红 | `#FF5D8F` 品红粉 | `#2A9D8F` 青绿 |
| --accent-1 | `#4ECDC4` 青 | `#00C2A8` 蓝绿 | `#F4A261` 橙沙 |
| --accent-2 | `#FFD166` 黄 | `#FFC53D` 黄 | `#E9C46A` 芥黄 |
| --accent-3 | `#9B5DE5` 紫（点缀） | `#FF8C42` 橙 | `#C3A6FF` 丁香紫 / `#FFB5C2` 柔粉 |
| --ink | `#111111` | `#111111` | `#1A1A1A` |
| --bg | `#FAF3E7` 米白 | `#F8F9FA` 浅灰 | `#FDF6EC` 米白 |

每屏取 primary + 2 accent + 黑白；C 套取自 Du Pasquier 的 American Apparel 系列，适合儿童与文创品牌。

## 三、字体

- **Display**：`Righteous`（首选，几何 80s）或 `Shrikhand`（更玩闹，斜体感）；少量点缀可用 `Bungee`、`Monoton`（霓虹线体，限 1 个词）。注意均为单一 400 字重，层级靠字号与颜色制造。
- **正文**：`Poppins`（400/600/700），备选 `Montserrat`。
- **中文**：`Noto Sans SC`（400/500/700/900），标题用 900 压得住几何图形。

**字号**：H1 display `clamp(44px, 7vw, 88px)` 行高 1.05 可 rotate(-2deg)；H2 32–40px/700（中文 900）；H3 20–24px/700；body 16–18px/400 行高 1.7；标签/按钮 14–16px/700 全大写 0.08em。

## 四、圆角 / 描边 / 阴影

- 圆角二值化：卡片与形状 **0–4px 直角**，按钮与 chip **999px pill**；禁止 8–16px 中庸圆角。
- 描边：`--border: 3px solid #111`；小型元素可 2px。
- 阴影：`--shadow-pop: 6px 6px 0 #111`；hover 按压 `translate(3px,3px)` + `3px 3px 0`；重点卡片可用彩色硬阴影 `8px 8px 0 var(--primary)`。

## 五、形状词汇表（8 种，CSS 思路）

1. **波点阵**：`radial-gradient(var(--c) 4px, transparent 4.5px)` + `background-size:24px 24px`
2. **条纹**（黑白斜纹是身份纹）：`repeating-linear-gradient(45deg,#111 0 10px,#fff 10px 20px)`
3. **锯齿 zigzag**：`clip-path: polygon(...)` 三角齿边，做分界带边缘
4. **Squiggle 蚯蚓线**：inline SVG `path M0,10 Q10,0 20,10 T40,10 T60,10...`，`stroke:3px round`
5. **闪电**：`clip-path: polygon(60% 0, 20% 45%, 45% 45%, 30% 100%, 85% 40%, 55% 40%)`
6. **三角**：`clip-path: polygon(50% 0, 0 100%, 100% 100%)`
7. **圆环/半圆**：`border-radius:50%` / `999px 999px 0 0`
8. **Bacterio 斑点噪纹**：多层错位 radial-gradient 小点或 SVG feTurbulence

## 六、版式模式（6 个）

1. **爆炸 Hero**：米白底 + 对角两个装饰簇（各 3 形状，尺寸 60–140px，rotate 各异）；display 大标题 rotate(-2deg)；黑色 pill CTA + 硬阴影；底部 12px 黑白条纹带收边。
2. **贴纸卡片网格**：3 列，白底 3px 黑描边 + 6px 硬阴影，间距 24–32px；每卡左上角一个 rotate(-4°) 形状色标；hover 抬起（阴影 8px + translate(-2px,-2px)）。
3. **纹理分界带**：区块之间 80–120px 高的带子，波点/条纹/锯齿三选一轮换，中央可嵌一句短语（白字黑底 pill）。
4. **锯齿拼色分屏**：左右 55/45 双色块，分界线为锯齿（clip-path），内容白卡直角压在色块上（内边距 48px）。
5. **跑马灯公告条**：黑底白字或黄底黑字，高 48px，短语间用 ✦/三角分隔，匀速 marquee。
6. **图形 bullet 列表**：每条 bullet 用不同几何形状（三角/圆/方轮换，色轮取色，14–18px），行距 1.9。

## 七、动效

**允许**：形状漂浮（translateY ±6px，6–8s ease-in-out 循环）；squiggle 描边生长（stroke-dashoffset）；hover 硬阴影按压（120ms）；marquee 匀速滚动；入场 pop（scale 0.9→1，回弹 `cubic-bezier(0.34,1.56,0.64,1)`）；形状慢速自转（360°/30s）。
**禁止**：视差滚动；模糊/毛玻璃；渐变动画；阴影模糊值 morphing；3D 翻转；超过 300ms 的惯性拖尾（孟菲斯要 "snappy"）；骨架屏（用几何 loading：旋转方块 + 交替配色替代）。

## 八、移动端

1. 装饰簇从四角减为 hero 两簇，尺寸减半；删除任何可能与文字重叠的簇。
2. 纹理带 80–120px → 48px；波点 background-size 24px → 16px。
3. 全局 `overflow-x:hidden`，倾斜幅度减半（-3°~3°）防横向溢出。
4. 触控目标 ≥44px：pill 按钮 padding 加大；移动端阴影缩至 4px。
5. 卡片网格 3 列 → 1 列，保留描边 + 阴影（缩小不取消）；H1 下限 36px，body 16px 不再降。

## 九、反模式与适用边界

**廉价剪贴画灾难的成因**：emoji 当装饰；一次性引入 20 个不重复形状（违反词汇表规则）；混入渐变与玻璃拟态；模糊阴影；彩色小字正文；透明度花哨的写实 PNG 贴图；每屏密度一致无峰值。
**适合**：创意市集、音乐节、儿童/青年品牌、独立文创、游戏周边。
**不适合**：医疗、金融、法律、企业官网、严肃新闻（趣味复古语境错位 → tacky）。

**降级模式**：不用任何装饰图形时，仅靠「3px 黑描边 + 6px 硬阴影 + 直角/pill 二值圆角 + 配色」也能达到 80% 的孟菲斯辨识度。

## 十、信息来源

- Wallpaper* – Memphis Group definitive guide: https://www.wallpaper.com/design-interiors/memphis-design-group-definitive-guide
- Creative Bloq – 10 iconic examples: https://www.creativebloq.com/inspiration/10-iconic-examples-of-memphis-design
- Crabiz – Memphis Design 101: https://www.crabiz.com/blog/designing-with-an-80s-trend-memphis-design-101
- Design Styles Showcase: https://design-styles.enlighten-media.net/pages/memphis
- GraphicMama – 60+ Memphis Design Examples: https://graphicmama.com/blog/memphis-design-examples
- Awwwards – Memphis Milano 官网: https://www.awwwards.com/sites/memphis-milano
- Wikipedia – Memphis Group: https://en.wikipedia.org/wiki/Memphis_Group

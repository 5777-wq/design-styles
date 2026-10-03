# Psychedelic 研究笔记（1960s 旧金山迷幻海报学派 → 网页 UI）

> 来源：Wikipedia（Psychedelic art / Wes Wilson / Victor Moscoso / Rick Griffin / Alton Kelley）、MDN feDisplacementMap、CSS-Tricks（gooey effect / reduced motion）、W3C WCAG（SC 2.3.1 / 2.3.3）、真实案例 Levitation Festival (levitation.fm)、Desert Daze (desertdaze.org)、Awwwards Trippy Sites、Google Fonts CSS API 实测。

## 一、起源与正典（史实基础）

1966 年 2 月 Bill Graham 接管旧金山 Fillmore Auditorium，聘 **Wes Wilson** 设计 **BG-1 至 BG-105**（1966.2–1967.9）系列海报；Wilson 发现维也纳分离派设计师 **Alfred Roller**（1902/1903 年 Ver Sacrum 封面）的手绘流动字体，将其放大、加粗、字腔充气、字形随阅读线起伏，形成标志性「融化字体」。**Victor Moscoso**（Neon Rose 系列）师从 Josef Albers，用「等明度的暖色紧贴等明度冷色」制造视网膜振动；**Rick Griffin** 出自冲浪插画与 Zap Comix，创造 Flying Eyeball（1968 Hendrix 海报）；**Alton Kelley & Stanley Mouse** 为 Grateful Dead 改绘 Edmund Sullivan《鲁拜集》骷髅插图，即 FD-26「Skeleton and Roses」（1966）。五人并称 **Big Five**，1967 年共组 Berkeley Bonaparte 发行海报。风格根源 = Art Nouveau（Mucha 的剪影与卷须）+ op art 振动 + 摇滚反文化，高峰期 1966–1972。

**关键 authentic 事实：原版海报是丝网/胶印平涂，限 5–7 个专色，无渐变无发光**——这是与「AI 迷幻图」的分水岭。

## 二、标志性视觉母题

① 流动充气展示字（文字即画面，可读性极差是原教旨特征）；② 高饱和互补撞色的振动（品红/橙、紫/青柠）；③ 同心圆、漩涡、涡纹（Fillmore 日落式同心圆）；④ 密集有机线条填充；⑤ 轴对称曼陀罗构图；⑥ 新艺术式女性剪影与藤蔓。

## 三、12 条铁律（重点：可读性分离）

1. **双层分离**：迷幻处理（流动体/漩涡/振动）只允许出现在 hero 与章节 display 层；正文、表单、时刻表、按钮属信息层，零迷幻处理——原海报的可读性灾难是历史遗产，不是执行标准。
2. **全局底字**：深紫底 `#1A0B2E` × 奶油字 `#FFF3E0` 为默认组合，正文 ≥16px / 行高 ≥1.7。
3. **实色投影**：流动标题必须配同色系实色投影（offset 4–6px、模糊 0），禁止模糊光晕——平涂投影既复刻丝网印又保证字形可辨。
4. **振动不碰文字**：互补振动只用于大面积色块、粗描边、背景图形；永不做文本对文本（明度相等时对比度必然不合格）。
5. **一屏一对**：每屏最多一组振动配对，其余同套色内和谐——原海报 5–7 专色，色越多越廉价。
6. **平涂禁渐变**：仅允许 Fillmore 式径向「日落晕」（单一互补双色）；大面积彩虹 mesh 渐变 = AI 迷幻图的第一标志。
7. **背景退让**：漩涡/同心圆做背景时透明度 ≤20%，不与文字争对比。
8. **形变限额**：SVG 位移滤镜 scale ≤ 字号的 15%；任何关键信息（日期/票价/艺人名）必须存在无形变副本。
9. **正文绝缘**：波浪/位移滤镜永不接触正文、导航、按钮。
10. **前庭安全**：所有循环动效响应 `prefers-reduced-motion: reduce`，reduce 时全部静态化，内容不缺失（WCAG 2.3.3）。
11. **构图分区**：曼陀罗对称构图只用于海报卡与 hero；lineup/时刻表用常规网格排版。
12. **质感保守**：插画用高饱和平涂 + 粗描边（≥3px）；禁玻璃拟态、毛玻璃、噪点模糊叠加。

## 四、设计 Token

**配色 A「Fillmore 深夜」（默认深底）**：bg `#1A0B2E` / surface `#2A1650` / text `#FFF3E0` / primary 品红 `#FF00A8` / secondary 橙 `#FF6B00` / accent 青柠 `#B4FF00` / 投影同系 `#0F0620`。
**配色 B「Neon Rose 日光」（奶油底）**：bg `#FFF3E0` / surface `#FFE3BD` / text `#2A0A4A` / primary 品红 `#D6008F`（浅底加深保对比）/ secondary 电光青 `#00E5FF` / accent 橙 `#FF6B00`。
**配色 C「Acid Lime」**：bg `#0E0E2A` / text `#FFF3E0` / 主振动 青柠 `#B4FF00` × 电光青 `#00E5FF` / 辅 紫 `#7B2FFF`。

**振动配对法则**（明度差 <15% 且色相差 >120° 时振动最强，仅装饰用）：品红 × 青柠（最烈）、橙 × 电光青（最经典安全）、紫 × 青柠。文本恒用深底奶油组合（对比度 >12:1）。

**字体（已验证存在于 Google Fonts）**：`Climate Crisis`（目前最接近 Wilson 充气 Blob 质感的免费字体，带可变 YEAR 轴）；备选 `Bagel Fat One`；新艺术辅助衬线 `Yeseva One`（章节引言）；`Rubik Bubbles` 贴纸徽章小字。Shrikhand 已被 memphis 占用排除；Fredoka 过于圆润友好不推荐。正文 `Inter` + `Noto Sans SC`。

**SVG 波动方案**：`<filter id="warp"><feTurbulence type="fractalNoise" baseFrequency="0.012 0.02" numOctaves="1" seed="7"/><feDisplacementMap in="SourceGraphic" scale="14" xChannelSelector="R" yChannelSelector="G"/></filter>` 经 `filter: url(#warp)` 作用于标题。参数：baseFrequency 0.01–0.05（越大越碎）、numOctaves 1–2、scale ≈ 0.12–0.15× 字号、filter region 四周加 20% padding 防边缘被吃。性能：逐像素重绘，只挂标题元素（≤ 视口 15% 面积），禁挂 body/容器；动效只动 baseFrequency（±0.003）或 SMIL 动 scale（8→14）周期 ≥8s；移动端/DPR≥2 降级为静态位移。

## 五、版式模式（6 个）

1. **漩涡 Hero**：径向同心圆 SVG 背景（3–4 环，描边 24–40px，品红→紫），标题 Climate Crisis `clamp(44px, 12vw, 110px)` + 8px 实色投影，副标常规体。
2. **波浪分割带**：SVG path 波形 divider 高 60–120px，双波错位叠放（前层实色、后层互补色 20% 不透明）。
3. **海报卡**：2:3 纵横比，内三层——流动体标题 / 中景同心圆图形 / 底部无衬线信息条；hover 抬升 4px 且投影换互补色（一次性 250ms）。
4. **Lineup 时刻表**：按日分组两栏，时间等宽数字，行首 32px 圆点按振动对轮换配色，艺人名 700 无衬线——信息密度区完全干净。
5. **贴纸徽章**：胶囊描边 2px 互补色 + 实色填充，整体旋转 −4°~4° 叠在卡片角上。
6. **Marquee 分隔条**：高 48px 无限滚动文本条，`aria-hidden`，两屏之间情绪过渡用。

## 六、动效（眩晕安全阈值）

**允许**：hover 抖动 `steps()` 位移 ≤2px、≤300ms、不循环；波浪 divider 静态；feTurbulence 慢频呼吸（周期 ≥8s、幅度 ≤6px）；色相/透明度过渡（不改变形状位置，相对安全）；漩涡旋转仅背景层、周期 ≥20s、透明度 ≤20%。
**禁止**：视差滚动；大面积 mesh 渐变流动；任何 >3Hz 频闪（WCAG 2.3.1：1 秒内 ≤3 次闪光）；文字形变动画循环；滚动触发的旋转。
**豁免**：`prefers-reduced-motion: reduce` 时全部静态化，内容不因关闭动效而缺失。

## 七、移动端

① 标题 clamp()，<768px 关闭滤镜动画只留静态位移；② 海报卡单列 max-width 420px；③ 振动色块移动端不透明度降至 12%；④ Marquee 速度放慢 1.5×；⑤ 触控目标 ≥44×44px，贴纸徽章不遮挡点击区。

## 八、示范页内容方案

**「ELECTRIC SWIRL · 迷幻摇滚音乐节」**（兼线上黑胶快闪店），单页结构：① 漩涡 Hero（活动名流动体 + 日期 2026.11.7–8 + 奶油副标）；② 波浪 divider；③ 三日 Lineup 干净时刻表（信息层示范）；④ 海报画廊：6 张海报卡分别致敬 Wilson 融化字、Moscoso 振动、Griffin 波浪、Kelley&Mouse 骷髅玫瑰、曼陀罗、同心圆日落；⑤ 黑胶唱片卡网格（2:3 卡 + 唱片旋转 hover）；⑥ 票务信息区（纯排版）；⑦ Footer 大字 Marquee + 前庭安全提示。

## 九、信息来源

- Wikipedia – Psychedelic art: https://en.wikipedia.org/wiki/Psychedelic_art
- Wikipedia – Wes Wilson: https://en.wikipedia.org/wiki/Wes_Wilson （BG-1~105、Alfred Roller 字体源头）
- Wikipedia – Victor Moscoso: https://en.wikipedia.org/wiki/Victor_Moscoso （Albers 色彩理论、等明度冷暖振动）
- Wikipedia – Rick Griffin: https://en.wikipedia.org/wiki/Rick_Griffiin （Flying Eyeball）
- Wikipedia – Alton Kelley: https://en.wikipedia.org/wiki/Alton_Kelley （FD-26 骷髅玫瑰来源）
- MDN – feDisplacementMap: https://developer.mozilla.org/en-US/docs/Web/SVG/Reference/Element/feDisplacementMap
- W3C WCAG – Animation from Interactions (SC 2.3.3): https://www.w3.org/WAI/WCAG21/Understanding/animation-from-interactions.html
- 真实案例: Levitation https://www.levitation.fm · Desert Daze https://desertdaze.org · Awwwards Trippy Sites https://www.awwwards.com/favsto/collections/trippy-sites

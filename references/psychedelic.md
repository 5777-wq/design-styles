# Psychedelic 风格网页设计 (1960s 迷幻海报)

## 风格本质

一句话：**丝网印刷的振动与流动——融化字体、互补撞色、同心漩涡，但信息层永远干净。**

1966–1969 旧金山 Fillmore 海报学派，Wes Wilson 从维也纳分离派设计师 Alfred Roller 的手绘字体发展出「融化字体」；Victor Moscoso 师从 Albers 用等明度冷暖撞色制造视网膜振动；Big Five（Wilson/Moscoso/Griffin/Kelley/Mouse）定义了摇滚海报的全部语法。**原版是丝网平涂、限 5–7 专色、无渐变无发光**——这条史实是与「AI 迷幻图」的分水岭。

**适用**：音乐节、唱片店、艺术展、潮流快闪——需要强情绪与复古态度的场合。
**不适用**：文字密集产品、严肃机构、需要长时间阅读的页面。

## 十二条铁律（核心：可读性分离）

1. **双层分离**：迷幻处理只出现在 hero 与 display 层；正文/表单/时刻表/按钮属信息层，零迷幻处理。
2. **全局底字**：深紫底 `#1A0B2E` × 奶油字 `#FFF3E0` 默认组合；正文 ≥16px / 1.7。
3. **实色投影**：流动标题配同色系实色投影（offset 4–6px、模糊 0），禁模糊光晕。
4. **振动不碰文字**：互补振动只用于大色块、粗描边、背景图形；永不文本对文本。
5. **一屏一对**：每屏最多一组振动配对——色越多越廉价。
6. **平涂禁渐变**：只允许 Fillmore 式径向「日落晕」（单一互补双色）；彩虹 mesh = AI 迷幻图标志。
7. **背景退让**：漩涡/同心圆做背景透明度 ≤20%。
8. **形变限额**：SVG 位移 scale ≤ 字号 15%；关键信息必须有无形变副本。
9. **正文绝缘**：滤镜永不接触正文、导航、按钮。
10. **前庭安全**：循环动效响应 prefers-reduced-motion，reduce 时全部静态。
11. **构图分区**：曼陀罗构图只用于海报卡与 hero；时刻表用常规网格。
12. **质感保守**：高饱和平涂 + 粗描边（≥3px）；禁玻璃拟态与噪点模糊。

## 设计 Token 速查

**配色 A「Fillmore 深夜」（默认）**：bg `#1A0B2E` / surface `#2A1650` / text `#FFF3E0` / 品红 `#FF00A8` / 橙 `#FF6B00` / 青柠 `#B4FF00` / 投影 `#0F0620`。
备选：B「Neon Rose 日光」奶油底 `#FFF3E0` + 深紫字 `#2A0A4A` + 品红 `#D6008F` + 电光青 `#00E5FF`；C「Acid Lime」`#0E0E2A` 底 + 青柠×电光青主振动。

**振动配对法则**（明度差 <15%、色相差 >120° 时最强，仅装饰用）：品红×青柠（最烈）、橙×电光青（最安全）、紫×青柠。文本恒用深底奶油（>12:1）。

**字体**（Google Fonts）：display `Climate Crisis`（最接近 Wilson 充气质感的免费字体）；备选 `Bagel Fat One`；新艺术衬线 `Yeseva One`；徽章 `Rubik Bubbles`；正文 `Inter` + `Noto Sans SC`。
引入：`family=Climate+Crisis&family=Yeseva+One&family=Rubik+Bubbles&family=Inter:wght@400;600;700&family=Noto+Sans+SC:wght@400;700`

**SVG 波动滤镜**（标题专用，正文绝缘）：

```html
<filter id="warp">
  <feTurbulence type="fractalNoise" baseFrequency="0.012 0.02" numOctaves="1" seed="7"/>
  <feDisplacementMap in="SourceGraphic" scale="14" xChannelSelector="R" yChannelSelector="G"/>
</filter>
<!-- filter region 四周加 20% padding 防边缘被吃；scale ≈ 字号 × 0.12–0.15 -->
```

性能：只挂标题元素（≤ 视口 15% 面积）；动效只动 baseFrequency（±0.003）周期 ≥8s；移动端/DPR≥2 静态位移。

## 工作流程

1. **选配色与振动对**：A 深夜（默认）/ B 日光 / C Acid；确定本页唯一振动配对。
2. **从模板起步**：复制 `assets/templates/psychedelic.html`（虚构音乐节 ELECTRIC SWIRL 示范页，含 SVG 滤镜标题、漩涡 hero、干净 lineup、海报卡全套），替换内容。
3. **分区检查**：迷幻层（hero/海报卡/分割带）与信息层（lineup/票务/正文）严格分离。
4. **过自检清单**，重点核对眩晕安全与 reduced-motion 豁免。

## 自检清单

- [ ] 迷幻处理只在 hero 与 display 层；正文/表单/时刻表完全干净
- [ ] 全局底字对比度 >12:1；没有文本对文本的振动配对
- [ ] 流动标题有实色投影（模糊 0）；关键信息有无形变副本
- [ ] 每屏 ≤1 组振动配对；全页色板 ≤7 色
- [ ] 没有彩虹 mesh 渐变；日落晕只用单一互补双色
- [ ] 背景漩涡/同心圆透明度 ≤20%
- [ ] SVG 滤镜只挂标题、scale ≤ 字号 15%、滤镜区域有 padding
- [ ] 动效：无 >3Hz 频闪、无形变循环、漩涡旋转 ≥20s；reduced-motion 全静态
- [ ] 移动端滤镜静态化、海报卡单列、振动色块透明度降档
- [ ] 贴纸徽章不遮挡触控目标（≥44px）

## 深入阅读与模板

- `references/notes/psychedelic.md` — 完整研究笔记：Big Five 正典史（BG-1~105、Neon Rose、FD-26）、振动色彩学、SVG 滤镜参数与性能、WCAG 眩晕安全、信息来源
- `assets/templates/psychedelic.html` — 零构建示范页（音乐节 ELECTRIC SWIRL），浏览器直接打开

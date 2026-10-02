# 瑞士网格系统与 CSS 布局实现

> 来源：Müller-Brockmann《Grid Systems in Graphic Design》原书（Monoskop PDF）、The Vignelli Canon、Material Design 间距规范、Ryan Mulligan / Josh Comeau 的 breakout 布局方案、Smashing Magazine。

## 一、经典网格理论要点

- Müller-Brockmann：网格是"约束引擎"——选定系统后坚持使用，变化来自内容而非即兴排布；"The grid system is an aid, not a guarantee"。
- 网格的四个变量：列 (column)、栏距 (gutter)、页边距 (margin)、模块 (field)。关键洞见：网格的成功不仅取决于元素放置，还取决于**网格相对于容器的定位**；模块化决策应从文本基线网格推导。
- **12 列成为标准的原因**：12 可干净拆为 1/2/3/4/6/12 份，覆盖几乎所有构图。Bootstrap、Tailwind、Material、Carbon 均沿用。
- Vignelli：用最少的网格结构承载最多的内容变化；栏间距理想值 = 一行文字的高度。
- 留白不是"剩余空隙"，而是主动的结构元素。

## 二、推荐网格规格

| 变量 | 桌面 ≥1200 | 平板 768–1199 | 移动 <768 |
|---|---|---|---|
| 列数 | 12 | 8 | 4 |
| 容器 max-width | 1440px（内容区 1280） | 100% | 100% |
| 页边距 margin | 64px | 40px | 20px |
| 栏距 gutter | 24px | 24px | 16px |
| 基线步长 | 4px | 4px | 4px |
| 间距步长 | 8px | 8px | 8px |

容器写法：`max-width: 1440px; margin-inline: auto; padding-inline: clamp(20px, 4.4vw, 64px)`。**Margin 必须明显宽于 Gutter（约 2–3 倍）**，否则版面显得拥挤无序。流体栏距：`--gutter: clamp(16px, 1.67vw, 24px)`。

## 三、8pt/4pt 间距体系

4pt 为基线步长（排版、图标、微调），8pt 为组件与布局步长。

| Token | 值 | 用途 |
|---|---|---|
| space-1 | 4px | 图标微调、hairline 上下间隙 |
| space-2 | 8px | 标签与值、行内间距 |
| space-3 | 16px | 段落间距、移动端 gutter |
| space-4 | 24px | 桌面 gutter、卡片内边距 |
| space-5 | 32px | 组件组间距 |
| space-6 | 48px | 子区块间距、移动端 section 间距 |
| space-7 | 64px | 桌面页边距 |
| space-8 | 96px | section 间距（桌面下限） |
| space-9 | 128px | section 间距（桌面常规） |

**行高对齐基线**：所有 line-height 取 4 的倍数（正文 16/24 即 1.5；H1 48/56；说明 12/16）；公式 `line-height = round-to-4(font-size × 1.4~1.5)`。

## 四、布局模式库（8 个）

**P1 三层 breakout 骨架（全页基础）**
命名网格线构成 full / content 层，内容落 content，出血图落 full：
```css
.grid { display: grid; grid-template-columns:
  [full-start] minmax(var(--gutter), 1fr)
  [content-start] min(1280px, 100% - 2 * var(--gutter)) [content-end]
  minmax(var(--gutter), 1fr) [full-end]; }
```
子元素 `grid-column: content`，出血图 `grid-column: full`。不用负 margin、不用 viewport hack。

**P2 不对称主侧分栏（8+4）**
12 栏中主内容占 8、元信息占 4，顶部对齐。主内容永远占宽栏，窄栏只放补充信息（日期、编号、标签）。移动端各自 span 12。

**P3 编辑式 5/7 分割**
`grid-template-columns: 5fr 7fr`；窄左栏放章节编号与大标题（贴左边线），宽右栏放正文。左栏 `align-self: start; position: sticky; top: 96px` 可让标题随滚动驻留。

**P4 索引式章节头（01/02/03）**
每个 section 顶部一条全宽细线，线上方左置编号、右置章节名。编号自动化用 CSS counter（`counter-reset` / `counter(section, decimal-leading-zero)`）；section 用 `border-top: 1px solid; padding-top: 16px`。

**P5 hairline 细分隔线系统**
线只出现在网格线上——section 之间、表格行之间、页眉页脚下缘。1px（高 DPI 屏可用 0.5px）；表格行可用 `rgba(0,0,0,.15)` 区分主次。**禁止用线框盒子**：线是水平结构线，不是容器描边。

**P6 粘性侧边章节索引**
左栏放 "01 Index / 02 Work / 03 About" 目录，滚动驻留。要点：grid/flex 子项必须 `align-self: start`（否则被拉伸导致 sticky 失效）；祖先不得有 `overflow: hidden`；过长加 `max-height: calc(100vh - 192px); overflow-y: auto`；各 section 加 `scroll-margin-top: 96px` 防锚点被固定页眉遮挡；当前章节高亮用 IntersectionObserver。

**P7 固定极简导航条**
顶边线下四格元信息条（Logo | 章节索引 | 时间 | 联系），等宽分栏、文字贴各格左缘：
```css
position: fixed; inset: 0 0 auto 0; display: grid;
grid-template-columns: repeat(4, 1fr); border-bottom: 1px solid;
padding: 16px clamp(20px, 4.4vw, 64px);
background: rgba(255,255,255,.85); backdrop-filter: blur(8px);
```

**P8 行式作品索引（替代卡片阵列）**
作品列表为全宽行：编号、项目名（大字）、类别、年份依次排开，行间 1px 细线：
```css
display: grid; grid-template-columns: 1fr 6fr 3fr 2fr;
align-items: baseline; padding-block: 24px; border-top: 1px solid;
```
hover 用 `transform: translateX(8px); transition: 150ms`。这是瑞士网站 work index 的标志性排布。

## 五、展示型网页结构骨架

1. **Hero**：全高或 80vh；超大标题贴容器左边线，右下角小号元信息（坐标/年份）形成对角张力；不居中。
2. **Manifesto**：8+4 分栏；宽栏放 2–3 句宣言式大字（28–40px），窄栏放小号补充段，顶部对齐；section 上 128px 下 96px。
3. **Work index**：P8 行式列表；可穿插一个 `grid-column: 1/-1` 的全出血图像打破节奏（刻意破格，且必须回到网格线）。
4. **About**：5/7 分割，sticky 编号标题 + 正文；数据（成立年份、项目数）用 hairline 分行排列，不做圆角统计卡片。
5. **Footer**：多栏元信息网格（4×N），顶部 1px 全宽线，最底一行版权贴页面最下缘；链接下划线 `text-underline-offset: 4px`。

## 六、常见错误

1. **居中排版**——消灭不对称张力。
2. **均匀卡片阵列**——三等宽卡片 × N 行是瑞士的反面；改不对称跨度或行式索引。
3. **间距脱离步长**——出现 13px、37px 等随意值，或 line-height 非 4 的倍数导致文本基线跨栏漂移。
4. **元素落入 gutter / 无目的地破格**——内容起止必须落在栏线上；只有强调目标明确时才允许 breakout，且必须回到网格线。

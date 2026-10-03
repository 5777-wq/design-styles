# De Stijl 研究笔记（风格派 / 新造型主义 → 网页 UI）

> 来源：Wikipedia（De Stijl / Neo-Plasticism / Rietveld Schröder House / Architype Van Doesburg）、MoMA（Broadway Boogie Woogie）、Jen Simmons Responsive Mondrian、Webflow/Awwwards/Behance 案例、Jotform「Mondrianism in Web Design」（Metro 谱系）、color-hex Mondrian palette、Pressbooks（De Stijl and Bauhaus 词汇表分界）。

## 一、史实定位

1917 年，Theo van Doesburg 在荷兰莱顿创办期刊《De Stijl》，运动因此得名。核心成员：**Piet Mondrian**（理论家，《造型艺术中的新造型主义》1917 连载、1920 法文单行本 *Le Néo-Plasticisme*，1925 年收入包豪斯丛书第 5 种）、**Theo van Doesburg**（组织者，《反构图》1924 引入 45° 对角线，直接导致 Mondrian 1924–25 年决裂退群；与 van Eesteren 的 Maison d'Artiste 模型 1923）、**Gerrit Rietveld**（红蓝椅 1918/约 1923 施色、乌得勒支施罗德住宅 1924——2000 年 UNESCO 世界遗产）、Bart van der Leck、Vilmos Huszár、J.J.P. Oud。Mondrian 正典：《红、黄、蓝构成》系列（1930 巅峰）、《百老汇布吉伍吉》（1942–43，MoMA 藏，唯一系统性「破戒」：黑线换成彩色线）。van Doesburg 1922 年在魏玛开班冲击包豪斯。

历史语义：De Stijl 追求战后普遍和谐的秩序，把画面还原为「横线 + 竖线 + 三原色」的最小词汇表——它不是装饰风格，而是一套**视觉语法**。网页上它是所有「格子风」（含 Microsoft Metro）的祖先。

## 二、12 条铁律（每条一句为什么）

1. **只用水平线与垂直线**——对角线与曲线属于元素主义和包豪斯，出现即不再是风格派。
2. **黑色分割线必须贯通到容器边缘，禁止悬空断裂**——贯通线是构图的承重墙，断线等于塌房。
3. **全局仅 6 色：红、黄、蓝、黑、白、灰**——禁止二次色、渐变、投影；色彩越少，秩序越强。
4. **任何两个彩色块不得相邻**——必须由黑线或白格隔开，这是 Mondrian 构图的硬规则。
5. **色块非对称分布但整体平衡**——一个主色大块（通常红）+ 若干小块；三色不必同时出现。
6. **白色是最大的颜色**——白格占画面 50% 以上，色块只是画面里的「事件」。
7. **直角统治一切：border-radius 一律 0**——圆角是自然形态的残余。
8. **黑线粗细全站不超过 3 档**——线宽即排版层级，多余档位制造噪声。
9. **用 CSS Grid 的 gap 画黑线**（容器铺黑、格子铺色）——结构上保证「线永远贯通」，而非逐条画 border。
10. **正文住白格，颜色住导航与标识**——大段文字不压色块（黄块只放黑字短标题）。
11. **等级靠格子面积与线宽表达**——面积即权重，不用下划线、斜体、花式按钮。
12. **断点之间保持行列次序**——先保结构再缩放，构图塌缩不许打乱阅读顺序。

## 三、设计 Token

### 配色 A：正典纯白版（社区通行 "Mondrian palette"）

| Token | Hex | 用途 |
|---|---|---|
| --red | `#DD0100` | 主 CTA、主色块（白字对比约 5.2:1，可放白字） |
| --yellow | `#FAC901` | 强调小块（**必须黑字**，对黑约 13:1） |
| --blue | `#225095` | 次级色块、链接色（白字约 7.9:1） |
| --black | `#0D0D0D` | 所有分割线、正文 |
| --white | `#FFFFFF` | 底色、白格 |
| --gray | `#8E8E8E` | 辅助文字、灰色块（仅 Broadway 变体） |

### 配色 B：米白纸感变体（CSS 教程通行色值）

红 `#E30613` / 黄 `#FFD800`（黑字）/ 蓝 `#0247FE` / 黑 `#0D0D0D` / 纸 `#F9F5F0`（白格用 `#FFFDF8`）/ 灰 `#B9B4AC`。

面积配比：白 ≥60%、黑线 8–10%、三色合计 ≤25%，单色块不超过画面 35%。

### 字体栈

- 标题（拉丁）：`"Archivo Black"`（Google Fonts）；历史彩蛋（仅 logo/点缀）：Architype Van Doesburg——据 van Doesburg 1919 年方格模数字母表复刻的商用字体。
- 正文/界面：`"Inter"` / `"Archivo"` + 中文 `"Noto Sans SC"`（400/500/700/900）。
- 标题与色块共存法：Archivo Black 黑字置于白格（首选）；或黑字置于黄块；红蓝块只放白色短词（≤2 词）。禁止三色字、描边字。

### 黑线粗细体系

12px：页首/页尾贯通线、hero 主分隔；8px：标准网格 gap（默认）；4px：卡片内次级分隔。
实现约定：最外层容器 `background: #0D0D0D`，Grid 用 `gap` 出线，天然贯通。

### 色块尺寸

桌面最小 96×96px（导航块 ≥120×48px、触达 ≥44px），移动端最小 72×72px；主色块 ≤ 视口宽 40%；正文白格 ≥320px 宽；每屏色块 ≤3 个；构图总格数 4–7 格为宜。

## 四、版式模式（6 个）

1. **正典 Hero 构图**：`grid-template-columns: 3fr 1fr 2fr; grid-template-rows: 2fr 1fr 3fr; gap: 8px`，areas `"t t r" "t t y" "b b y"`——大白格 t 放宣言，红块 r=CTA，黄小块 y 放年份徽标，底行 b 放副标。
2. **蒙德里安导航条**：高 64–72px，logo 白格 + 菜单项各为独立色块（min-width 96px），当前页用当期主色；导航即构图的一部分。
3. **章节画框模式**：每个章节一块白格，四周 8px 黑线贯通至页面边缘；章节编号用 24×24 色块角标挂在格子左上（贴线、不居中悬浮）。
4. **不等分画廊**：`repeat(12, 1fr)`，卡片跨 4/5/3 列不等，gap 8px；一组内只允许 1 张卡着色，其余白底；图片 `object-fit: cover`、直角、无滤镜。
5. **色块 KPI 条**：红/黄/蓝三格各承载一个数字（Archivo Black 48px，黑字或白字按对比度规则），说明文字落白格。
6. **Rietveld 交错页（About）**：嵌套 Grid + 8px 黑边白块层叠模拟板片交错（z-index 错落），禁止 rotate/skew；页脚用「封底构图」收尾：一条 12px 贯通线 + 三个 12px 三色小方块横排。

## 五、动效

**允许**：hover 色块 `filter: brightness(1.06)` 或内侧线宽 8→12px 加重反馈（≤150ms）；导航黑条 0→8px 高度展开；入视口 opacity 0→1（无位移或 ≤8px）；`prefers-reduced-motion` 下全部静止。
**禁止**：旋转、斜切、弹跳；对角线运动轨迹；颜色渐变与 hue 过渡；box-shadow 悬浮感（用加粗黑线代替 elevation）；色块平移穿越黑线；视差滚动；持续闪烁。

## 六、移动端

1. 构图塌缩按「正文白格 → 首要色块 → 次要格」线性化，各断点重写 `grid-template-areas` 但保持相对次序。
2. 线宽降一档（12→8、8→4），黑线永不消失——线消失等于风格消失。
3. 导航塌缩为纵向色块列表，每项高 ≥48px。
4. 横向 `padding: 0`，保证贯通线触达屏幕两边。
5. <480px 时色块删减到 ≤2 个，最小 72×72px。

## 七、示范页内容方案

虚构品牌：**VML · Vorm en Lijn**（虚构荷兰风格派家具工作室，1918–2026 主题单页）。① 顶部 12px 贯通线 + 蒙德里安导航（家具/陈列室/工坊/联系）；② 正典 Hero：大白格 headline「一九一八年的椅子，今天依然站立」+ 红块 CTA「预约陈列室」+ 黄块「1918→2026」；③ 白格故事区：红蓝椅复刻版（3 段文字 + 2:1 图片格）；④ KPI 色块条：106 年 / 12 位匠人 / 3 种原色；⑤ 不等分画廊：6 件产品（1 红标卡 + 5 白卡）；⑥ Rietveld 交错 About 板；⑦ 封底构图页脚 + 三色方块行。

## 八、反模式与 bauhaus 判据

反模式（任一出现即退化为「蒙德里安连衣裙贴图」——YSL 1965 式的把构图当印花而不是当结构）：色块相邻；出现对角线/旋转；圆角；黑线悬空断裂；色块多而碎。

**选 De Stijl 还是选 bauhaus**：De Stijl 只有正交 + 黑白 + 三原色，无圆、无三角、无 45°；bauhaus 有圆方三角基础形与斜向动势，气质更热。判据一句话：**页面里只要有一个图标或插画需要圆或三角，选 bauhaus；全部视觉都能用横竖线段完成、且品牌想表达秩序与严肃（美术馆、基金会、建筑、家具、文档型站点），选 De Stijl。**

## 九、信息来源

- Wikipedia – De Stijl: https://en.wikipedia.org/wiki/De_Stijl
- Wikipedia – Neo-Plasticism: https://en.wikipedia.org/wiki/Neo-Plasticism
- MoMA – Broadway Boogie Woogie: https://www.moma.org/collection/works/78682
- Jen Simmons – Responsive Mondrian: https://labs.jensimmons.com/
- Jotform – Mondrianism in Web Design: https://www.jotform.com/blog/mondrianism-in-web-design
- color-hex – Mondrian Color Palette: https://www.color-hex.com/color-palette/25374
- Wikipedia – Architype Van Doesburg: https://en.wikipedia.org/wiki/Architype_Van_Doesburg
- Pressbooks – De Stijl and Bauhaus: https://pressbooks.pub/art104/chapter/de-stijl-and-bauhaus

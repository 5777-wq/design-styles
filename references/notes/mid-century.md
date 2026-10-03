# Mid-Century Modern 研究笔记（1950s 美国现代平面设计 → 网页 UI）

> 来源：Kittl Atomic Age Guide、Media.io 与 Color-Hex（MCM 配色）、Kate McEnroe、Alvin Lustig 官方档案、New Directions、Smithsonian、CSS-Tricks Shapes、css-generators、Smashing Magazine、Siteinspire（The Mid-Century Modernist）、OnExtrapixel 45 Retro Websites（Lost Type Co-op、Austin Eastciders、Cast Iron Design 等真实案例）。

## 一、起源与正典（历史真实性锚点）

1945–1965 年美国商业设计黄金期：战后乐观主义、原子时代想象、广告业爆发，欧洲现代主义（包豪斯、构成主义，经 Moholy-Nagy 传入）与美国商业实用主义融合。

- **Paul Rand**：《Thoughts on Design》(1946–47) 确立「图形即观念」；IBM 八条纹 logo（1972，条纹暗示速度而不破坏字形）、Eye-Bee-M 字谜海报（1981，rebus 手法）、ABC (1962)、UPS (1961)、Westinghouse (1960)。核心方法论：**符号的经济学**——wit 是设计的一部分。
- **Saul Bass**：《金臂人》(1955) 海报与标题序列——白底、撕裂黑纸、倾斜手臂，把形象削到最少笔画；《惊魂记》标题；AT&T 贝尔球 (1969)、United Airlines。
- **Eames 夫妇**：家具模压曲线 + 《Powers of Ten》尺度叙事；**Alexander Girard** 纺织的民俗化几何重复单元；**Josef Albers**《向正方形致敬》限域叠色；**Alvin Lustig** New Directions 书封（1941–1952）——用抽象几何象征文学内容（《欲望号街车》封面：淡紫底上三个极简人形）。

## 二、标志性母题（必须具体可画）

有机 blob 与 boomerang 回旋镖；原子星芒（4/8/12 尖）与轨道线 + 圆点；符号化图形（眼、手、箭头、唱片、杯——Rand 符号论）；哑光暖色；「几何无衬线 + 粗 slab + script 点缀」三重奏；纸纹理与 2–4 色专色印刷感；温和不对称构图（60/40、元素偏置）。Atomic Age 补充：轨道式布局（元素绕焦点）、模块化重复单元（源自纺织）、线条暗示速度。

## 三、12 条铁律（每条一句为什么）

1. **每屏最多一个装饰母题**（星芒或 blob 二选一）——高级感来自符号经济学，堆叠即「复古贴纸机」。
2. **整页限 4–5 个颜色位**——模拟当年有限油墨的专色印刷。
3. **所有彩色必须加灰调**（饱和度约 45–65%）——50 年代油墨无荧光色，哑光才有时代感。
4. **标题用几何无衬线或粗 slab，正文用中性无衬线**——粗细对比是 50s 编辑排版骨架。
5. **script 手写体全页只许出现一处**（字标或一句 slogan）——手写体泛滥是复古第一大忌。
6. **blob 用 8 值 border-radius，且禁止 morph 动画**——原版是静态丝网印刷图形。
7. **星芒用 clip-path/SVG 纯色绘制，禁渐变**——丝网印刷不存在渐变。
8. **纸纹理仅作噪点叠加**（opacity ≤4%，fixed）——负责年代感，不负责抢戏。
9. **构图温和不对称**：60/40 分栏、元素偏置、大量留白——Rand 版式基本法。
10. **圆角只有两种语言：全圆胶囊（999px）或近直角（≤16px）**——当时不存在「默认 4px 小圆角」。
11. **分割用锯齿边、虚线、打孔线**——继承 diner 菜单与收据的原版语法。
12. **选定一个品牌符号（眼/回旋镖/唱片）贯穿全页**——Rand：「设计是品牌的沉默大使」。

## 四、设计 Token

**配色 A · 经典暖调**：奶油 `#F5EFE0`（底）/ 芥末 `#E3B23C` / 赤陶 `#D96C3F` / 灰蓝 `#5B7C99` / 炭 `#2B2B28`（文字）。
**配色 B · 青绿粉变体**：青瓷绿 `#2F6F73` / 鲑粉 `#E8A08D` / 芥末 `#D4A437` / 米白 `#E7D8C3` / 胡桃棕 `#3B2F2A`。
**配色 C · Atomic Era**：赤土 `#D97364` / Dutch 白 `#F1E4B7` / 铅蓝 `#83B3AB` / 深蓝黑 `#21233A`。

**字体（Google Fonts）**：display `Jost` 600/700（Futura 复刻）或 `Alfa Slab One`（粗 slab）；点缀 `Yellowtail` 或 `Kaushan Script`（仅一处）；正文 `Inter` 或 `Source Sans 3`；中文 `Noto Sans SC` 400/700，标题字距 +0.05em。总字族 ≤5，一条 link 引入。

**形状参数**：卡片圆角 20–24px 或全圆；blob `border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%`（备选 `58% 42% 55% 45% / 45% 55% 45% 55%`）；星芒 `clip-path: polygon()` 交替内外顶点（12 尖，内半径 ≈0.5R，css-generators 生成）；boomerang 用 SVG 双弧 path；打孔边用 radial-gradient 圆点列 + `border-bottom: 2px dashed`。

## 五、版式模式（6 个）

1. **Blob Hero**：左文右形，blob 占约 45vw，内嵌单一品牌符号；标题 Jost 64–80px。
2. **星芒公告条**：副色底横带，3 枚 24px 星芒等距分布。
3. **菜单卡**：名称（Jost 500 18px）+ 点线 leader + 价格（Alfa 18px）；分类标题小型大写、字距 0.12em。
4. **票券区块**：打孔边 + 虚线内分割，整块 rotate(-1.5deg)，用于营业时间/地址。
5. **符号三联卡**：三张等宽圆角卡，各配一个线性符号（杯/唱片/眼），等距网格。
6. **Albers 宣言区**：同色系叠色方块背景 + 反白大字引言，替代插图。

## 六、动效

**允许**：胶囊按钮 hover 硬阴影位移 2px（150ms）；星芒极慢自转（60s linear infinite）；内容淡入上移 8px；票券 hover 摆正回 0deg。
**禁止**：blob morph 变形、弹性 bounce、霓虹发光闪烁、3D 翻转、渐变扫光、marquee、视差滥用——一切「数字感强于印刷感」的运动。

## 七、移动端

1. Blob Hero 改文字置顶 + 标题下方 70vw 圆形色块。
2. 星芒数量减半、单枚 ≤40px，绝不压文字。
3. 菜单 leader 点线用 flex + dotted border-bottom 单栏版。
4. 触控目标 ≥44px，胶囊按钮移动端全宽。
5. display 40px / 正文 16px 起步，行高 1.6。

## 八、示范页内容方案

**虚构唱片行「Moonbeam Records」（1955）**：① 导航：Yellowtail 字标 + Jost 菜单（灰蓝底奶油字）；② Hero：奶油底 + 赤陶 blob + 黑胶圆盘符号，slogan「音乐，像 1955 年一样转」；③ 星芒公告条「本周新到 · 原版 78 转上市」；④ 菜单卡版「本周榜单」：曲名 + 点线 + 价格，分类标题 JAZZ / BLUES / POP；⑤ 符号三联卡：唱片订购 / 唱机修复 / 上门估价；⑥ 票券区块（rotate -1.5°）：地址、营业时间、电话；⑦ Albers 宣言区：叠色方块 + 引言「一张唱片是一次原子时代的旅行」；⑧ 页脚：回旋镖小图标 + 营业信息。

**反模式自检**：星芒 + 回旋镖 + 手写体 + 棋盘格 + 霓虹同页出现 = 贴纸机；全页加棕色 sepia 滤镜 =「太脏」。高级感只来自三件事：**一个符号说一件事、限色加灰、充足留白**。

## 九、信息来源

- Kittl — Atomic Age Design Guide: https://www.kittl.com/blogs/atomic-age-design-guide-asp
- Media.io — Mid Century Modern Color Palette: https://www.media.io/color-palette/mid-century-modern-color-palette.html
- Alvin Lustig 档案: https://alvinlustig.com/book-jackets · https://www.ndbooks.com/author/alvin-lustig-designers-page
- Smithsonian — Lustig《欲望号街车》书封: https://www.aaa.si.edu/collections/items/detail/alvin-lustig-book-jacket-streetcar-named-desire-16061
- CSS-Tricks — The Shapes of CSS: https://css-tricks.com/the-shapes-of-css
- css-generators 星芒: https://css-generators.com/starburst-shape
- Siteinspire — The Mid-Century Modernist: https://www.siteinspire.com/website/1967-the-mid-century-modernist
- OnExtrapixel — 45 Retro Website Designs: https://onextrapixel.com/45-great-examples-of-retro-website-design

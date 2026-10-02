# 包豪斯研究笔记（Bauhaus → 网页 UI）

> 来源：SkillsUI Bauhaus Guide、Kittl、Pawluk Studio、MoMA（Joost Schmidt 1923 海报）、Encyclopedia of Design（Bayer Universal）、Letterform Archive、Dribbble 案例集、Google Fonts。

## 一、起源与精神内核

1919 年格罗皮乌斯在魏玛合并美术学院与工艺学校创立包豪斯；1925 年迁德绍（玻璃幕墙校舍落成），后迁柏林，1933 年被纳粹关闭，仅存续 14 年。核心人物：Kandinsky（形式与色彩理论）、Klee（《形式与造型讲义》）、Moholy-Nagy（构成主义、斜线实验）、Albers（预科「纸与形状」练习）、Herbert Bayer（Universal 字体、德绍校舍导视）、Joost Schmidt（1923 展览海报）。德绍时期纲领「艺术与技术的新统一」——网页翻译的方向：**不是复古 1920s，而是「几何作为功能语言」**。

关键锚点：Kandinsky 1923 年问卷实验——多数人将**黄填三角、红填方、蓝填圆**。形状与色彩有固定心理学配对，这是包豪斯区别于任意「儿童色块」的理论根据。

## 二、标志性视觉母题

- **三原色几何**：圆/方/三角 × 蓝/红/黄，按 Kandinsky 配对使用，不是随机撒色。
- **Bayer Universal 理想**（1925）：纯几何构字、单一字表（去大写）、圆规直尺可作。网页对应：几何无衬线 + 统一的全大写标签体系。
- **Joost Schmidt 1923 海报**：「圆组成的十字」——中央红色圆 + 放射弧线，下方网格切成楔形，BAUHAUS 沿对角阶梯排布；构成主义**斜线与旋转**的来源。史实配色是**黑/红/米白**（不是三原色）——暗色海报版色板有史实依据。
- **Futura**（Renner, 1927）：包豪斯滋养的几何无衬线商业峰。
- **粗规则线与实心黑**：德绍校舍栏杆、Moholy 封面的横竖黑线，是版式骨架而非装饰。

## 三、配色（3 套）

**经典三原色版 `bauhaus-primary`**（默认，白底海报感）：

| token | hex | 用途 |
|---|---|---|
| --color-red | `#E2001A` | 主 CTA、强调、「方」位 |
| --color-yellow | `#F5A800` | 高亮、次级强调（避开浅黄） |
| --color-blue | `#1D4E89` | 链接、信任区块、「圆」位 |
| --color-ink | `#111111` | 正文、规则线、大标题 |
| --color-paper | `#F5F1E6` | 页面底色（米白） |
| --color-surface | `#FFFFFF` | 卡片/色块底 |

**海报构成版 `bauhaus-poster`**（Joost Schmidt 依据，仅黑/红/米白，适合 hero 与深色区块）：red `#D9262C`、ink `#141414`、paper `#EFE9DC`。
**现代校准版 `bauhaus-calibrated`**（屏幕对比度友好，正文 AA 达标）：red `#D7263D`、yellow `#F2B705`（只作背景色块，不作小字文字色）、blue `#1A47B8`、paper `#FAF7F0`。

硬性约束：单屏主色 ≤3 个；黄永远不当正文文字色；黑与米白承担 80% 面积，三原色各占 <10%。

## 四、字体

- **展示/标题**：`Jost`（Google Fonts，Futura 谱系最近复刻）——首选；备选 `League Spartan`（更粗更墩）、`Poppins`（更圆更现代，仅当需要亲和感）。
- **正文**：`Inter` 或继续 `Jost` 400（包豪斯偏好单字族多字重，混族破坏 Universal 精神）。
- 引入：`https://fonts.googleapis.com/css2?family=Jost:wght@300;400;500;700;900&family=Inter:wght@400;600&display=swap`
- **中文**：`Noto Sans SC`（几何骨架最接近）；标题 700–900，正文 400。中文不强行全大写/斜体，以字重与字距做层级。
- **字距**：全大写标签 0.12em；正文 0；≥80px 展示标题 -0.02em。

**字阶**：display 72–120px/900；h1 48px/700；h2 32px/700；h3 24px/500；body 16–18px/400；line-height 1.5（标题 1.05）；行长 60–72ch。

**几何纪律**：矩形一律直角（border-radius: 0），圆必须正圆（50%、宽高相等），不存在 8px 中间态圆角。规则线 1px 实线（细节）与 3–4px 实线（分节），禁虚线/双线/渐变线。禁投影，用实色硬阴影（`4px 4px 0 #111`）表达层叠。

## 五、版式模式（6 个）

1. **Schmidt 海报 Hero**：12 栅格；中央或偏左 1/2 大圆（直径 4–5 列宽，红或蓝），叠加 45° 旋转的黄色三角（2 列宽）贴圆边；标题 3–5 词全大写沿左轴，右侧留白 4 列；底部通栏 4px 黑线。
2. **色块导航条**：导航项 = 等宽直角色块，每项一种原色/黑，文字反白，active 项色块下压 4px 黑条；高度 64px。
3. **楔形分割带**：区块之间用旋转 45° 的方形或三角形色带过渡（高 96–160px），替代圆弧波浪。
4. **Bento 几何卡组**：4–6 个直角卡片混合：实色卡（几何图形做图标）、白卡黑描边、黑卡反白字；图标一律内联 SVG 基本几何（圆+线），禁拟物图标库。
5. **规则线目录页**：列表行间 2px 黑线，行号用 900 字重超大数字，hover 整行反色（黑底米白字）。
6. **数据几何徽章**：统计数字 = 正圆色块内反白数字（蓝圆）+ 黑线刻度。

## 六、动效

**允许**：hover 硬阴影位移 ≤2px（120ms）；色块 hover 反色（0–80ms）；SVG stroke-dashoffset 直线绘制（400ms linear——几何必须匀速）；45° 旋转入场（一次性 300ms ease-out）。
**禁止**：弹性/spring 缓动、淡入淡出堆叠、渐变过渡动画、形状变形 morph、阴影扩散动画、视差滚动。

## 七、移动端

1. 主角几何缩放不删减：hero 大圆改 `min(60vw, 320px)`，保持「每屏一个主角」。
2. 色块导航折叠为全屏直角菜单：黑底 + 原色块菜单项，配 45° 三角开关图标。
3. 触控目标 ≥44px，用色块面积保证（按钮 = 整块色块，不是描边幽灵按钮）。
4. 楔形分割高度减半（48–80px）。
5. display 48px 起，正文 ≥16px，黄底区块禁用。

## 八、与瑞士风格的分界（判据）

包豪斯：几何图形本身是主角，构成即内容，允许大面积色块、45° 旋转、色块导航——栅格只是构图工具。瑞士：几何退场为网格后台，信息层级是主角，无装饰图形、无旋转、摄影担纲。
**网页判据：删掉所有几何色块后页面仍「成立」= 瑞士；删掉后信息崩塌、依赖色块才能表意 = 包豪斯。** 信息密度高的仪表盘应使用瑞士 skill。

## 九、反模式（幼稚拼贴的成因）

1. 三原色等比例均铺（各 ~33% 面积）= kindergarten 感；正确是黑/米白主导。
2. 到处撒小圆点小三角当「彩蛋装饰」，几何不承担功能。
3. 圆角卡片 + 三原色 = Material Design 侵权感。
4. 违反 Kandinsky 配对（蓝三角、绿三角）。
5. 混入非几何元素：手写体、插画风插画、不规则蒙版照片。
6. 颜色加透明度/柔光/渐变——包豪斯的色是印刷油墨实色。
7. 每屏超过 3 种原色 + 黑白，或黄字上白底（不可读）。

## 十、信息来源

- SkillsUI Bauhaus Web Design Guide: https://skillsui.app/blog/bauhaus-web-design
- Kittl Bauhaus Design Principles: https://www.kittl.com/blogs/bauhaus-design-principles-adv
- Pawluk Studio, Bauhaus in Web Design: https://www.pawlukstudio.pl/en/blog/bauhaus-in-web-design
- MoMA 收藏，Joost Schmidt 1923 海报: https://www.moma.org/collection/works/6235
- Encyclopedia of Design, Herbert Bayer Universal: https://encyclopedia.design/2023/01/10/herbert-bayer-universal-typeface
- Letterform Archive, Bauhaus Typefaces: https://letterformarchive.org/news/bauhaus-typefaces-part-two/
- Google Fonts Jost: https://fonts.google.com/specimen/Jost

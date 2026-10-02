# 日式侘寂 / Japandi 研究笔记

> 来源：Hara Design Institute、Kengo Kuma & Associates、和色大辞典 (colordic.org)、NIPPON COLORS、utsubo Japanese Web Design Style Guide、Kittl Japandi guide、Architectural Digest、tategaki 实现文档、Ippodo Tea、星野リゾート。

## 一、美学根源

**侘寂（wabi-sabi）**：不完美（fukinsei 非对称）、无常（mujō）、不圆满（koko 朴素）——从茶室美学发源，接纳残缺、锈迹与时间痕迹。**间（ma）**：不是「留出来的空白」，而是「被赋予能量的、主动做功的间隔」——"Space is the design."。**原研哉《白》与「空」**：白不是 empty 而是 ready-state——什么都不是、因而什么都可以是的容器；MUJI 方法是「去除一切试图左右你思维的元素」。**无印良品「这样就好」（これでいい）**：用克制的满足感替代欲望刺激——2003 年「地平线」campaign 用一张几乎全空的风景照拿下东京 ADC 大奖。**隈研吾「负建筑」**：建筑应「输给」环境；材料**粒子化**（木格栅、和纸、小单元组合）消解体量——界面不应是「物」，而应退后成为材质、光线与间隙的载体。

## 二、Japandi 与日本网页的两极

Japandi（日式侘寂 + 北欧 hygge/lagom，2020+ 室内热词）配方：日式提供有机肌理、不完美、非对称但平衡；北欧提供功能性、温度与舒适。网页上的 Japandi ≈ 日式留白与大地色 + 北欧稍高的功能密度。

关键认知：日本网页设计本身有两极——大众端（乐天、Yahoo! Japan：高密度、链接墙，因「信息=信任」文化）与高端端（奢侈、旅馆、美术馆：一屏一意、低密度、明朝体）。**本规范只做高端极，切勿混用两极规则。**

## 三、与瑞士风格的分界

| 维度 | 瑞士国际主义 | 日式禅意 |
|---|---|---|
| 秩序来源 | 数学网格、客观 | 自然、不完美、余韵 |
| 留白目的 | 层级与视线引导 | 「间」的心境，空白即内容 |
| 字体 | 无衬线（Helvetica） | 衬线/明朝体 |
| 层级手段 | 色块、字重 | 细线、字距、留白 |
| 不对称 | 动态对角冲突 | 「均工」静平衡 |
| 肌理 | 禁止 | 必须（纸、木、噪点） |
| 节奏 | 快、锐利 | 慢、呼吸 |

## 四、设计 Token 详表

### 配色（hex 经和色大辞典 colordic.org 核验）

**方案 A「纸与墨」（默认）**：底色 生成り kinari `#F7F3EC`（可交替 `#FBFAF5`）；卡面 胡粉 gofun `#FDFCF8`；主文字 墨 sumi `#26231F`（标题可用 `#1A1A18`）；次级 鈍 nibi `#6E6A61`；细线 rgba(38,35,31,.16)；点缀 藍鼠 ainezu `#6C848D`。

**方案 B「茶土」**（茶/食品类主点缀）：利休茶 `#A59564`、黄土 `#C39143`、小豆 `#96514D`、白茶 `#DDBB99`。
**方案 C「朱印」**（强调/印章专用，小面积）：臙脂 enji `#B94047`（可用深緋 `#C9171E` 调暗）；辅助 洗柿 `#F2C9AC` 做浅色块。

### 字体（Google Fonts 引入名）

- 中文主体：**Noto Serif SC**（200/300/400/500）
- 假名/日文点缀：**Shippori Mincho** 或 **Zen Old Mincho**（400/500）
- 中文楷书点缀（一两处手写感）：**LXGW WenKai TC**（霞鹜文楷；简体需自托管）或 **Ma Shan Zheng**（仅单字级）
- 西文衬线：**Cormorant Garamond**（300 light + italic）或 EB Garamond
- 无衬线辅助：**Noto Sans SC**（300/400）
- 栈：`"Cormorant Garamond","Noto Serif SC","Shippori Mincho",serif`（西文先于中文）

### 竖排（writing-mode）实现要点

- `writing-mode: vertical-rl`（列自右向左，正统日式；vertical-lr 不合和风）
- 默认 `text-orientation: mixed` 让标点正确转向；拉丁字母会横倒，混排时改横排或避免
- `line-height` 即列间距（建议 2–2.4）；`letter-spacing` 变纵向字距（0.3–0.5em 出「落款感」）
- 两位数字纵中横排用 `text-combine-upright: all`
- 限 `max-height` 控列长；边框用 logical properties（border-block-*）防方向错乱
- 只用于标题/短语/落款，永远不做正文

### 字号 / 字重 / 字距（桌面基准）

- Display（hero 竖排大字）：72–120px，weight 300–400，tracking 0.35em
- H1 40–48 / H2 28–32 / H3 20–22
- 正文 15–17px，weight 400，line-height 1.9–2.1，tracking 0.05em
- 西文小标签 10–11px，uppercase，tracking 0.25–0.35em，weight 400
- **禁 700+ 粗体**（明朝体粗体即「凶」）；强调靠字号与留白

### 圆角 / 线条 / 肌理

- border-radius：0（默认）/ 2px（图卡）；圆点符号 3–4px 正圆
- hairline：1px solid rgba(38,35,31,.16)（移动端恒 1px，0.5px 部分安卓不渲染）；重要分隔用双细线（间隔 3px 两条 1px）
- 印章：24–32px 方形臙脂块内反白 1–2 字，rotate(-3deg) 以内
- 确需阴影时仅此一档：`0 4px 24px rgba(26,26,24,.06)`
- 全局纸纹：SVG `feTurbulence`（fractalNoise, baseFrequency≈0.8）data-URI 平铺，`position:fixed` 覆盖层，opacity 3–6%，`mix-blend-mode:multiply`，pointer-events:none
- 和纸纤维感：baseFrequency 拉长（0.9/0.15）+ 沿纤维方向 scale(1,2)；麻布纹：`repeating-linear-gradient(45deg,…)` 2px 周期、明度差 ≤3%
- 摄影处理：自然光、低对比、可加 1–2% sepia 统一色温

## 五、版式模式（7 个）

1. **「一文字入魂」Hero**：100svh；竖排 4–8 字标题 72–120px 置于右侧 20–30% 处，左侧整片空白；右下角印章；底部居中 hairline + "Scroll"。空白占比 ≥65%。
2. **「间之栅格」**：12 列网格但内容只占 4–5 列，offset 至非中心位（col 2–6 或 7–11）；正文 max-width 34–40 字符；模块纵向间距 96–160px。
3. **「横线章节」**：全宽 1px hairline + 左端 4px 圆点 + 汉数字序号「壱・弐・参」14px + 右端英文小标签；上 padding 48 下 24。
4. **「小图大空」交替**：图宽 38–45%，图文左右交错（约 7:3），下一模块镜像；图为材质空景，radius 0。
5. **「竖排落款」**：右缘固定竖排站点标语 12–14px，tracking 0.4em，鈍色；滚动时 opacity 淡至 0.4。
6. **「静衡卡片」**：2–3 列产品卡，无边框无阴影，图上文下；名称衬线 16px + 价格 EB Garamond italic；hover 仅图片 scale 1.04（800ms）。
7. **「轻脚注页脚」**：上方 160px 空白后一行式页脚：竖排落款 + 12px 地址/版权 + 一行英文标签；无多列 sitemap。

## 六、动效（慢是侘寂的无常感，不是延迟）

**允许**：opacity 淡入 600–1200ms；translateY 12–20px 淡入上移 800–1200ms；图片 scale 1.0→1.04（800–1500ms）；hairline scaleX 0→1（800ms）；hover opacity 0.7（400ms）；极缓视差（系数 ≤0.05）；页面间纸色淡入过渡（400–600ms）；IntersectionObserver threshold 0.15、stagger 120–180ms；统一缓动 `cubic-bezier(.16,1,.3,1)` 或 ease-out。
**禁止**：bounce/elastic/spring 任何弹性缓动；大位移 slide；3D 翻转；跑马灯；快速自动轮播（<5s）；鼠标跟随特效；进度条式 loading（改为静态短句 + 3 圆点呼吸 2s+）；多层视差叠加。
**节奏原则**：全站比用户预期慢半拍，但单项 ≤1.2s（不慢到像卡顿）。

## 七、移动端

1. 正文一律横排；竖排标题保留但降至 32–48px 且 ≤2 列。
2. 纵向留白按 0.5–0.6 收缩（160→72px），hero 空白仍 ≥40%。
3. 细线恒 1px；触控目标 ≥44px。
4. LCP 优先：hero 用静图 + 淡入，禁重 JS 动效；遵守 prefers-reduced-motion。
5. 正文 ≥15px、行高 ≥1.9——大行距是日式可读性底线。

## 八、反模式与适用边界

**反模式**：樱花/灯笼/艺伎/和服贴图插画（伪和风）；毛笔字体排整段正文；竖排正文；顶天立地一块孤字的「空洞留白」；用深底白字装「禅」（茶室是纸、木与光，不是黑）；把服务器慢包装成「加载仪式感」。
**适用**：茶/酒/香/器物匠人品牌、温泉旅馆与酒店、美术馆与文化机构、和菓子/怀石料理、婚礼与摄影工作室。
**不适用**：SaaS 后台、资讯门户、工具产品、儿童品牌、促销驱动电商。

## 九、信息来源

- Hara Design Institute（原研哉事务所）: https://hara.ndc.co.jp/
- Kengo Kuma & Associates: https://kkaa.co.jp/ · Architecture of Defeat: https://kkaa.co.jp/en/books/architecture-of-defeat-2
- 和色大辞典（传统色 hex）: https://www.colordic.org/w · NIPPON COLORS: http://nipponcolors.com/
- utsubo – Japanese Web Design Style Guide（ma 与两极论）: https://www.utsubo.com/blog/japanese-web-design-style-guide
- Kittl – Japandi style guide: https://www.kittl.com/blogs/japandi-style-design · AD Japandi 101: https://www.architecturaldigest.com/story/japandi-style-101
- 縦書き实现: https://tategaki.github.io/explan4.html · https://fastcoding.jp/blog/all/frontend/css-writing-mode-tategaki
- 原研哉哲学: https://blakecrosley.com/zh-Hans/blog/design-philosophy-kenya-hara
- 案例: Ippodo Tea 一保堂茶铺 https://global.ippodo-tea.co.jp/ · 星野リゾート HOSHINOYA https://hoshinoresorts.com/ja/brands/hoshinoya/

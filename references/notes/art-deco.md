# Art Deco 研究笔记（装饰艺术 → 网页 UI）

> 来源：Wikipedia（1925 巴黎博览会）、Britannica、Mad Paris「1925-2025」、Swann Galleries、Van Cleef & Arpels 档案、Qode Interactive（真实网页案例：Hôtel Léna / Club Raia / Hotel Icon）、MDN repeating-conic-gradient、FAMSF（Lempicka）。

## 一、历史考证

1925 年 4 月起，巴黎举办「现代工业与装饰艺术国际博览会」（Exposition Internationale des Arts Décoratifs et Industriels Modernes），风格当时被称为 "Style 1925"；**"Art Deco" 一词在 1966 年巴黎装饰艺术博物馆回顾展后才流行**（1968 年 Bevis Hillier 定名）。正典坐标：

- 家具师 **Émile-Jacques Ruhlmann**（博览会「收藏家酒店」Hôtel du Collectionneur）
- 海报师 **Cassandre**（《L'Atlantique》1931、《Dubonnet》1932、《Normandie》1935——低视角巨轮 + 自创字体 Bifur/Peignot 是 Deco 平面教科书）
- 建筑：**克莱斯勒大厦**（William Van Alen, 1930）与**帝国大厦**（1931）的阶梯退台；**迈阿密海滩装饰艺术区**（热带流线变体：奶油底 + 粉彩 + 眉毛窗）
- 绘画：**Tamara de Lempicka** 的立体主义式棱角块面
- 1922 图坦卡蒙墓发掘引发埃及热：莲花、翼日轮、「金 + 黑 + 青金蓝」
- 《了不起的盖茨比》(2013) 是当代影视复刻范本

## 二、标志性母题（仅用这些，别发明）

旭日纹/放射扇形 (sunburst)、阶梯退台 (ziggurat setback)、平行细线组与嵌套线框、人字纹 chevron、雕平浮雕式几何（低浮雕、非透视）、埃及化母题（莲花、翼日轮、方尖碑轮廓）、流线型速度线（3 条一组平行圆弧）、严格对称与垂直塔式骨架。

## 三、12 条铁律（每条一句为什么）

1. **一切对称**——Art Deco 是唯一以正面性 (frontality) 为美学的风格，版面默认左右镜像居中；不对称即现代主义，摧毁识别性。
2. **深哑光底 + 小面积金线**——金是「描线」不是「填色」，金占画面 ≤10% 才贵；满屏金字 = 婚庆 PPT。
3. **只用几何装饰，禁用有机卷草**——藤蔓涡卷花体属于新艺术 (Art Nouveau) 与维多利亚，混种信号。
4. **细线是骨架**——分隔、边框、饰带用 1px 级 hairline 的多重嵌套表达精致；粗黑边属于 Neubrutalism。
5. **阶梯代替曲线**——转折用 45° 斜切或直角退台 (ziggurat)；大圆角只允许出现在流线变体（定向圆弧，不是软糖圆角）。
6. **大写 + 宽字距做展示体**——Deco 海报字全是全大写几何体，letter-spacing 0.15em 起步（0.12–0.25em 区间）。
7. **最多两套字族**——一个几何展示体 + 一个正文体；展示体只做标题。
8. **配色限三方**——一个深底 + 一个珠宝色（翡翠/宝蓝/酒红）+ 金，外加米白做文字；每页 ≤4 种色彩。
9. **垂直分层像建筑立面**——内容按「开间」分栏，栏间细线，模拟摩天楼窗格节奏；栏内禁止再分栏。
10. **摄影必须处理**——降饱和/黑白或深色叠加 + 细金框装裱；原图直出破坏「雕平」质感。
11. **留白也是材料**——奢华来自空旷大堂的比例感；密集段落用「衬线正文 + 大段距」缓冲。
12. **动效克制对称**——只允许从中轴向两侧对称展开、缓慢线条生长、极慢旭日旋转；弹跳、弹簧、3D、霓虹闪烁禁止（那是赛博/蒸汽朋克的语言）。

## 四、设计 Token

### 配色（3 套）

| Token | A 午夜翡翠（默认） | B 宝蓝爵士 | C 迈阿密流线（浅色） |
|---|---|---|---|
| bg 深底 | `#0D0D0F` | `#0A1128` | — |
| bg 面/卡 | `#16161A` | `#14213D` | `#F7EFE2` 奶油底 |
| 珠宝强调 | 翡翠 `#0F5132`（亮态 `#1E7A46`） | 宝蓝 `#2B4C8C` | 焦橙 `#C1622B` |
| 金/铜线 | `#D4AF37`（高光 `#E8C878`） | 古金 `#C9A227` | 红棕铜 `#B08968` |
| 正文浅字 | 香槟米白 `#F2E8D5` | 象牙 `#FFFFF0` | 深棕 `#5C4033` |
| hairline | rgba(212,175,55,.55) | rgba(201,162,39,.5) | `#2B2B2B` @1px |

### 字体（Google Fonts 全部实测可用）

- 展示体主选：**Limelight**（戏院跑马灯戏剧体，品牌字）、**Poiret One**（几何细体，副标/装饰字，只大号）
- 奢华衬线：**Cormorant Garamond**（正文衬线首选）/ Playfair Display；碑铭备选 Cinzel（≤3 词）、Marcellus
- 海报条形：**Oswald**（章节标签/票务）；Monoton 仅限 logo 一处
- 正文无衬线：**Jost**（Futura 血统，比 Josefin Sans 耐读）
- 引入：`family=Limelight&family=Poiret+One&family=Cormorant+Garamond:ital,wght@0,400;0,600;1,400&family=Jost:wght@300;400;500&family=Oswald:wght@500`

### 字阶与字距

品牌字 72–120px / Limelight；H1 48–72px；H2 32–40px 全大写；eyebrow 标签 13–14px / Oswald / letter-spacing 0.3em；正文 17–18px / 行高 1.7（衬线）或 1.6（Jost）；展示体统一 0.12–0.25em 宽字距；数字/年份用 Cormorant 600。

### 细线与边框体系

- 单线 1px；双线框 = 外 1px + 内 1px 间隔 4–6px（outline + border 或双层伪元素）；重要卡用三线（1px/2px/1px）
- 四角饰件：`::before/::after` 画 8–12px 直角折线或菱形 ◆（CSS rotate 45° 小方块）
- 人字纹衬带：`repeating-linear-gradient(45deg, gold 0 2px, transparent 2px 10px)` 叠反向层，高 8–12px，两端渐隐

### 对称构图规则

居中轴线必须存在且唯一：logo、H1、按钮全压中轴；两栏以上必须等宽镜像；页眉页脚用「中徽标 + 两侧等距链接」门式结构。破例仅限：长文阅读区与图注可左对齐，容器仍居中。

## 五、版式模式（8 个）

1. **圣坛 Hero**：满屏深底 + 居中旭日纹 + Limelight 品牌字 + 上下各一条双层 hairline（间距 8px）+ eyebrow；旭日圆心藏在品牌字后方，半径约为视口宽 70%。
2. **旭日纹 CSS**：`repeating-conic-gradient(from -90deg, gold 0deg 4deg, transparent 4deg 12deg)` 硬色标放射线 + `mask-image: radial-gradient(closest-side, black 30%, transparent 72%)` 由内向外渐隐；透明占 2/3 才轻盈。
3. **建筑立面分栏**：等宽 2–4 栏，栏间 1px hairline，每栏顶部 32px 短金线 + Oswald 标签。
4. **阶梯分割带 (ziggurat divider)**：clip-path 画 3–4 级退台横条（每级 8px 高、缩进 16px），或三个堆叠居中 div 宽 100%→66%→33%。
5. **嵌套线框卡**：内边距 32–40px，双线框，顶部中央嵌菱形饰件；hover 只允许框线亮度 transition 0.3s。
6. **Cassandre 海报区**：超大几何形（船头/塔/乐器剪影，clip-path）占 70% 版面，低视角倾斜 -8°~-12°，配一行小号 Oswald 注释——「巨形 + 微字」尺度对比是 Deco 平面核心语法。
7. **人字纹衬带**：章节标题上下各一条 10px chevron 带，宽 ≤480px 居中，透明度 0.6。
8. **票券/菜单块**：米白纸色块 + 深棕双框 + 两端半圆缺口（径向渐变打孔），条目间点线引导价目（衬线数字右对齐）。

## 六、动效

**允许**：淡入 + 8–16px 位移；hairline 从中轴向两侧生长 (scaleX)；金线 0.6→1 透明度呼吸（周期 ≥4s）；旭日整体旋转 ≤60s/圈；滚动一次性 reveal（0.5–0.7s ease-out）；按钮金线描边 0.3s。
**禁止**：bounce/elastic、粒子礼花、3D 翻转视差、霓虹闪烁、逐字弹跳、每屏超过 1 处无限循环强动效。

## 七、移动端

1. 展示体字号降级不降字距：Limelight ≥40px，letter-spacing ≥0.1em。
2. 立面分栏 <768px 折单栏，但保留 hairline 变水平分隔线，维持「立面」记忆。
3. 旭日纹改用固定 900px 圆形置于 hero 顶部裁切，防摩尔纹。
4. 三线框窄屏减为双线（间距 4px）。
5. 触控目标 ≥48px；金线 hover 态触屏改 active 线亮补偿。

## 八、示范页内容方案

**品牌**：「鎏金狐 THE GILDED FOX」——1925 年传奇爵士俱乐部。Hero：eyebrow "EST. 1925 · PARIS — SHANGHAI"，主标「今夜，回到装饰艺术的黄金年代」，副标 Poiret One "Cocktails · Jazz · Midnight"，旭日纹衬底，双线框 CTA「预订席位」。区块：① 立面三栏（现场爵士 / 鸡尾酒档案 / 午夜舞池）；② ziggurat 分割带；③ Cassandre 海报式「本月主题：萨克斯的低语」+ 巨型萨克斯剪影；④ 演出日历（票券块）；⑤ 人字纹衬带 + 鸡尾酒单（嵌套线框卡 ×3：「翡翠狐」「零点特快」「鎏金 1925」）；⑥ 页脚门式结构 + 翼日轮 + 双层 hairline。

## 九、反模式

廉价化三来源：**金色滥用**（渐变金字满屏、金大面积底色）、**混种**（+蒸汽朋克齿轮/+维多利亚卷草/+婚礼玫瑰金 script/+赛博霓虹）、**质感做作**（bevel/emboss、厚投影、纸张滤镜拉满）。
高级公式：**90% 哑光深底 + ≤10% 金 hairline 与几何饰件 + 严格对称 + 宽字距大写**——金出现在「线的末端」，永远不出现在「面的填充」。

## 十、信息来源

- Wikipedia – International Exhibition of Modern Decorative and Industrial Arts: https://en.wikipedia.org/wiki/International_Exhibition_of_Modern_Decorative_and_Industrial_Arts
- Britannica – Art Deco: https://www.britannica.com/art/Art-Deco
- Mad Paris – 1925-2025 One Hundred Years of Art Deco: https://madparis.fr/1925-2025-One-Hundred-Years-of-Art-Deco
- Swann Galleries – Art Deco at 100: https://www.swanngalleries.com/news/vintage-posters/2025/04/art-deco-at-100-the-1925-paris-exhibition-the-birth-of-art-deco-design
- Qode Interactive – Art Deco and its Use in Design: https://qodeinteractive.com/magazine/art-deco-design
- MDN – repeating-conic-gradient(): https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/repeating-conic-gradient
- FAMSF – Tamara de Lempicka: https://www.famsf.org/learn-engage/read-watch-listen/5-things-to-know-art-deco-tamara-de-lempicka

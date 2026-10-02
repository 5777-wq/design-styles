# 波普艺术研究笔记（Pop Art → 网页 UI）

> 来源：Tate、Don Corgi 配色研究、Mew Design、Awwwards pop-art 案例集、Google Fonts、Lea Verou CSS Patterns 同源做法。

## 一、风格档案

1950s 起于伦敦「独立集团」（ICA 附属）：Paolozzi 1947 年拼贴首用「Pop」意象；Hamilton 1956 年《Just What Is It that Makes Today's Homes So Different, So Appealing?》成为宣言式图标，1957 年给出经典定义——"流行的、瞬时的、廉价的、批量生产的、年轻的、机智性感的、大生意的"。1960s 美国爆发：Warhol 用丝网印刷复制明星与罐头（《Marilyn Diptych》1962、《Campbell's Soup Cans》1962），把"批量生产"本身变成语言；Lichtenstein 放大漫画格（《Whaam!》1963），将本戴点与粗黑描边手工化；Keith Haring 1980s 粗线小人 + 放射线。核心姿态：**挪用大众消费文化与广告美学，模糊高低艺术边界**。

网页可迁移母题：丝网平色块与系统重复（四联画网格）、本戴点/halftone、漫画对话框与拟声词（POW! BANG!）、粗黑描边、高饱和撞色、明星/商品符号居中构图、超市货架/价签陈列感。

## 二、配色（4 套，撞色可互换但每屏 ≤3）

| 方案 | 背景 | 前景/描边 | 撞色 |
|---|---|---|---|
| A 莉琴斯坦因印刷间（默认） | `#FFFDF5` 漫画纸白 | `#111111` | 红 `#E60023` / 黄 `#FFE900` / 蓝 `#002395` |
| B 沃霍尔霓虹工厂 | `#FFF8F0` | `#1A0B2E` | 热粉 `#FF1493` / 电光青 `#00E5FF` / 紫 `#8A2BE2` |
| C 哈林街头 | `#FFFFFF` | `#000000` | 消防红 `#CE1126` / 草绿 `#009E60` / 黄 `#FFD400` |
| D CMYK 印刷厂（可作深色：bg/fg 互换） | `#F7F3E8` 新闻纸 | `#101010` | 过程青 `#00B7EB` / 品红 `#FF0090` / 过程黄 `#FFD700` |

配对法则：撞互补（红配绿、蓝配橙、黄配紫），取色环"右上角"（高饱和高亮度），永不取灰调中间色。

## 三、字体

- **展示体**：`Bangers`（漫画拟声，仅 1 字重，全大写 + letter-spacing 0.02–0.05em）；`Luckiest Guy`（1950s 广告风备选）；`Archivo Black`（中性粗黑，用于 h2/h3，比漫画体耐用）。
- **正文体**：`Archivo`（400/500/700）或 `Source Sans 3`；中文回退 `"Noto Sans SC", "PingFang SC", "Microsoft YaHei"`。
- 引入：`family=Bangers&family=Archivo:wght@400;500;700&family=Archivo+Black`

| 级别 | 规格 |
|---|---|
| display（拟声词/hero） | Bangers，clamp(3rem, 8vw, 7rem)，全大写，+0.04em，可多色描字（text-shadow 4 向 2px 黑描边） |
| h1 | Archivo Black，clamp(2.25rem→3.5rem)，行高 1.1 |
| h2 / h3 | Archivo Black / Archivo 700，1.75rem / 1.25rem |
| body | Archivo 400，16–18px，行高 1.7（中文 1.75），行长 45–75 字符 |
| 微标签/价签 | Archivo 700，0.75rem，全大写，+0.08em |

## 四、圆角 / 描边 / 阴影 / 网点

- 描边：主 3px `#111`；重 4–5px（hero 图、爆炸框）；细 2px（输入框、次级元素）。
- 圆角：全站二选一——硬朗印刷风 0–2px，或圆润漫画风 12–16px + 气泡 999px；不得超过 2 档。
- 硬阴影（blur 恒 0）：卡片 `4px 4px 0 0 #111`；hero/重点 `8px 8px 0 0`；hover `6px 6px` + `translate(-2px,-2px)`；active `translate(4px,4px)` 且阴影归零。
- 本戴点：`radial-gradient(circle, var(--accent) 3px, transparent 3.5px)` + `background-size: 16px 16px`；双层错位成菱形网：`background-position: 0 0, 8px 8px`；hero 阴影层用 4px/20px 渐稀；禁止软边 dot。

## 五、版式模式（7 个）

1. **爆炸 Hero**：中心 starburst（clip-path 或 SVG）包主标语，背景网点由密渐稀；Bangers 大字多色描字；CTA 黄底黑字 3px 描边 + 6px 硬影。
2. **沃霍尔四联格**：2×2 / 3×3 等分格，同一对象换撞色背景重复；gap 16px，格描边 3px；格内文字 ≤2 行。
3. **漫画分镜条**：3 格 panel 错位基线（top 偏移 0 / 24px / 48px），格内编号 #01–#03 + 拟声小标签，形成对角线动势。
4. **气泡推荐墙**：评价容器 border-radius 24px + ::after 旋转 45° 方块做尾巴；气泡底色轮换撞色；头像圆框 3px 描边。
5. **贴纸导航/徽章**：白底 2px 描边 + `8px 8px 0` 硬影的小贴纸，logo 做圆形贴纸，hover 抬起（影 10px）。
6. **超市价签定价区**：价签 = 顶部撞色头条 + tabular-nums 大价格 + `border-top: 2px dashed` 打孔线；背景等距竖线暗示货架。
7. **POW! 跑马灯**：全宽无缝 marquee，撞色底 + Bangers + ★/● 分隔，高 48–64px，20–30s linear infinite。

## 六、动效

**允许**：硬影位移按压（≤150ms）；scale-in「砸落」（1.6→1，200ms）用于拟声词；回弹曲线 `cubic-bezier(0.34,1.56,0.64,1)`；marquee 匀速滚动；`steps()` 步进动画（漫画翻帧感）；hover 撞色互换（瞬时）。
**禁止**：>500ms 淡入淡出、视差滚动、柔和 box-shadow 过渡、morphing blob、玻璃拟态 blur、同屏 >2 个元素同时动。

## 七、移动端

1. 描边降档（4→3px、3→2px）、硬影 6→4px。
2. 爆炸 hero 简化：burst 改矩形+角标，字号 clamp 下限 2.5rem。
3. 四联格塌缩单列或 2 列，单元只留 1 行标题；拟声词减至 1 处、尺寸减半。
4. 触控目标 ≥44px：描边按钮 padding ≥12px 20px；marquee 降到 40px 高。
5. 网点密度减半（background-size 16px→24px）防摩尔纹。

## 八、反模式与适用边界

**变廉价混乱**：高饱和大面积铺正文底色；拟声词/爆炸框到处飞；随机重复无系统；灰调做旧色混入；模糊阴影 + 圆角 + 渐变混入拟物语法；摄影原片直出；细线描边（<2px 失去墨线感）。
**适合**：潮流/街头品牌、饮料零食快消、音乐节与活动页、游戏、创意机构、DTC 新消费。
**不适合**：金融医疗法律等严肃信息站、长文阅读产品、企业级 SaaS 控制台。

## 九、信息来源

- Tate – Pop Art: https://www.tate.org.uk/art/art-terms/p/pop-art
- Don Corgi – 20 Pop Art Color Palettes: https://doncorgi.com/blog/pop-art-color-palettes/
- Mew Design – Pop Art Graphic Design Guide: https://docs.mew.design/blog/pop-art-design-style
- Awwwards – pop-art 网站集: https://www.awwwards.com/websites/pop-art/
- Neubrutalism 权威指南（硬阴影规格参照）: https://neubrutalism.com
- Creative Market – Pop Art Design Trend: https://creativemarket.com/blog/design-trend-report-pop-art-design
- Google Fonts: Bangers / Luckiest Guy / Archivo Black / Archivo

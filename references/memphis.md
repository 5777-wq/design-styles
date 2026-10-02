
# 孟菲斯风格网页设计 (Memphis Design)

## 风格本质

一句话：**「有系统的任意」——固定的形状词汇表高强度重复，黑白压阵，热闹得有语法。**

1981 年 Ettore Sottsass 与 Michele De Lucchi、Nathalie Du Pasquier 等人在米兰创立 Memphis Group，用廉价塑料层压板和「反好品味」印花对抗现代主义的中性功能主义（Carlton 书架、Casablanca 柜、Bacterio 波浪纹），渗透了整个 80 年代流行文化（《Miami Vice》《怪奇物语》式复古美术）。

**适用**：创意市集、音乐节、儿童/青年品牌、独立文创、游戏周边——需要「远距离抓眼球」与情绪能量的场合。
**不适用**：医疗、金融、法律、企业官网、严肃新闻——趣味复古语境错位时会显得俗气 (tacky)。

## 十二条铁律

1. **所有装饰必须来自固定形状词汇表（≤8 种），同一形状至少出现 2 次**——重复产生系统感，这是「有系统的任意」而非随机撒贴纸。
2. **装饰独立成层**：`position:absolute` + `pointer-events:none` + `aria-hidden="true"`——装饰永不参与交互、永不挤压内容。
3. **装饰只出现在指定区域**：页面四角、标题旁、卡片角标、分界带四处——正文行内出现装饰即破坏语法。
4. **每屏装饰实例 ≤6 个，成簇放置**（每簇 3 个形状）——密度集中在「簇」而非均匀散点，才有节奏。
5. **描边统一 3px 纯黑**，形状、卡片、按钮、图标同宽——粗描边是孟菲斯最重要的身份识别。
6. **硬阴影替代模糊阴影**（`6px 6px 0 #111`，无 blur）——模糊投影会立刻稀释风格。
7. **禁止渐变、禁止 tint/shade**——孟菲斯靠纯色并置的「生产性不和谐」，渐变是异质元素。
8. **同屏 3–4 个高饱和色 + 黑白压阵，背景只用白/米白/浅灰**——黑白几何（条纹、波点、Bacterio）是让高饱和色不打架的缓冲层。
9. **倾斜仅限装饰与强调元素（rotate -6°~6°），正文、导航、表单永不倾斜**。
10. **bullet、分隔、标签一律用几何形状**，图标只用扁平几何——写实剪贴画和 emoji 会让孟菲斯瞬间变廉价。
11. **一页只有一个装饰密度峰值（hero），向下逐屏递减**——处处热闹等于没有热闹。
12. **可读性不妥协**：正文一律 `#1A1A1A` on 米白（对比度 ≥12:1），彩色只做底色、描边、大字号 display。

## 设计 Token 速查

**配色 A「米兰 1981」（默认）**：

| token | hex |
|---|---|
| --primary | `#FF6B6B` 珊瑚红 |
| --accent-1/2/3 | 青 `#4ECDC4` / 黄 `#FFD166` / 紫 `#9B5DE5`（点缀） |
| --ink / --bg | `#111111` / `#FAF3E7` 米白 |

备选：B「电光 80s」品红粉 `#FF5D8F` / 蓝绿 `#00C2A8` / 黄 `#FFC53D` / 橙 `#FF8C42` on `#F8F9FA`；C「Du Pasquier 柔和印花」青绿 `#2A9D8F` / 橙沙 `#F4A261` / 芥黄 `#E9C46A` / 柔粉 `#FFB5C2` on `#FDF6EC`（适合儿童与文创）。

**字体**（Google Fonts）：

| 场景 | 字体 | 规格 |
|---|---|---|
| Display | `Righteous`（首选，几何 80s）或 `Shrikhand`（玩闹斜体感）；点缀限 1 词可用 `Monoton` | clamp(44px, 7vw, 88px)，行高 1.05，可 rotate(-2deg) |
| 正文西文 | `Poppins` 400/600/700 或 `Montserrat` | 16–18px，行高 1.7 |
| 中文 | `Noto Sans SC` 400/500/700/900 | 标题 900 压得住几何图形 |

**圆角二值化**：卡片与形状 **0–4px 直角**（硬几何），按钮与 chip **999px 全圆 pill**；禁止 8–16px 中庸圆角。
**描边**：`3px solid #111`；小型元素可 2px。
**阴影**：`6px 6px 0 #111`；hover 按压态 `translate(3px,3px)` + `3px 3px 0`；重点卡片可用彩色硬阴影 `8px 8px 0 var(--primary)`。

**形状词汇表（8 种，CSS 思路）**：

1. 波点阵：`radial-gradient(var(--c) 4px, transparent 4.5px)` + `background-size:24px`
2. 黑白斜条纹：`repeating-linear-gradient(45deg,#111 0 10px,#fff 10px 20px)`
3. 锯齿 zigzag：`clip-path: polygon(...)` 三角齿边
4. Squiggle 蚯蚓线：inline SVG path `M0,10 Q10,0 20,10 T40,10...`，stroke 3px round
5. 闪电：`clip-path: polygon(60% 0, 20% 45%, 45% 45%, 30% 100%, 85% 40%, 55% 40%)`
6. 三角：`clip-path: polygon(50% 0, 0 100%, 100% 100%)`
7. 圆环/半圆：`border-radius:50%` / `999px 999px 0 0`
8. Bacterio 斑点噪纹：多层错位 radial-gradient 小点

## 工作流程

1. **选色板与形状词汇**：确定 3 套配色之一 + 从 8 种形状中选 4–6 种作为本站词汇表（本站内不再引入新形状）。
2. **从模板起步**：复制 `assets/templates/memphis.html`（虚构创意市集「跳线市集」示范页，含装饰簇、跑马灯、贴纸卡、锯齿分屏、票券全套），替换内容。
3. **布置装饰簇**：hero 密度峰值 → 分界带 → 卡片角标，密度递减；全程遵守四区域规则。
4. **过自检清单**。

## 自检清单

- [ ] 装饰全部来自固定词汇表，同一形状至少出现 2 次
- [ ] 装饰层 absolute + pointer-events:none + aria-hidden，不挤压内容
- [ ] 装饰只出现在四角/标题旁/卡片角标/分界带；每屏 ≤6 个成簇放置
- [ ] 全部描边 3px 黑、全部阴影 6px 6px 0（无 blur）、无渐变
- [ ] 同屏 3–4 个高饱和色，背景是白/米白/浅灰
- [ ] 只有装饰与 display 倾斜（-6°~6°），正文导航表单端正
- [ ] bullet/分隔/标签是几何形状，没有 emoji 和写实剪贴画
- [ ] 正文 #1A1A1A on 米白，没有彩色小字
- [ ] 移动端装饰减半、overflow-x:hidden、阴影 4px、触控目标 ≥44px

## References 索引

- `references/notes/memphis.md` — 完整研究笔记：Memphis Group 史、3 套配色、形状词汇表 CSS、6 个版式模式、动效清单、反模式、信息来源
- `assets/templates/memphis.html` — 零构建示范页（虚构创意市集「跳线市集 JUMPER FAIR」），浏览器直接打开

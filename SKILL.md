---
name: design-styles
description: 网页设计风格选择器与设计语言合集——内置 13 套风格鲜明、可落地的完整设计系统：瑞士国际主义 (swiss)、日式侘寂 (japandi)、Anthropic/Claude 纸感编辑部 (anthropic)、装饰艺术 (art-deco)、风格派 (de-stijl)、包豪斯 (bauhaus)、构成主义 (constructivism)、中古现代 (mid-century)、玻璃拟态 (glassmorphism)、孟菲斯 (memphis)、波普艺术 (pop-art)、新粗野主义 (neubrutalism)、迷幻海报 (psychedelic)。当用户要求做任何网页/官网/落地页/作品集/活动页/UI 界面设计时触发——即使用户没有点名风格；当用户提到「瑞士风格」「日式/侘寂」「像 Claude/Anthropic 官网」「纸感」「编辑部风」「Art Deco」「蒙德里安/风格派」「包豪斯」「构成主义」「中古/复古 50 年代」「玻璃拟态/毛玻璃」「孟菲斯」「波普」「粗野主义」「迷幻」等任何风格词时也触发。用户未指定风格时，必须先展示风格菜单让用户选择。
---

# 网页设计风格合集 (Design Styles)

一套可选择的网页设计语言库。每套风格包含：12 条铁律、完整设计 token（配色/字体/字阶/圆角/阴影）、版式模式、自检清单，以及一个可直接打开的零构建示范模板。

## 工作流程

### 第一步：定风格（最重要）

**用户没有点名风格时，必须先用 AskUserQuestion 展示风格菜单让用户选择**，不要擅自决定。菜单按用户的项目类型给推荐（推荐项放第一个选项并标注「推荐」）：

| 风格 | 气质一句话 | 典型场景 |
|---|---|---|
| **swiss 瑞士国际主义** | 网格、无衬线、左对齐、冷静高级 | 品牌官网、SaaS、作品集、年报 |
| **japandi 日式侘寂** | 极端留白、明朝体、自然肌理的慢 | 茶/酒/旅馆/匠人品牌、文化机构 |
| **anthropic 纸感编辑部** | 暖纸底、衬线叙事、墨色 10% hairline、clay 点缀 | AI 产品、研究机构、写作工具、出版物 |
| **art-deco 装饰艺术** | 对称的几何奢华：深底、金线、阶梯与旭日纹 | 奢华酒店、爵士酒吧、珠宝、电影院 |
| **de-stijl 风格派** | 贯通黑线 + 三原色格子的最小视觉语法 | 美术馆、基金会、家具与建筑品牌 |
| **bauhaus 包豪斯** | 几何三原色构成，图形即主角 | 设计院校、美术馆、文化机构 |
| **constructivism 构成主义** | 红黑米白的对角动员令：楔形与口号 | 影展、出版市集、文化节、倡议活动 |
| **mid-century 中古现代** | 原子时代的暖色符号学：blob、星芒、回旋镖 | 咖啡馆、唱片行、复古品牌、创意机构 |
| **glassmorphism 玻璃拟态** | 磨砂半透明 + 彩色光斑景深 | 音乐、天气、钱包等情绪化产品 |
| **memphis 孟菲斯** | 80 年代形状词汇表派对，热闹有语法 | 创意市集、青年品牌、活动页 |
| **pop-art 波普艺术** | 粗黑描边、高饱和撞色、漫画拟声词 | 潮牌、饮料零食、音乐节、游戏 |
| **neubrutalism 新粗野主义** | 硬边框 + 硬阴影的贴纸朋克 | 开发者工具、创意工具、D2C |
| **psychedelic 迷幻海报** | 丝网平涂的振动与流动，信息层永远干净 | 音乐节、唱片店、艺术展、快闪 |

**用户已点名风格（如「用波普风格」）时跳过菜单，直接路由。**

### 第二步：读风格规范

读 `references/<风格名>.md`——里面有该风格的本质、12 条铁律、完整 token、工作流程与自检清单。需要学理依据、更多版式模式或信息来源时，读 `references/notes/<风格名>.md`（瑞士风格的深入材料拆成 5 份：swiss-principles / swiss-typography / swiss-grid-layout / swiss-color-motion / swiss-patterns）。

### 第三步：从模板起步

复制 `assets/templates/<风格名>.html` 作为起点（零构建单文件，浏览器直接打开即是完整风格示范）。替换内容与文案，按规范调整 token。多页项目把 CSS 抽成共享文件，保持 token 一致。

### 第四步：自检交付

按所选风格规范末尾的自检清单逐条核对。通用底线（所有风格共享）：

- 正文对比度 ≥ WCAG 4.5:1；触控目标 ≥44px
- 展示字体经 Google Fonts 引入 + 系统回退栈，离线不塌
- 动效尊重 `prefers-reduced-motion`
- 移动端：网格塌缩保留层级与风格载体（描边/细线/编号/形状等身份元素不删）

## 风格速查：气质极点分布

```
冷静 ◀────────────────────────────────────────────▶ 热闹
  japandi  swiss  de-stijl  art-deco  bauhaus  mid-century  glassmorphism  memphis  pop-art
                                             constructivism(动员感)   psychedelic
叛逆 ◀────────────────────────────────────────────▶ 秩序
  psychedelic  pop-art  neubrutalism  memphis  constructivism  mid-century  bauhaus  de-stijl  art-deco  swiss  japandi
```

- 用户说「极简高级」「性冷淡」「气质」→ swiss 或 japandi（冷静 vs 温暖）
- 用户说「像 Claude/Anthropic 官网」「纸感」「书卷气」「编辑部」→ anthropic
- 用户说「奢华」「酒店」「爵士年代」「盖茨比」→ art-deco
- 用户说「蒙德里安」「格子」「秩序感」→ de-stijl（有圆三角图形则 → bauhaus）
- 用户说「构成主义」「苏联海报」「斜线」「影展」「出版市集」→ constructivism
- 用户说「复古」「50 年代」「唱片行」「咖啡馆」「原子时代」→ mid-century
- 用户说「热闹」「年轻」「抓眼球」→ pop-art 或 memphis（漫画 vs 形状派对）
- 用户说「有态度」「反主流」「开发者」→ neubrutalism
- 用户说「通透」「材质感」「苹果风」→ glassmorphism
- 用户说「迷幻」「摇滚」「嗡嗡振动」「嬉皮」→ psychedelic
- 用户说「几何」「构成」「艺术感」→ bauhaus

## 如何新增一套风格

1. 在 `references/` 加 `<风格名>.md`（按现有格式的结构：本质/铁律/token/工作流/自检）；
2. 在 `references/notes/` 加研究笔记（含信息来源）；
3. 在 `assets/templates/` 加 `<风格名>.html` 示范页；
4. 更新本文件的菜单表与气质分布图。

## 文件结构

```
design-styles/
├── SKILL.md                  ← 本文件（菜单 + 路由）
├── references/
│   ├── swiss.md … anthropic.md   （13 份风格规范，选型后必读对应一份）
│   └── notes/                    （研究笔记：学理、案例、来源）
└── assets/templates/
    ├── swiss.html … anthropic.html （13 个零构建示范模板）
```

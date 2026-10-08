# Anthropic / Claude 官网拆解研究笔记（纸感编辑部 → 网页 UI）

> 来源：2026-10 对 www.anthropic.com 与 claude.com/product/overview 的实机渲染拆解（Chrome 1440×900，从页面 CSS 变量中直接提取 290 个 token 中的核心部分），非转述资料。

## 一、总体判断

Anthropic/Claude 的官网品味来自一套极度自律的「纸上编辑部」系统：暖纸底代替纯白、衬线做叙事、无衬线做界面、边框是墨色的透明度、全站只有 ivory 灰阶 + slate 墨阶 + 一个 clay 橙。它证明了「克制的堆叠」本身就是风格——没有任何一个新发明，但每一个决定都朝同一个方向。

## 二、实测设计 Token

### 背景系统：象牙白三阶

| Token | 值 | 用途 |
|---|---|---|
| --ivory-light | `#FAF9F5` | 页面底 |
| --ivory-medium | `#F0EEE6` | 卡片底、次级区块 |
| --ivory-dark | `#E3DACC` | 卡片 hover、更深分层 |

### 墨色系统：板岩四阶

| Token | 值 | 用途 |
|---|---|---|
| --slate-dark | `#141413` | 正文近黑（非纯黑） |
| --slate-medium | `#3D3D3A` | 按钮 hover |
| --slate-light | `#5E5D59` | 链接、次级文字 |
| gray-500 档 | `#878683` 级 | 弱化注记 |

### 边框 = 墨色的透明度（关键发明）

```
--border:       #1414131A   /* 墨色 10% */
--border-hover: #14141333   /* 墨色 20% */
```
边框不是另一种颜色——hover 是「墨变浓」而不是「换色」。整站永远不会有突兀的灰线。

### clay 橙家族（唯一强调色）

`--clay: #D97757`（Claude 品牌橙）/ hover `#C6613F` / dark `#C46849`。用于星芒 logo、链接、插画面板；不用于大面积。

### 粉彩插画面板色

牛皮纸 `#E8E6DC`、蜜桃 `#EBC9B7`、淡紫 `#CBCADB`、鼠尾草 `#BCD1CA`——平色块 + 单色墨线手绘，从不混风格。

## 三、字体系统（三族分工）

| 族 | 官方字体 | 分工 | 实测样例 |
|---|---|---|---|
| Serif | Anthropic Serif（Georgia 回退） | 叙事与展示：正文、巨型标题 | anthropic.com H2：96px / weight 400 / lh 1.16 / 字距 -1.44px；正文 24px / 1.40 |
| Sans | Anthropic Sans（Arial 回退） | UI：导航、H1、按钮 | anthropic.com H1：约 61px / 700 / lh 1.10 |
| Mono | Anthropic Mono | 档案标签：DATE / CATEGORY 类注记 | 大写小字 + hairline 行 |

**最反常识的决定：正文用衬线，界面用无衬线**（多数科技公司相反）。claude.com 的 H1 也是衬线（72px / 500 / 1.10）。按钮文字用衬线 400（公司官网）——控件也带书卷气。

- 字号阶梯：0.875 / 1 / 1.125 / 1.25 / 1.5rem（detail→display-s），展示级 52 / 72 / 96px
- 存在非整数字重 480——可变字体精细调校
- **行宽用 ch 制**：`--text-width-prose: 80ch`、body 60ch、headline 30ch、title 45ch、narrow 20ch

## 四、间距与形状

- 间距 9 档全是 4 的倍数：`--space--1..9` = 4/8/12/16/24/32/40/48/64px
- 页边距 `clamp(2rem, 1.08rem + 3.92vw, 5rem)`
- 圆角 4 档：small 4px / main 8px / large 16px / round 100vw（胶囊）
- 分层靠底色深浅（ivory 三阶），几乎不用 box-shadow

## 五、布局语法与细节

1. **hero 宣言右偏置**：首屏左侧整片空白，一句衬线宣言放右侧约 60% 处——不对称但安静。
2. **档案感卡片**：announcement 卡 = ivory-medium 底 + 大圆角（16px）+ 衬线标题 + 底部 mono 大写小标签表（DATE / CATEGORY / DETAILS）+ hairline 分行 + 黑色 pill「Read announcement →」。
3. **导航滚动收缩**：滚下后 wordmark 缩为字标 monogram。
4. **黑色 pill 按钮 + 箭头**：全站唯一高对比元素，每次出现都有分量；主按钮 = gray-950 近黑 + ivory 文字。
5. **滚动时间轴叙事**：claude.com 产品页用 8AM / 12PM / 4PM 刻度轴带动场景切换；场景配「Modify prompt / Replay」白色 pill。
6. **粉色 pastel 插画**：平色块 + 墨线，出现在时间轴场景与新闻卡缩略图（clay 底白色线稿「网络头」）。
7. **微动效**：内容淡入上移，无弹跳无发光；新闻卡是白底浮层 + 轻阴影（全站少数阴影，用于真浮层）。

## 六、可抄的十条规则（skill 铁律的原型）

1. 页面底 `#FAF9F5`，不用纯白。
2. 正文与展示标题用衬线，导航与控件用无衬线。
3. 边框 = 墨色 10% alpha，hover 20%——不是换色，是墨变浓。
4. 全站强调色只有一个 clay `#D97757`，只用于点缀。
5. 巨型衬线标题敢用 weight 400（96px / -1.44px 字距）。
6. 分层靠 ivory 三阶底色，不靠阴影。
7. 4px 间距阶梯，9 档用到底。
8. 行宽按字符数（ch）定，中文段落按 em。
9. 档案感细节：mono 大写小标签 + hairline 行 + 右对齐值。
10. 黑色 pill 按钮是唯一的高对比元素，省着用。

## 七、免费替代字体

Anthropic Sans/Serif/Mono 是定制商用字体。近似替代：**衬线 → Newsreader**（opsz 轴，96px 大标题效果接近 Tiempos 气质；备选 Source Serif 4、Lora）；**Sans → Instrument Sans**（grotesque 微暖；备选 Inter）；**Mono → IBM Plex Mono**。中文：衬线 Noto Serif SC、无衬线 Noto Sans SC。

## 八、对照截取样本

- anthropic.com 首屏：暖米白底、右偏置衬线宣言、黑 pill「Try Claude」
- anthropic.com「Latest releases」：三张 ivory-medium 卡 + DATE/CATEGORY/DETAILS mono 行
- claude.com/product/overview：星芒 logo + 衬线 Claude 字标、时间轴滚动叙事、pastel 插画面板、Modify prompt/Replay 白 pill

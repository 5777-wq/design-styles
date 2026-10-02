# 瑞士风格的网页字体与排印规范

> 来源：Inter 官方（rsms.me）、Monotype、Adobe Fonts、Typewolf、Fontsource/jsDelivr 实测、Tailwind 字距标尺、Utopia clamp 公式、MDN、W3C《中文排版需求》(clreq)。

## 一、Helvetica 家族的网页现状

- **Helvetica 本体**：版权归 Monotype，桌面授权不覆盖 `@font-face` 网页嵌入；网上的"免费 Helvetica webfont"基本是未授权克隆，商用有法律风险。Google Fonts 与 Adobe Fonts 均无 Helvetica 本体。
- **Neue Haas Grotesk（NHG）**：Christian Schwartz 对 1957 年原版的数字修复，被认为是最"正宗"的 Helvetica。包含在 Adobe Fonts 库中，Creative Cloud 订阅用户可通过 "Web Projects" 合法用于网站——这是获得"真 Helvetica"性价比最高的路径。
- **Helvetica Now**：Monotype 2019 年重绘版，按光学尺寸分 Micro / Text / Display 三档，走 Monotype 订阅或 MyFonts 单买。

结论：血统之选是 NHG（有 CC 订阅则零成本）；预算项目用免费替代。

## 二、免费替代字体评估（瑞士气质 = 中性、几何、grotesque 血统）

| 字体 | 气质 | 可变轴 | 评价 |
|---|---|---|---|
| **Inter** (OFL) | 几何 neo-grotesque，与 Helvetica Neue 神似度最高的屏幕字体 | wght 100–900 + opsz + 真斜体 | 全能首选；opsz 轴自动完成正文/标题光学切换；特性极全（tnum、zero、ss01–08） |
| **Archivo** (OFL) | 源自新闻纸排印的 grotesque，比 Helvetica 更硬更紧凑 | wght 100–900 + wdth 62–125 | 标题冲击力强，适合大字 display；正文略挤 |
| **Instrument Sans** (OFL) | 明确的 Helvetica 系复古气质 | wght 400–700 + wdth 75–100 | Google Fonts 上最"像 Helvetica"的新字体，但无 opsz、字重上限 700 |
| Roboto | 中性合格 | wght 100–900 | "安卓感"稀释瑞士气质 |
| IBM Plex Sans | 人文主义修饰 | 100–700 | 中性度不足；有官方 Plex Sans SC 可配中文 |
| Space Grotesk | 切口式细节太抢戏 | 300–700 | **不中性**，只可点缀标题，不作正文 |

**推荐组合**：Inter（正文全能首选）→ Archivo（display 标题）→ Instrument Sans（要最接近 Helvetica 外形时）。

引入方式三选一：

```html
<!-- Google Fonts -->
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,100..900&display=swap">
<!-- Fontsource 自托管 (npm i @fontsource-variable/inter) -->
<!-- 官方 CDN -->
<link rel="stylesheet" href="https://rsms.me/inter/inter.css">
```

## 三、系统字体栈与中文搭配

```css
font-family: "Helvetica Neue", Helvetica, Arial,
  "PingFang SC", "Hiragino Sans GB",
  "Noto Sans SC", "Source Han Sans SC", "Microsoft YaHei", sans-serif;
```

原则：西文永远在前（拉丁与数字由 Helvetica/Inter 渲染），中文按平台降序（macOS 苹方 → Windows 雅黑 → Android/Noto）。要跨平台一致，把 webfont 化的 Noto Sans SC 提到苹方之前。

## 四、排印细节规则

- **字号层级**：瑞士风大标题在网页上通常做到视口的 6–11vw。响应式用 Utopia 式 clamp 三段式：`clamp(最小值, 截距 + 斜率×vw, 最大值)`，斜率 = (max−min)/(视口max−视口min)×100。正文最小：拉丁 16px；中文正文建议 ≥15px、绝对下限 12px。
- **字距**：大标题负字距 **-0.02em 至 -0.03em**（字号越大取越负）；全大写小标签正字距 **+0.05em 至 +0.1em**（常用 0.08em）。正文一律 0，**正文禁止负字距**。
- **行高**：display/h1 1.02–1.1；h2 1.15；h3 1.25；拉丁正文 1.5–1.6；含中文正文 1.7–1.8；大写标签 1.2。
- **字重**：古典瑞士只用 400 + 700（原版 Helvetica 仅两字重）；现代实践允许 500/600 作 UI 中间档，**全站不超过 3 个字重**。
- **对齐与行宽**：一律左对齐 ragged right。纯拉丁正文 `max-width: 60–70ch`（理想 66ch，Josh Comeau 建议用 rem 而非 ch，因 ch 随字号漂移）；含中文段落每行 32–40 字 ≈ `max-width: 38em`。标题断行 `text-wrap: balance`，正文 `text-wrap: pretty`。

## 五、排印 Scale（基准 360–1240px 视口，1rem=16px）

| 级别 | font-size（clamp） | line-height | letter-spacing | weight |
|---|---|---|---|---|
| display | `clamp(3rem, 1.977rem + 4.55vw, 5.5rem)`（48→88px） | 1.05 | -0.03em | 700 |
| h1 | `clamp(2.25rem, 1.739rem + 2.27vw, 3.5rem)`（36→56px） | 1.1 | -0.025em | 700 |
| h2 | `clamp(1.75rem, 1.443rem + 1.36vw, 2.5rem)`（28→40px） | 1.15 | -0.015em | 600 |
| h3 | `clamp(1.25rem, 1.148rem + 0.45vw, 1.5rem)`（20→24px） | 1.25 | 0 | 600 |
| body | `clamp(1rem, 0.949rem + 0.23vw, 1.125rem)`（16→18px） | 1.6（含中文 1.75） | 0 | 400 |
| caption | 0.8125rem（13px） | 1.5 | 0 | 400 |
| micro-label | `clamp(0.6875rem, 0.676rem + 0.05vw, 0.75rem)`（11→12px） | 1.2 | +0.08em，全大写 | 500 |

hero 级标题可再上探：`font-size: clamp(48px, 9vw, 160px); line-height: 0.95–1.05`。

## 六、数字排版

数据表格、价格、统计数字一律 `font-variant-numeric: tabular-nums`（等宽数字，纵向对齐）；序列号/编号可再加 `slashed-zero`。全浏览器 Baseline 可用，但**前提是字体提供该特性**——Inter 原生支持；Helvetica 系统字体部分支持，回退写法 `font-feature-settings: "tnum" 1`。正文叙述文本保持默认比例数字。

## 七、中西文混排 5 规则

1. **栈序定权**：西文字体永远写在中文前面，保证拉丁与数字由 Helvetica/Inter 渲染，中文回落苹方/思源——自动形成"西文清秀、中文饱满"的正确对比。
2. **中西间距 ≤ 0.25 汉字宽**（W3C clreq）：浏览器默认空隙即可，不手动塞空格，也不用负字距压缩。
3. **负字距只给拉丁**：-0.02~-0.03em 作用于汉字会造成笔画粘连；混排标题负字距减半到 -0.01em 以上，或对中文片段 `letter-spacing: 0`。中文任何场景不用负字距。
4. **中文行高加大、禁用斜体**：含中文正文 line-height 1.7–1.8；中文没有真 italic，强调一律用字重或颜色；全局设 `font-synthesis: none` 防止浏览器伪造斜体/字重。
5. **中文字重收敛在 400/500/700**：微软雅黑只有 400/700，中间字重会被合成假粗体；跨平台一致的做法是加载 Noto Sans SC 可变字重对齐 Inter；中文字重一般不高于西文同级。

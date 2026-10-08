# Anthropic / Claude 风格网页设计 (纸感编辑部)

## 风格本质

一句话：**暖纸底上的衬线编辑部——边框是墨色的透明度，全站只有灰阶加一个 clay 橙，靠克制本身建立品味。**

源自 Anthropic/Claude 官网的实测设计系统（token 全部从渲染页面提取，见 notes）。它不是历史风格，而是当代「calm tech」的最高水准样本：象牙白三阶分层、衬线叙事 + 无衬线界面、档案感 mono 标签、几乎零阴影。

**适用**：AI 产品、研究机构、写作/阅读工具、出版物、咨询与研究团队——任何想传达「严谨且有文化」的品牌。
**不适用**：需要强情绪冲击的活动页（→ pop-art/psychedelic）、儿童品牌、游戏。

## 十二条铁律

1. **页面底 `#FAF9F5`，永不用纯白**——暖纸底是整份书卷气的地基。
2. **正文与展示标题用衬线，导航与控件用无衬线**——编辑部反转：衬线管叙事，Sans 管界面。
3. **边框 = 墨色 10% alpha，hover 20%**——不是换色，是墨变浓；全站不允许出现别的线色。
4. **全站强调色只有一个 clay `#D97757`**，只用于点缀（logo 符号、链接、插画面板），占屏 <5%。
5. **巨型衬线标题敢用 weight 400**（展示级 96px / 字距 -1.44px）——衬线的优雅在细，不在粗。
6. **分层靠 ivory 三阶底色（#FAF9F5/#F0EEE6/#E3DACC），不靠阴影**——阴影只留给真正的浮层。
7. **间距只用 4px 阶梯的 9 档**（4/8/12/16/24/32/40/48/64）。
8. **行宽按字符数定**：拉丁 prose 80ch / 标题 30ch；中文段落 32–40 字（约 36em）。
9. **档案感细节**：mono 大写小标签 + hairline 分行 + 右对齐值——数据行像规格表。
10. **黑色 pill 按钮是唯一的高对比元素**（near-black 底 + ivory 字 + 箭头），省着用。
11. **圆角只有 4/8/16px 与全圆胶囊四档**。
12. **微动效只有淡入上移**（≤300ms）；无边框色过渡、无弹跳、无发光。

## 设计 Token 速查

```css
:root {
  /* 象牙白三阶（背景系统） */
  --ivory-light:  #FAF9F5;
  --ivory-medium: #F0EEE6;
  --ivory-dark:   #E3DACC;
  /* 板岩墨四阶（文字与按钮） */
  --ink:        #141413;
  --ink-medium: #3D3D3A;
  --ink-light:  #5E5D59;
  /* 边框 = 墨色透明度 */
  --border:       rgba(20, 20, 19, 0.10);
  --border-hover: rgba(20, 20, 19, 0.20);
  /* clay 橙（唯一强调色） */
  --clay:       #D97757;
  --clay-hover: #C6613F;
  /* 粉彩插画面板 */
  --kraft: #E8E6DC;  --peach: #EBC9B7;
  --lavender: #CBCADB;  --sage: #BCD1CA;
}
```

**字体**（免费近似替代；官方 Anthropic 字体为商用定制）：
衬线 **Newsreader**（opsz 轴，display 效果最接近；备选 Source Serif 4）；Sans **Instrument Sans**（备选 Inter）；Mono **IBM Plex Mono**；中文衬线 **Noto Serif SC**、无衬线 **Noto Sans SC**。
引入：`family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;1,6..72,400&family=Instrument+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&family=Noto+Serif+SC:wght@400;500;700&family=Noto+Sans+SC:wght@400;500`

**字阶**：display 衬线 clamp(2.75rem, 6vw, 6rem) / 400–500 / lh 1.1 / 字距 -0.01em；statement 衬线 clamp(1.75rem, 3.5vw, 3.5rem)；正文衬线 17–18px / 1.7（中文）；导航/控件 Sans 15–16px；mono 标签 11–12px 大写 +0.08em。

## 工作流程

1. **确认气质**：品牌需要「严谨且有文化」才用本风格；要冲击力选别的。
2. **从模板起步**：复制 `assets/templates/anthropic.html`（虚构写作工具「页边 MARGIN」示范页），替换内容。
3. **组装语法**：右偏置衬线宣言 hero → 档案感卡片（mono 规格行）→ 时间轴叙事 + 粉彩插画面板 → 衬线宣言带 → 规格表 → 门式页脚。
4. **过自检清单**。

## 自检清单

- [ ] 页面底是 #FAF9F5 不是纯白；分层用 ivory 三阶，没有 box-shadow（浮层除外）
- [ ] 正文与标题衬线、导航控件无衬线；全站 ≤3 字族（衬线/无衬线/等宽）
- [ ] 所有边框是墨色 10% alpha，hover 20%；没有第二种线色
- [ ] clay 只出现在点缀处（<5%）；没有第二个强调色
- [ ] 展示标题 weight ≤500 且字号 ≥48px；没有粗黑大标题
- [ ] 间距全是 4 的倍数；行宽按 ch/em 限定
- [ ] 数据行用 mono 大写标签 + hairline + 右对齐值
- [ ] 黑色 pill 按钮每屏 ≤1 个；圆角只用 4/8/16px 与胶囊
- [ ] 动效只有淡入上移（≤300ms）；无边框色动画
- [ ] 插画（如有）是粉彩平色块 + 单色墨线，不混风格

## 深入阅读与模板

- `references/notes/anthropic.md` — 完整拆解笔记：anthropic.com 与 claude.com 实测 token、字体系统分工、布局语法、免费替代方案
- `assets/templates/anthropic.html` — 零构建示范页（写作工具「页边 MARGIN」），浏览器直接打开

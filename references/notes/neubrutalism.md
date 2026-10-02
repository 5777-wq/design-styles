# 新粗野主义研究笔记（Neubrutalism → 网页 UI）

> 来源：NN/g、neubrutalism.com、neobrutalism.dev、onething.design、Lagomorph 规则集、designmd.app、Gumroad Component Library、efeele.dev。

## 一、谱系与分界

**建筑源头**：1950s 粗野主义建筑，法语 béton brut（裸露混凝土），Le Corbusier 等人把结构材料直接暴露为立面。

**Web Brutalism（约 2014–2016）**：反模板化精致设计的「反设计」运动——原始 HTML、系统默认字体、蓝色下划线链接、以丑为意识形态。命名时刻常归于 2015 年 12 月彭博对 Balenciaga「未设计」官网的专题报道；brutalistwebsites.com 策展人 Pascal Devigne："It's about brutal honesty, not brutalism"。Hacker News、Craigslist、Drudge Report 是「天然粗野」活化石。

**Neubrutalism（2021–2024 主流化）**：2021 年 Gumroad 改版是公认转折点——粗黑描边、纯色块、「像把矩形往东南拖了两像素」的硬偏移阴影；随后 Figma 社区涌现数十个 UI kit；neobrutalism.dev（shadcn/ui + Tailwind，5.6k stars）将其工程化。定性：**"心情很好的朋克摇滚"**。

**分界线**：web brutalism 是失控的原始 HTML，无可用性承诺；neubrutalism 是**精心设计过的「故意粗糙」**——保留清晰的层级、留白、无障碍与交互反馈。案例：Gumroad、Tony's Chocolonely、Dodonut、Panda CSS；Figma 为警示案例（2021–22 采用后 2024 放弃）。

## 二、配色（3 套）

| 角色 | A 经典黄 | B 橙紫撞色 | C 柠檬天蓝 |
|---|---|---|---|
| 背景 | `#FFFDF5` | `#F5F0E6` | `#FDF6E3` |
| 主色（CTA/强调块） | `#FFD23F` | `#FF6900` | `#FFD803` |
| 撞色 accent | `#FF6B6B` | `#B8B8FF` | `#74B9FF` |
| 备选池 | `#88D498` 绿 / `#FFA552` 橙 / `#B8A9FA` 薰衣草（三套通用） | 同左 | 同左 |
| 描边/阴影/正文 | `#000000` | `#000000` | `#000000` |

阴影色恒为纯黑；进阶变体允许「彩色阴影」（阴影色=卡片填充色），一套页面内二选一，不得混用。

## 三、字体

- Display：`Archivo Black`（400）、备选 `Syne` 700–800、`Bebas Neue`
- Heading：`Space Grotesk`（500–700）
- Body：`Inter` 或 `DM Sans`（400/500）
- Mono 点缀：`Space Mono` 或 `IBM Plex Mono`（400/700）
- 标准配对：Archivo Black（大写展示标题）+ Space Grotesk（小标题）+ Inter（正文）+ Space Mono（标签/代码/价格）

**描边宽度体系**：2px（表内格线、次级分隔）→ 3px（按钮/卡片/输入框，标准）→ 4px（区块分隔、hero、面板外框）。颜色恒 `#000`。

**硬阴影体系（blur=0，方向恒右下）**：sm `3px 3px`（badge/chip）→ md `5px 5px`（按钮/卡片/面板）→ lg `8px 8px`（hover/浮层）→ xl `12px 12px`（hero/对话框）。

**圆角策略**：默认全 0；或全站统一 12–24px 大圆角（边框与阴影同步跟随），禁止混用。

## 四、版式模式（8 个）

1. **硬边框卡片阵列**：白底或饱和纯色底，3px 边框 + md 阴影，gap 16–24px，padding 24px；hover：translate(-2px,-2px) + 阴影升至 lg，120–150ms。
2. **物理按钮系统**：主钮主色底黑字，3px 边框 + md 阴影，padding 12px 24px，700 字重；hover translate(-2px,-2px)+阴影 7px 7px；**active translate(3px,3px)+shadow:none**（位移=阴影 offset，完全「按灭」）；focus-visible：3px outline（`#74B9FF`）offset 3px。
3. **贴纸 badge**：2px 边框 + sm 阴影，Space Mono 大写，可整体 rotate(-3°–3°)，用于 "NEW/10K STARS" 类贴纸。
4. **加粗分割与双线框**：区块间 4px 实线；强调面板用 border+outline 同向错开 4px 形成双线。
5. **暴露表格**：单元格全部 2px 黑边框，无斑马纹，表头主色纯色底；价格表中间档垫黄色 + 旋转贴纸。
6. **海报式 hero**：米白底上撞色几何色块（零渐变），展示字体大写 clamp(3rem, 8vw, 7rem)，允许元素轻微重叠与不对称错位；等宽 kicker 置顶。
7. **等宽标签系统**：所有 kicker/label/meta 用 Space Mono 大写、0.05em、14–16px，充当「打字机注记」。
8. **终端/代码面板**：黑底等宽亮字（如 `#88D498` 绿），4px 边框 + xl 阴影。

## 五、动效

**允许**：transform 位移 + 阴影 offset 同步增减（100–150ms，linear 或 steps）；按压消阴影；badge 一次性 steps() 弹跳；粗描边 focus outline。
**禁止**：blur/模糊阴影、渐变与颜色过渡、长弹性缓动（>300ms）、视差、大面积 opacity 淡入、glow。`prefers-reduced-motion` 时降级为仅阴影变化。

## 六、移动端

1. 阴影减半（md→3px，lg→4px）避免视觉错位与拥挤。
2. 描边不减（保 2–3px），卡片阵列降为单列。
3. 大标题 clamp 收敛、不超 2 行。
4. 高饱和底仅限小组件，正文区保持米白底。
5. hover 交互必须有 :active 等价物（触摸无 hover），触控目标 ≥44px。

## 七、适用与反模式

**适合**：独立开发者产品、创意工具、D2C 潮流品牌、活动/战役页、portfolio、开发者与 Web3 工具。
**不适合**：金融/保险/医疗（信任感）、企业级数据仪表盘、长文阅读产品、奢侈品牌。
**反模式**：阴影带模糊、渐变、1px 细描边、5 个以上撞色、正文放高饱和底、只做 hover 不做按压态、无目的追赶潮流（Figma 弃用是前车之鉴）。

## 八、与瑞士风格的对立点（同 skill 族的边界）

瑞士是「无线、留白、hairline 分隔的秩序」；neubrutalism 是「有线、硬影、色块的物理秩序」。两者共享的只有网格纪律（8px 对齐）与无障碍底线。

## 九、信息来源

- NN/g – Neobrutalism: Definition and Best Practices: https://www.nngroup.com/articles/neobrutalism/
- Neubrutalism — The Definitive Guide: https://neubrutalism.com
- neobrutalism.dev 组件库: https://www.neobrutalism.dev
- onething.design – What is Neo-Brutalism UI Design: https://www.onething.design/post/what-is-neo-brutalism-ui-design
- Lagomorph – Neubrutalism: A Consideration, and Ruleset (2022): https://lagomor.ph/2022/08/neubrutalism-a-consideration-and-ruleset
- designmd.app 风格档案: https://designmd.app/library/neubrutalism
- Gumroad Component Library (Figma): https://www.figma.com/community/file/1350960002277170570
- efeele.dev – Neubrutalism web design: https://efeele.dev/en/blog/posts/neubrutalism-web-design

---
name: riso-style
description: 生成 Anthropic 暖色调 + Risograph 复古印刷风格的插图。统一限色调色板(奶白底/陶土橙/雾蓝/苔绿/墨炭),手绘线条 + 套色错位 + 纸纹质感,适合教学网页插图、PPT 配图、文章封面、品牌物料。当用户提到 "Anthropic 风格图"、"Risograph"、"riso 风格"、"复古印刷风"、"暖色调插画"、"系列插图"、"故事分镜"、"教学配图"、"独立杂志风" 时使用。本 skill 只提供经过验证的 prompt 风格模板,具体生图模型由使用者自行接入。
---

# Riso Style · 暖色调 Risograph 插图 Prompt 模板

## 用途

一套经过验证的 **Risograph 风格 prompt 模板**,产出**风格高度一致**的系列插图。

> ⚠️ **本 skill 只负责"风格"——即 prompt 模板与调色板规范,不绑定任何生图后端。**
> 你需要自行接入一个文生图模型(任意支持文本 prompt 的图像生成 API / MCP / 本地模型均可),
> 把下文拼好的 prompt 喂进去即可。模型选择、API key、计费、下载/保存逻辑全部由使用者处理。
> 模板在 Doubao Seedance、即梦、Midjourney、SDXL 等模型上均验证过可用,核心是**限色 + 质感关键词**。

典型场景:
- 教学网页 / 知识科普文章 — 概念可视化
- PPT 章节封面、轮播图
- 故事分镜 / 漫画式叙事(每幕一图)
- 品牌物料、Bot 头像系列
- 文档配图(替代单调截图)

## 风格定义

### Anthropic 5 色调色板(严格限色)

| 角色 | 色值 | 用途 |
|---|---|---|
| 奶白底 | `#faf9f5` | 背景主色 |
| 陶土橙 | `#d97757` | 主体强调色、暖光、关键文字 |
| 雾蓝 | `#6a9bcc` | 阴影、远景、冷物体 |
| 苔绿 | `#788c5d` | 植物、辅助强调 |
| 墨炭 | `#141413` | 线条、字体、深色物体 |

> 这 5 个色是同一套品牌色。**保证生成的图直接嵌入网页/PPT 毫无违和**。

### 视觉签名

1. **限色** — 严格 5 色,不允许渐变,不允许霓虹荧光
2. **纸纹** — visible paper grain(打印颗粒感)
3. **错位** — slight offset misregistration(套色不准的复古感)
4. **手绘线** — loose hand-drawn ink lines(略有抖动,不机械)
5. **平面** — flat color blocks(无阴影,无 3D)
6. **复古** — 70 年代独立杂志 / zine 美学
7. **横版** — 16:9 默认,适合网页 banner 和 PPT

### 必须禁止的元素

每个 prompt 末尾必须包含:`No gradients, no 3D, no neon, no cyberpunk, no glossy.`
否则模型会偷偷加渐变光、霓虹边、3D 阴影。

## Prompt 模板

**建议保持 < 1024 字符**(多数生图模型有 prompt 长度上限,Seedance 硬限 1024)。

### 基础模板

```
Risograph print illustration, editorial magazine style. {SCENE_DESCRIPTION}

Strict 5-color palette: cream off-white background (#faf9f5), terracotta orange (#d97757) for {ORANGE_USAGE}, dusty blue (#6a9bcc) for shadows, sage green (#788c5d) accents, deep charcoal (#141413) line art.

Visible paper grain, slight offset misregistration, loose hand-drawn ink lines, flat color blocks. No gradients, no 3D, no neon. 1970s indie zine aesthetic. 16:9 horizontal. {TEXT_CLAUSE}
```

### 占位符填法

| 占位符 | 说明 | 例子 |
|---|---|---|
| `{SCENE_DESCRIPTION}` | 场景主体 + 主要对象 + 动作 + 氛围,2-4 句 | `Inside a small bar, a software engineer sits at a wooden counter while the bartender hands over a frothy beer mug. Both smile calmly. Visible bar shelves with bottles, warm window light from the right.` |
| `{ORANGE_USAGE}` | 哪些元素用主色橙 | `the beer foam and warm light` / `the lizard skin and warm accents` / `the chaotic trajectory line` |
| `{TEXT_CLAUSE}` | 文字策略,3 选 1 | `No text in the image.` / `The only text shown is "FRIED RICE" and "BOOM".` / `The garbled symbols and squares are the focal visual.` |

### 文字处理(关键)

文生图模型渲染中文几乎一定乱,英文短词偶尔正确。三种策略:

1. **完全无字** → 加 `No text in the image.`
2. **少量英文标志/品牌名** → 加 `The only text shown is "BAR.EXE" in block letters.`
3. **故意要乱码效果**(编码错误主题) → 加 `The garbled symbols/squares are the focal visual.`

中文文案**坚决不要让模型画**,留到网页 caption 里写。

## 工作流

### 1. 单张生成

```
1. 解析用户描述 → 生成 1 个 SCENE_DESCRIPTION
2. 套入基础模板 → 拼出 prompt(注意长度上限)
3. 调你自己接入的文生图模型,把 prompt 传进去
4. 拿到返回的图片(URL 或二进制),按你的需要下载 / 保存 / 展示
5. 返回:本地路径 + 用过的 prompt(方便用户微调重生)
```

> 接入哪个模型由你决定。常见做法:某个文生图 HTTP API、一个 image-generation MCP server、
> 或本地 Stable Diffusion / ComfyUI。本 skill 不预设端点、不携带任何 key。

### 2. 批量生成(系列图)

并发或串行调用 N 次生图(取决于你的后端是否支持并发),
依次下载 + 命名 `01-xxx.jpg / 02-xxx.jpg ...`,最后输出索引清单。

> 多数生图模型单次调用约 30-50 秒,若后端支持并发,系列图一次性发 N 个请求更快。

### 3. (可选)写入剪切板(macOS)

```bash
osascript -e 'set the clipboard to (read (POSIX file "/path/to/img.jpg") as JPEG picture)'
```

支持 JPEG / PNG / TIFF,对应 `as JPEG picture` / `as PICT` 等。

## 实战案例(用过的 prompt 直接复用)

### 案例 1:酒吧外景 — 工程师推门

```
Risograph print illustration, editorial magazine style. A cozy small bar with a glowing rectangular sign "BAR.EXE" above entrance, street view at night. A lone software engineer figure with backpack and laptop walks toward the bar door. Through the windows: bartender behind counter, stools.

Strict 5-color palette: cream off-white background (#faf9f5), terracotta orange (#d97757) for sign and warm light, dusty blue (#6a9bcc) for shadows, sage green (#788c5d) accents, deep charcoal (#141413) for line art.

Visible paper grain, slight offset misregistration, hand-drawn loose ink lines, flat color blocks with overlap. No gradients, no 3D, no neon glow, no cyberpunk. 1970s indie zine cover aesthetic. 16:9 horizontal. No text except "BAR.EXE" sign in block letters.
```

### 案例 2:特殊数字漂浮的概念图

```
Risograph print illustration, editorial style. Bar interior. A confused bartender holds a measuring beaker, carefully pouring exactly 0.7 cup of beer. Around him float oversized numbers "-1", "0.7", "2³²" and an infinity symbol. A small overflowing barrel sits in the corner. Surreal absurd math vibe.

Strict 5-color palette: cream off-white (#faf9f5) background, terracotta orange (#d97757) for beer and key digits, dusty blue (#6a9bcc) for shadows and floating math symbols, sage green (#788c5d) accents, deep charcoal (#141413) line art.

Visible paper grain, slight offset misregistration, loose hand-drawn lines, flat color blocks. No gradients, no 3D, no neon. 1970s indie zine aesthetic. 16:9 horizontal. The only text shown is the floating numbers "-1", "0.7", "2³²".
```

### 案例 3:剖面建筑 + 轨迹线

```
Risograph print illustration, editorial cross-section style. Cutaway view of a small bar building showing the interior. A wild winding red dashed trajectory weaves chaotically: enters through front door, exits a side window, climbs in via the back door, dives down through a sewer manhole. Each entry/exit marked. The bartender stands inside the bar looking exhausted.

Strict 5-color palette: cream off-white (#faf9f5) background, terracotta orange (#d97757) for the chaotic trajectory line, dusty blue (#6a9bcc) for building walls and shadows, sage green (#788c5d) for door/window accents, deep charcoal (#141413) line art.

Visible paper grain, slight offset misregistration, loose hand-drawn lines, flat color blocks. No gradients, no 3D, no neon. 1970s indie zine architectural cutaway aesthetic. 16:9 horizontal. No text.
```

更多 prompt 在 `examples/` 里。

## 经验 & 踩坑

### 通用生图限制

- **Prompt 长度**:多数模型有上限(Seedance 1024 字符),超长会报错,需缩短
- **临时 URL 会过期**:很多生图服务返回的图片 URL 有有效期(常见 24 小时),拿到后应立即下载,不要存 URL 留到后面用
- **单次调用 30-50 秒**:批量场景若后端支持并发,一次性发 N 个请求更快

### 风格保真

- "Strict 5-color palette" 这个短语**必须有**,不写的话模型会随机加色
- "No gradients, no 3D, no neon, no cyberpunk" 必须放在最后,**抑制 AI 默认风格**
- "1970s indie zine aesthetic" 比 "Risograph" 更稳定地触发对的氛围
- "Visible paper grain, slight offset misregistration" 是质感关键词

### 文字渲染

- 中文几乎一定乱 → **永远不要让模型画中文**
- 英文短词(< 8 字母)偶尔正确,长词常出错
- 安全做法:`No text in the image` + 网页/PPT 上叠文字
- 想要文字时,显式列出 `The only text shown is "X" and "Y"`,而不是让模型自由发挥

### 中文目录/列表/章节图怎么办

如果场景就是要"中文目录页"、"中文章节封面",有三档兜底:

1. **首选:翻译成英文画**(本 skill 走过的路验证可行)。让模型画 `01 Overview / 02 Strategy / 03 Environment ...` 这样的英文章节列表,长度短、模型稳定渲染。听众看图时口播中文,或者下方加中英对照表。
2. **次选:模型画框架,PIL 后期叠中文**。让模型画一本"翻开的书 / 空白章节列表"作为视觉框架,然后用 Pillow + 系统中文字体精确叠中文。能保证字一定对,但要花时间调坐标,**不推荐**作为默认路径。
3. **下下策:HTML/CSS 模拟书页**。完全失去 Risograph 手绘味,基本等于"放弃这个 skill"。

经验:用户说"我要中文版"时,先问清楚是不是必须中文——大多数场景下"高亮哪一章"才是核心信息,中文标题可以用图说补,英文版就够。

### 系列一致性

- 同一系列保持**完全相同的风格段落**(后半段),只改场景描述(前半段)
- 不要中途换调色板顺序,色值要逐字相同
- 角色一致性:同一系列每张都加`a software engineer figure`、`the bartender` 等指代,保证人物风格不漂

### 输出整理

- 文件名加序号 `01- / 02- / ...`,匹配章节顺序
- 单图体积 ~500KB-1.5MB(jpg),网页可直接用,无需压缩

## 接入生图后端(自行实现)

本 skill 不内置任何生图后端。落地时你需要补一层"调模型"的胶水,接口约定建议:

1. 解析用户描述 → 生成 1 个或 N 个 SCENE_DESCRIPTION
2. 套入基础模板 → 拼出 prompt(注意长度上限)
3. 调用**你接入的**文生图模型(API / MCP / 本地模型),传入 prompt
4. 解析返回 → 拿到图片 URL 或二进制 → 下载到本地
5. (可选)写剪切板 / 上传到你的目标平台
6. 返回:本地路径列表 + 用过的 prompt(方便用户微调重生)

> 第 3 步是唯一与后端耦合的地方。换模型时只改这一步,prompt 模板和调色板规范保持不变。

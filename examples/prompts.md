# Prompt 速查表

实战用过、经过验证的 Risograph 风格 prompt。直接 copy 改 SCENE 部分即可。

风格段落(后半)在所有 prompt 里完全一致——不要改,改了一致性就崩。

## 通用风格段落(必须原样保留)

```
Strict 5-color palette: cream off-white background (#faf9f5), terracotta orange (#d97757) for {ORANGE}, dusty blue (#6a9bcc) for shadows, sage green (#788c5d) accents, deep charcoal (#141413) line art.

Visible paper grain, slight offset misregistration, loose hand-drawn ink lines, flat color blocks. No gradients, no 3D, no neon. 1970s indie zine aesthetic. 16:9 horizontal. {TEXT_CLAUSE}
```

---

## Cover · 入场 / 招牌

```
A cozy small bar with a glowing rectangular sign "BAR.EXE" above entrance, street view at night. A lone software engineer figure with backpack and laptop walks toward the bar door. Through the windows: bartender behind counter, stools.
```
- ORANGE: `sign and warm light`
- TEXT_CLAUSE: `No text except "BAR.EXE" sign in block letters.`

## Happy Path · 一切正常

```
Inside a small bar, a software engineer sits at a wooden counter while the bartender hands over a frothy beer mug. Both smile calmly. Visible bar shelves with bottles, warm window light from the right.
```
- ORANGE: `beer foam and warm light`
- TEXT_CLAUSE: `No text rendered in the image.`

## Boundary · 边界值漂浮

```
Bar interior. A confused bartender holds a measuring beaker, carefully pouring exactly 0.7 cup of beer. Around him float oversized numbers "-1", "0.7", "2³²" and an infinity symbol. A small overflowing barrel sits in the corner. Surreal absurd math vibe.
```
- ORANGE: `beer and key digits`
- TEXT_CLAUSE: `The only text shown is the floating numbers "-1", "0.7", "2³²".`

## Abnormal · 蜥蜴 / 怪味输入

```
Bar interior. A small lizard sits casually on the wooden counter. Next to it stands a dirty glass with murky "foot-bath water" and a fish bone floating in it. The bartender clutches his head in despair, eyes wide, mouth open in a silent scream. Surreal absurd humor.
```
- ORANGE: `lizard skin and warm accents`
- TEXT_CLAUSE: `No text in the image.`

## State · 建筑剖面 + 乱窜轨迹

```
Cutaway view of a small bar building showing the interior. A wild winding red dashed trajectory weaves chaotically: enters through front door, exits a side window, climbs in via the back door, dives down through a sewer manhole. Each entry/exit marked. The bartender stands inside the bar looking exhausted.
```
- ORANGE: `chaotic trajectory line`
- TEXT_CLAUSE: `No text.`
- 加一句 style: `cross-section style`

## Encoding · 乱码满天

```
Bar interior. Several beer glasses on the counter overflow with garbled characters: square blocks "□□□", "NaN", "null", "0xCC". The chalkboard menu has dissolved into nonsensical symbols. The bartender stares baffled at a glass full of square block characters spilling out. Vintage character-encoding error vibe.
```
- ORANGE: `warning glyphs and broken characters`
- TEXT_CLAUSE: `The garbled symbols and squares are the focal visual.`
- 加一句 style: `editorial glitch style`

## Stress · 人潮 / 极限负载

```
A tiny bar building viewed from outside, surrounded and overwhelmed by an enormous crowd of hundreds of stick-figure engineers stretching across the entire image, queuing to get in or rushing past. The bar building visibly tilts and bends under the pressure. Several beer barrels burst open, beer pouring out of windows.
```
- ORANGE: `bar and overflowing beer`
- TEXT_CLAUSE: `No text in the image.`

## Security · 废墟 / 注入攻击

```
A small bar half destroyed. The signboard hangs broken and crooked, walls shattered, tables and chairs disintegrating into pixelated dust particles flying away (Thanos-snap effect). SQL fragments float through the air: "DROP TABLE", semicolons, single quotes. The bartender stands amid the rubble, exhausted but alive. Empty stools.
```
- ORANGE: `fire embers and warning code`
- TEXT_CLAUSE: `The only text shown is the floating SQL fragments.`

## Finale · 反转

```
Bar interior, calm and intact. A regular casual customer (wearing a hoodie and jeans, normal-looking) sits at the counter holding a menu. The bartender behind the counter has gone completely pale, eyes wide in shock, sweat drops on his forehead, his face turning blue-screen blue. On the chalkboard menu the words "FRIED RICE" stand out in orange. A small comic-style explosion bubble with the word "BOOM" floats above the counter. Anti-climactic comedic ending vibe.
```
- ORANGE: `FRIED RICE and BOOM`
- TEXT_CLAUSE: `The only text shown is "FRIED RICE" and "BOOM".`

---

## 推广到非酒吧主题

把"Bar interior" 替换成新场景就行,色板和质感关键词原样保留。

### 例:电梯主题

```
A vertical cross-section of a 32-floor apartment building. The elevator car at floor 5 is brightly lit, with an overload-warning indicator glowing. Other floors show small silhouettes of waiting passengers.
```

### 例:工程师调试场景

```
A software engineer at a small wooden desk under a single warm lamp, late at night. Multiple monitors show scrolling logs and an error stack trace. A coffee cup, a sticky note saying "TODO". The engineer rubs his temples in despair.
```

### 例:抽象概念图(数据/算法)

```
An editorial conceptual illustration of a sorting algorithm: numbered cards sliding across a wooden table, with hand-drawn arrows showing the comparison swaps. A magnifying glass hovers over the in-progress segment.
```

---

## 不该写什么

下列词触发 AI "默认风格",一定要在 prompt 末尾的 negative 段抑制:

- 不要写 `realistic`、`photographic`、`hyper-detailed` → 会脱离 riso 风格
- 不要写 `vibrant colors` → 会破坏限色
- 不要写 `cyberpunk`、`neon`、`futuristic` → 会变赛博风
- 不要写 `glossy`、`polished` → 会变 3D 渲染感

每张 prompt 末尾保留固定的 negative:
```
No gradients, no 3D, no neon, no cyberpunk, no glossy.
```

---

## 字符数自检

Seedance 限 1024 字符。模板拼接后接近上限时,删除冗余形容词:
- "loose hand-drawn ink lines" → "loose ink lines"(省 9 字)
- "Visible paper grain, slight offset misregistration" → "Paper grain, offset misregistration"(省 14 字)
- "1970s indie zine aesthetic" → "indie zine aesthetic"(省 6 字)

但**不要砍**:
- 5 色调色板的色值(就是色值,模型靠 hex 锚定)
- "Strict 5-color palette" 这个开头(决定限色严格度)
- 末尾的 negative 段

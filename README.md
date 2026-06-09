# riso-style

> Anthropic 暖色调 + Risograph 复古印刷风格的插图 prompt 模板。

一套经过验证的 **Risograph 风格 prompt 模板**,用统一限色调色板(奶白底 / 陶土橙 / 雾蓝 / 苔绿 / 墨炭)+ 手绘线条 + 套色错位 + 纸纹质感,产出**风格高度一致**的系列插图。适合教学网页插图、PPT 配图、文章封面、品牌物料、故事分镜。

## 这是什么 / 不是什么

- ✅ **是**:一套 prompt 工程模板 + 调色板规范 + 实战 prompt 速查表,作为 [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) 使用。
- ❌ **不是**:一个开箱即用的生图服务。本仓库**不绑定任何生图后端,不携带任何 API key**。

具体生图用哪个模型、key 怎么配、图片怎么下载/保存,全部由你自行处理。模板在 Doubao Seedance、即梦、Midjourney、SDXL 等支持文本 prompt 的模型上均验证过——核心是**限色 + 质感关键词**,与具体模型无关。

## 用法

1. 把本仓库作为一个 Agent Skill 加载(`SKILL.md` 即 skill 定义)。
2. 描述你要的场景,skill 会按 `SKILL.md` 里的基础模板拼出一条 prompt。
3. 把拼好的 prompt 喂给**你自己接入的**文生图模型,拿到图。

接入生图后端的接口约定见 `SKILL.md` 末尾「接入生图后端」一节——唯一与后端耦合的只有「调模型」那一步,换模型不影响模板。

## Reference Images

`references/bar-images/` 提供 00-08 共 9 张酒吧系列参考图,对应 `examples/prompts.md` 里的实战 prompt。接入支持 reference image / style reference 的生图模型时,可以把这组图作为风格参考；不支持 reference 的模型也可以用它们做人眼校准样本。

## 文件结构

```
.
├── SKILL.md            # skill 定义:风格规范 + prompt 模板 + 工作流
├── examples/
│   └── prompts.md      # 实战验证过的 prompt 速查表(直接复用)
├── references/
│   └── bar-images/     # 00-08 酒吧系列风格参考图
├── LICENSE             # MIT
└── README.md
```

## License

[MIT](./LICENSE)

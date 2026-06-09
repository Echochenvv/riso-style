# Bar Images Reference

这一组图片是 `examples/prompts.md` 中 00-08 酒吧系列 prompt 的参考输出,用于校准 `riso-style` 的整体观感。

## 使用方式

- **作为风格参考**:接入支持 reference image / style reference 的生图模型时,可把本目录 9 张图作为同一套风格参考输入。
- **作为人工校准样本**:接入不支持 reference image 的模型时,用这些图对照生成结果,检查限色、纸纹、套色错位、手绘线条和 16:9 构图是否一致。
- **作为系列一致性样本**:做故事分镜或章节插图时,参考这一组的角色、场景和色彩连续性。

## 图片清单

| 文件 | 对应主题 |
|---|---|
| `00-cover.jpg` | Cover / 入场招牌 |
| `01-act01-smoke.jpg` | Happy Path / 一切正常 |
| `02-act02-boundary.jpg` | Boundary / 边界值漂浮 |
| `03-act03-abnormal.jpg` | Abnormal / 怪味输入 |
| `04-act04-flow.jpg` | State / 建筑剖面与轨迹 |
| `05-act05-encoding.jpg` | Encoding / 乱码满天 |
| `06-act06-stress.jpg` | Stress / 极限负载 |
| `07-act07-security.jpg` | Security / 注入攻击 |
| `08-finale-friedrice.jpg` | Finale / 反转结尾 |

## 注意

这些图片只作为 reference/style sample,不包含任何生图后端、API key 或调用逻辑。具体模型、reference 参数和计费方式由使用者自行处理。

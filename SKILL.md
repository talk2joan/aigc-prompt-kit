# AIGC Prompt Kit · 运镜与一致性元 Skill

**一句话定位：** 这是给「任何视频 AIGC 提示词写作」用的公共层。它不替你做具体影片，而是提供三样可复用的硬通货——**精确运镜词汇表、一致性锁方法、可核对质检清单**。

**和 seedance-prompt-library / seedance-* 分支的关系：** 那些分支是"主题库"（车、宠物、恐怖、旅拍…），本 Skill 是"公共方法层"。写一条 prompt 时，先按分支选模板，再按本 Skill 把"运镜精确化 + 身份锁定 + 自检"三件事做扎实。

## Use when

- 你想把一条 prompt 里的运镜从 `cinematic camera movement` 这种废话升级成**模型真的能执行**的具体运镜
- 你想要跨多个镜头保持**角色 / 产品 / 品牌外观一致**
- 你想在交付前用一份**可勾选清单**自检 prompt 有没有踩坑

## How it connects to existing skills

| 你已有的 Skill | 它负责 | 本 Skill 补什么 |
|---|---|---|
| seedance-prompt-library | 主题模板库（25 类） | 运镜术语表 + 质检清单 |
| seedance-car-vehicle | 车/速度片 | 一致性锁（车辆部件不漂移） |
| seedance-pet-animal | 动物主角片 | 一致性锁（数量钉死） |
| seedance-3d-cartoon | 3D 卡通角色 | 外观锁定 + 动作分段 |
| yayoi-kusama-style | 图像风格系统 | 图像向运镜/场景描述复用 |

## The three hard-won rules (from your corpus)

1. **运镜要写到"可执行"，不是"可想象"。** `slow cinematic dolly` 是废话，`Slow push-in from wide shot over 4 seconds, ending on the birds at 40% frame height` 才是指令。
2. **身份要写到"全片锁定"，不是"逐镜头重述"。** 在固定块里写一次外观，再加一句全程不变；逐镜头重复外观反而诱发段间突变。
3. **失败要写到"负面清单"，不是"希望它成功"。** 一个集中的 Not Do 块比十句正面描述更有效。

## Workflow

1. **锁定锚点（Anchor）**：从 `references/movement-lexicon.md` 挑一个精确运镜术语，或者从 eyecannndy 的 160 个技法里挑一个 slug。
2. **锁定身份（Lock）**：按 `references/consistency-lock.md` 给角色 / 产品 / 品牌写继承清单和不继承清单。
3. **填结构（Structure）**：按 `references/method-structure.md` 把 prompt 组织成 固定块 + 时间轴块 + 全局约束块。
4. **自检（Check）**：按 `qa/checklist.md` 逐项勾选，尤其关注运镜是否精确、身份是否锁定、负面清单是否集中。
5. **交付**：输出可复制 prompt 块 + 使用的运镜术语 + 使用的锚定案例。

## Key references

- **运镜词汇表** → `references/movement-lexicon.md`（160 个技法，含运镜/剪辑/特效/构图/风格分类）
- **一致性锁方法** → `references/consistency-lock.md`（角色 / 产品 / 品牌锁定模板）
- **方法论与结构** → `references/method-structure.md`（固定块 + 时间轴 + 负面清单）
- **质检清单** → `qa/checklist.md`（可勾选的自检项）

## Language

回复用用户的语言。prompt 本身可保持英文（如果目标工作流需要）；中文结构说明见 `references/method-structure.md` 后半部分。

## Notes

- `references/movement-lexicon.md` 的术语来源是 [eyecannndy.com](https://eyecannndy.com/)（Jacobi Mehringer 的 Visual Technique Library，160 个运镜技法），站方定位为"Enjoy. Learn. Don't gatekeep."。术语 slug 直接引用其 URL，不手改。
- 方法论的锚定案例来自你的 seedance-* skill 家族和 goodcase.ai 已验证案例，不是通用视频生成常识。
- 本 Skill 只承载"公共方法层"，不承载具体主题模板。要写某类影片，请回主题 Skill。
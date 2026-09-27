# AIGC Prompt Kit · 运镜与一致性元 Skill

**一句话：** 把「写 AIGC 视频提示词」从"凭感觉写"变成"按词典查、按清单锁、按质检过"的**可工程化流程**。

> **这个 Skill 解决的核心问题：** 你写一条 prompt 时，最常犯的错不是"画面描述不够美"，而是——
> - 运镜写得含糊：`cinematic camera movement` 这种废话，模型根本不知道你要什么
> - 身份锁不住：同一角色第 3 个镜头长出第三只手，同一产品换个颜色
> - 失败防不住：Not Do 清单没写、写了但埋在段中间
>
> 这个 Skill 把这三件事拆成**三个可复用的硬通货**：**143 个精确运镜术语表**、**一致性锁三件套**、**28 项交付质检清单**。

---

## 为什么它值钱（夸一夸）

### 1. 运镜写到"可执行"，不是"可想象"

普通 prompt 库给你一堆 `cinematic dolly` 这样的词，模型理解成什么就是什么。这个 Skill 让你写：

- `Slow push-in over 4s, ending on the face at 40% frame height`（推镜 + 时长 + 落点）
- `Whip pan 90 degrees in 0.3s, landing on the door`（甩镜 + 角度 + 时间）
- `Dolly zoom, push in while zooming out, background stretches`（眩晕推拉，写明关键）

**143 个运镜术语**按 5 大类（运镜 / 剪辑 / 特效 / 构图 / 风格）组织，每个带英文术语、中文含义、**AIGC 提示写法示例**、AIGC 高频坑。你不再需要记运镜名词，查表就能写。

### 2. 一致性锁三件套，直接解决"段间漂移"

这是 AIGC 视频**最致命**的问题。Skill 把它拆成可复用的协议：

| 件 | 作用 | 例子 |
|---|---|---|
| **Token 声明** | 把实体钉成变量，全片只引用不重画 | `@Koru = 红橙羽毛奇异鸟，头顶红羽冠` |
| **继承/不继承清单** | 控制什么保留、什么改变 | 继承：羽毛颜色；不继承：草裙（SH005 起换藏装） |
| **全局 Not Do** | 一次性禁掉所有失效模式 | `No attribute swap, No cloning, exactly ONE` |

含 **角色 / 产品 / 品牌** 三种锁定模板，覆盖剧情片、电商片、品牌片。

### 3. 28 项质检清单，交付前可勾选

把"这条 prompt 能不能用"变成**可勾选的流程**，8 项红项（结构完整性）、20 项黄项（一致性/运镜/负面清单），任一红项未通过不交付。

**这是网上 90% prompt 模板不具备的**——它们给你模板，不给你"怎么判断模板用对了"。

### 4. 端到端验证过

用《稻城之恋 SH001》实战 prompt 跑质检清单，**9/10 项通过**，证明方法论和真实出片经验吻合，不是纸上谈兵。

---

## 结构

```
aigc-prompt-kit/
├── SKILL.md                          # 入口，定位 + 与现有 skill 的关系
├── references/
│   ├── movement-lexicon.md           # 143 个运镜/视觉技法术语（5 大类）
│   ├── consistency-lock.md           # 一致性锁三件套 + 3 种锁定模板
│   └── method-structure.md           # 四块骨架：全局+固定+时间轴+约束
├── qa/
│   └── checklist.md                  # 28 项交付质检清单（红/黄项）
└── (本项目) LICENSE / README.md
```

---

## 来源标注（重要 · 请勿混淆）

本 Skill 不是凭空发明的，而是**从已验证的真实来源蒸馏而来**。请尊重原作者。

### 运镜术语表（`references/movement-lexicon.md`）

**来源：[Eyecandy - Visual Technique Library](https://eyecannndy.com/)**  
作者：Jacobi Mehringer  
定位：站方自述 *"The visual technique library for visual technique lovers. Enjoy. Learn. Don't gatekeep."*  
用途：136 个唯一运镜技法 slug，按 5 大类整理，补充了 AIGC 提示写法与高频坑。

> 本 Skill 只引用其**术语命名体系和分类**，未复制任何影像内容。站方明确欢迎学习与传播。

### 方法论与一致性锁（`references/consistency-lock.md`, `references/method-structure.md`）

**来源：seedance-* skill 家族（LearnPrompt/awesome-seedance）**

- [seedance-prompt-library](https://github.com/LearnPrompt/awesome-seedance) — 25 类主题模板
- seedance-car-vehicle / seedance-pet-animal / seedance-3d-cartoon 等 11 个分支 — 单主题模板
- 案例来源：[goodcase.ai](https://goodcase.ai/cases?filter=video) — 463 个人工验证的 Seedance 出片案例

### 实战锚定（端到端验证用）

《稻城之恋 EP.02 · Two Little Kiwis in Daocheng》— 9 镜头分镜提示词库，用于验证质检清单有效性。

---

## 怎么用

**作为 Skill 安装**（Claude Code / Codex / 商汤小浣熊 等支持 Skill 的 Agent）：

1. 克隆本仓库到 `~/.claude/skills/` 或对应目录
2. 写 prompt 时，Agent 会自动加载本 Skill 的运镜词典和一致性锁
3. 交付前自动跑质检清单

**作为提示词模板直接粘贴**（不装 Skill，直接用 chat 模型）：

把 SKILL.md 里的三条铁律抄进你的 workflow：

> 1. 运镜写到"可执行"，不是"可想象"
> 2. 身份写到"全片锁定"，不是"逐镜头重述"
> 3. 失败写到"负面清单"，不是"希望它成功"

---

## 许可证

[MIT](LICENSE) — 运镜术语、方法论、质检清单**全部开源**，欢迎使用、修改、二次分发。

**唯一要求：** 保留本 README 的来源标注，尊重 [eyecannndy.com](https://eyecannndy.com/)（Jacobi Mehringer）和 LearnPrompt/awesome-seedance 社区的原作者。

---

## 致谢

- [Eyecandy](https://eyecannndy.com/) — 运镜术语命名体系（Jacobi Mehringer）
- [LearnPrompt/awesome-seedance](https://github.com/LearnPrompt/awesome-seedance) — Seedance prompt 案例库
- [goodcase.ai](https://goodcase.ai) — 463 个人工验证案例
- 商汤小浣熊 — AIGC prompt 工程协作平台

> 做这个 Skill 的初衷：**提示词不该被 gatekeep。** 让每一个想做 AIGC 视频的人，都能像查词典一样写 prompt，像过安检一样质检。
# 方法论与结构 · Method Structure

> 这是从你的 seedance-* skill 家族蒸馏出的**通用 prompt 骨架**。无论写车、宠物、恐怖、旅拍，结构都一致：**全局块 + 固定块 + 时间轴块 + 全局约束块**。

## 四块骨架

任何一条 AIGC 视频 prompt 都应该由以下**四块**组成。跳过任何一块，就是 prompt 变模糊的地方。

### 块 1：全局块（Global Block）

**放什么：** 时长、画幅、帧率、整体风格、画质词汇。

**示例：**
```text
Disney Pixar 3D animated short film style, healing aesthetic,
warm color palette, soft lighting, 4K, kid-friendly.
Total duration: 15 seconds, vertical 9:16, 24 fps.
```

**要点：**
- **时长必须写死**。写 30 秒却只列 24 秒，模型会拉长最后一段填满
- **画幅必须写死**。`16:9` 和 `9:16` 生成的构图完全不同
- **风格只用一个形容词组**。不要堆 5 个风格词，会互相打架

### 块 2：固定块（Fixed Block）

**放什么：** 全片不变的人物、服装、道具、地点。

**示例：**
```text
CHARACTER LOCK (@Koru and @Moana):
@Koru: small cartoon kiwi bird, red-orange feathers, upright red crest, rounded child-sized proportions.
@Moana: small cartoon kiwi bird, yellow-orange feathers, pink flower headband, rounded child-sized proportions.
Both wearing green leaf skirts (Pacific outfit).
```

**要点：**
- **写一次，不要逐镜头重写**。逐段重申外观反而诱发段间突变
- 每个角色**一个 Token + 一个外观锚**
- 加上一句 `Preserved: ALL above for every shot` 全片锁定

### 块 3：时间轴块（Timeline Block）

**放什么：** 逐秒/逐段分镜脚本，一段一拍。

**示例：**
```text
[00:00-00:04] Shot 1: Slow Push-in
Setting: High-altitude meadow in Daocheng, snow mountains in distance.
@Koru and @Moana: walking side by side toward the detector station.
Camera: Slow push-in from wide shot, gradually bringing birds and detector closer.
Lighting: Bright natural daylight, soft shadows.
Sound: High-altitude wind, distant birdsong.
```

**要点：**
- **段长 2-5 秒**。纪实跟拍 2s 一段，广告 3s，音频驱动 MV 可细到亚秒
- **时间写成闭区间首尾相接**（`0-4s` 接 `4-8s`），总和等于总时长
- 每段写 **机位 + 动作 + 细节 + 声音**，不要只写情绪
- 段越短，越要写**可见的动作动词**，不要写**情绪形容词**

### 块 4：全局约束块（Global Constraint Block）

**放什么：** Not Do 清单 + 硬性限制，全片生效。

**示例：**
```text
Do NOT:
- No religious symbols (prayer flags, stupas, Buddha statues)
- No text or letters
- No extra characters (only Koru and Moana)
- No attribute swap between Koru and Moana
- No cloning, duplicates, or feature averaging
```

**要点：**
- **放在 prompt 末尾**，一次生效，不要埋在段中间
- 每条写清**禁止什么 + 括号说明具体形式**
- 写 `no extra characters` 比 `keep it simple` 有效 100 倍

---

## 时间轴示例（逐秒分段）

**示例：15 秒城市漫游 Vlog**

```text
[00:00-00:03] Shot 1: Wide establishing shot
Setting: Neon-lit alley in Tokyo at night, rain-slicked pavement.
Subject: Young woman in a beige trench coat, walking toward camera.
Camera: Static, slight handheld drift.
Sound: City ambience, distant traffic.

[00:03-00:06] Shot 2: Tracking follow shot
Subject: Same woman, same coat, walking through the alley.
Camera: Tracking behind her at a fixed distance, following her pace.
Action: She pauses to look at a shop window.
Sound: Shop door chime, rain.

[00:06-00:09] Shot 3: Over-the-shoulder
Subject: Same woman looking at the window display.
Camera: Over-the-shoulder, foreground shoulder soft.
Action: She reaches out and touches the glass.
Sound: Music starting, soft.

[00:09-00:12] Shot 4: Close-up on hands
Subject: Her hand touching the glass, raindrops on it.
Camera: Macro close-up on the hand and glass.
Action: A drop slides down the glass.
Sound: Music continues, rain softens.

[00:12-00:15] Shot 5: Push-in on reflection
Subject: Her reflection in the glass, neon lights behind.
Camera: Slow push-in on the reflection.
Action: She smiles faintly, turns to walk away.
Sound: Music peaks, then fades.
```

**关键：**
- 每一段**机位都不同**（Wide → Tracking → OTS → Macro → Push-in）
- 每一段**有一个动作**（走 → 停 → 触 → 滴 → 笑）
- **固定块锁住**：同一位女性、同一件风衣、同一个雨夜

---

## 常见坑（Pitfalls）

| 坑 | 症状 | 修复 |
|---|---|---|
| **只写总时长不写分段** | 视频 6 秒后开始漂 | 每段写 `[00:00-00:04]` 闭区间，总和=总时长 |
| **逐镜头重写外观** | 段间角色突变 | 外观写进固定块，后续用 Token |
| **一个镜头写两个机位** | 模型在中段自己切一刀 | 一秒只写一个机位 |
| **不写负面清单** | 莫名其妙多出第 3 只动物/第 5 根手指 | 末尾集中 Not Do |
| **时间精确到 0.01s** | 纯文本生成无意义 | 文本生成约 0.5s 分辨率，别超 |
| **把变形写成剪辑** | 变形变不自然 | 要求 `No cuts or jumps`，逐件写出变化 |
| **特写停在 Logo/文字上** | 生成文字必歪 | 特写改打材质/结构/接缝 |
| **风格词堆叠** | 画面风格打架 | 只用一个风格形容词组 |
| **时长不一致** | 模型拉长填满 | 分段总和 = 声明时长 |

---

## 中文结构速查

**任何一条 AIGC 视频 prompt 都包含以下四块：**

1. **全局块**：时长、画幅、帧率、风格、画质
2. **固定块**：人物/服装/道具/地点（写一次，全片锁定）
3. **时间轴块**：逐秒分段，一段一拍，每段一个机位 + 一个动作 + 一行音效
4. **全局约束块**：Not Do 清单，放在 prompt 末尾，全片生效

**三条铁律：**
- 运镜写到"可执行"，不是"可想象"
- 身份写到"全片锁定"，不是"逐镜头重述"
- 失败写到"负面清单"，不是"希望它成功"
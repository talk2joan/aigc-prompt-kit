# 一致性锁方法 · Consistency Lock

> **为什么重要：** AIGC 视频最致命的缺陷不是画面质量，而是**段间外观漂移**。同一角色第 3 个镜头长出第三只手、同一产品换个颜色、同一品牌换个 Logo。本方法来自你的 seedance-* skill 家族和《稻城之恋》实战，是**可复用的锁定协议**。

## 三件套：Token + 继承/不继承 + 全局 Not Do

一致性锁不是一个动作，而是**三件套协同**。缺一个，锁就会松。

### 1. Token 声明（把实体钉成变量）

给每个需要保持一致的实体起一个短 Token，全片只用 Token 引用，**不要逐镜头重写外观描述**。

```text
@Koru = 橙色奇异鸟（红棕色羽毛，头顶红色蓬松羽冠，体型较大）
@Moana = 黄色奇异鸟（浅橙色羽毛，粉红色花朵头饰，体型较小）
```

**规则：**
- Token 长度 2-6 个字符，用 `@` 前缀区分
- Token 声明**只在固定块写一次**，后续镜头用 `@Koru` 引用
- 每个 Token 附一句**可测量的外观锚**（颜色 + 形状 + 关键特征），不要只写情绪词

**为什么有效：** 逐镜头重写 `red-orange feathers, pink flower headband` 会诱发模型"重生成"这个角色，每次都略有不同。Token 让模型"记住"而不用"重画"。

### 2. 继承 / 不继承清单（控制什么保留、什么改变）

这是**跨场景一致性**的关键。角色换衣服、换场景时，必须明确声明**哪些保留、哪些改变**。

```text
继承清单（所有镜头保持不变）：
- 羽毛颜色、面部特征、体型比例
- Koru 的头顶红色蓬松羽冠
- Moana 的粉红色花朵头饰

不继承清单（某些镜头必须改变）：
- 惠灵顿的绿色叶子草裙（SH005 起换成藏装）
- 尤克里里/小吉他
- 惠灵顿码头/游艇背景
```

**规则：**
- 继承清单写**永久不变**的核心外观
- 不继承清单写**会改变**的部分，并标注改变发生的时间点
- 两个清单都必须是**可勾选的清单**，不要写段落

**为什么有效：** 只写"保持一致"没有用，模型不知道具体是哪些东西要保持。写清"保留 X、不保留 Y"，模型才知道边界。

### 3. 全局 Not Do（一次性禁掉所有失效模式）

把全片所有**不能出现**的东西集中在一个块里，放在 prompt 末尾，一次生效。

```text
Do NOT:
- No religious symbols (prayer flags, stupas, Buddha statues)
- No monks or religious figures
- No text or letters
- No adult ceremonial robes
- No cloning, duplicates, or feature averaging
- No attribute swaps between Koru and Moana
```

**规则：**
- Not Do 块放在 prompt **最后**，不要埋在段中间
- 每个条目写清"禁止什么" + 可选"括号说明具体形式"
- Not Do 要**具体**（`No religious symbols (prayer flags, stupas)`），不要写 `No inappropriate content`

**为什么有效：** 正面描述让模型"希望成功"，负面清单让模型"避免失败"。失败比成功更难修复，负面清单更值钱。

---

## 分类型锁定模板

### A. 角色锁定（Character Lock）

用于角色驱动的剧情片、动画、Vlog。

**固定块（写在时间轴之前）：**
```text
CHARACTER LOCK (@Koru):
- Species: small cartoon kiwi bird
- Color: red-orange feathers
- Signature: upright red fluffy crest on head
- Body: rounded, child-sized proportions
- Face: large expressive eyes, small beak
- Preserved: ALL above for every shot, no mutation
```

**变装规则（写在 Not Do 前）：**
```text
OUTFIT TRANSITION:
- SH001-SH004: green leaf skirt (Pacific outfit)
- SH005: transformation moment (leaf skirt -> Tibetan outfit)
- SH006-SH009: traditional Tibetan outfit
- Feather color and facial features MUST stay identical before and after
```

**关键坑：**
- ❌ 逐镜头重写外观 → ✅ 固定块写一次 + Token
- ❌ 让角色改变体型 → ✅ `rounded, child-sized proportions` 钉死
- ❌ 变装后特征互换 → ✅ `no attribute swap` 明确禁止
- ❌ 生成多个分身 → ✅ `exactly ONE [character]` 钉死数量

### B. 产品锁定（Product Lock）

用于产品广告、电商短片、品牌片。

**固定块：**
```text
PRODUCT LOCK:
- Product: [name]
- Color: [specific hex or brand color]
- Logo: [logo described as geometric shapes, NO text]
- Material: [specific material]
- Scale: [relative to hand or environment]
- Preserved: ALL above for every shot, no color drift
```

**运镜配合：**
- 产品展示用 `Central Framing` + `Product` 运镜组合
- 特写**避开 Logo 文字**，改打材质、接缝、纹理
- 全程 `shallow depth of field` 让背景虚化，聚焦产品

**关键坑：**
- ❌ 让 Logo 出现文字 → ✅ `Logo described as geometric shapes, NO text`（生成文字必歪）
- ❌ 颜色漂移 → ✅ `Preserve the exact [brand color]` 写死
- ❌ 产品变形 → ✅ `no duplicated components, no floating product`
- ❌ 特写停在 Logo 上 → ✅ 特写改打材质/接缝/纹理

### C. 品牌锁定（Brand Lock）

用于品牌一致性、系列片、多场景品牌片。

**固定块：**
```text
BRAND LOCK:
- Brand visual language: [palette, typography, iconography]
- Color palette: [specific primary + secondary]
- Iconography: [specific icon set]
- Mood: [single adjective, e.g. "minimal, premium"]
- Excluded: competitor colors, off-brand typography
```

**关键坑：**
- ❌ 品牌色漂移 → ✅ 写 **hex 值或具体色名**（`#0F4C81`），不要写 `deep blue`
- ❌ 风格混搭 → ✅ 写 `single mood adjective`
- ❌ 出现竞品元素 → ✅ Not Do 里写 `no competitor logos, no off-brand typography`

---

## 生成顺序建议（避免连锁漂移）

**原则：** 先锁锚点镜头，再批量生成。

```text
1. 先生成开场镜头（SH001）—— 确认角色/产品形象 + 场景氛围
2. 再生成关键动作镜头（如 SH006 乐器演奏）—— 确认复杂动作
3. 然后生成特效镜头（如 SH003 粒子）—— 确认视觉难点
4. 最后批量生成剩余镜头
```

**为什么有效：** 
- 开场镜头一旦满意，后续所有镜头都用它做参考图/参考帧
- 关键动作镜头先出，能尽早发现动作不可行，避免返工
- 特效镜头独立性强，先验证不阻塞主线

**Seed 策略（如有支持）：**
- 开场用固定 Seed 定调
- 关键动作镜头单独 Seed，不要和开场共用
- 收尾大场面单独 Seed，防止漂移

---

## 一致性核对清单

交付前逐项勾选：

- [ ] 每个角色/产品有明确 Token 声明
- [ ] Token 只在固定块写一次，后续引用
- [ ] 继承清单列出了"永久不变"的核心外观
- [ ] 不继承清单列出了"会改变"的部分及改变时间点
- [ ] 全局 Not Do 块放在 prompt 末尾，集中
- [ ] Not Do 里写清了数量钉死（`exactly ONE`）
- [ ] 变装/变形前后，核心外观（羽毛/颜色/脸部）保持一致
- [ ] 品牌/产品色写成了具体色名或 hex
- [ ] 特写避开文字/Logo 区域
- [ ] 生成顺序符合"先锁锚点，再批量"
# 运镜词汇表 · Movement Lexicon

> 来源：[eyecannndy.com](https://eyecannndy.com/)（Jacobi Mehringer 的 Visual Technique Library，定位 "Enjoy. Learn. Don't gatekeep."）。共 136 个唯一技法 slug，按 5 大类组织。
> 每个条目：**英文术语**（建议直接写进 prompt）/ **中文含义** / **AIGC 提示写法** / **eyecannndy 链接**。
> 使用原则：运镜不要写成 `cinematic camera movement`，写成具体术语 + 时间 + 机位 + 结束位置。

---

## 分类速览

| 大类 | 数量 | 覆盖 |
|---|---|---|
| 运镜 Motion | 32 | 镜头怎么动（弧线、推拉、环绕、跟拍…） |
| 剪辑 Editing | 22 | 镜头怎么切（闪切、跳切、定格…） |
| 视觉特效 VFX | 34 | 画面怎么变形（子弹时间、数据乱码…） |
| 构图 Framing | 11 | 画面怎么摆（特写、俯拍、过肩…） |
| 风格 Style | 43 | 整体质感（梦境、复古、像素、潮玩…） |

---

## 一、运镜 Motion（镜头怎么动）

### 基础六运动

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Pan` | 摇 | `Slow pan left to right over 4s, ending on the horizon` |
| `Tilt` | 俯仰摇 | `Tilt up from the shoes to the face over 3s` |
| `Tracking` | 跟拍 | `Tracking shot following the subject at a fixed distance` |
| `Trucking` | 横移 | `Truck right alongside the car, keeping it centered` |
| `Dolly (Dolly Shot)` | 推拉 | `Slow push-in over 4s, ending on the face at 40% frame height` |
| `Pedestal` | 升降 | `Pedestal up, revealing the whole room` |

**AIGC 要点：** 推镜（push-in）和拉镜（pull-back）是 AIGC 最容易执行的两个运镜，写清**时长 + 结束位置**即可；不要写 `dolly` 就完事。

### 进阶运动

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Arc Movement` | 弧线运动 | `Camera arcs around the subject 180 degrees over 5s, keeping focus locked` |
| `Camera Roll` | 滚转 | `Slow camera roll clockwise during the jump` |
| `Whip Pan` | 甩镜 | `Quick whip pan 90 degrees in 0.3s, landing on the door` |
| `Dutch Angle` | 荷兰角 | `Dutch angle, camera tilted 20 degrees` |
| `FPV Drone` | FPV 穿越机 | `FPV drone shot, flying between the pillars at speed` |
| `Ground Shot` | 地面机位 | `Ground-level shot, camera almost touching the grass` |
| `Low Angle` | 低角度 | `Low angle from below, looking up at the building` |
| `High Angle` | 高角度 | `High angle from above, looking down at the crowd` |
| `Worms-Eye` | 虫眼视角 | `Extreme low angle, worm's-eye view` |
| `Overhead` | 俯拍 | `Top-down overhead shot, birds-eye view` |
| `Over the Shoulder` | 过肩 | `Over-the-shoulder shot, subject in focus, foreground shoulder out of focus` |
| `Profile Shot` | 侧面 | `Profile shot, subject seen from the side` |
| `First-Person POV` | 第一人称 | `First-person POV, handheld, looking forward` |
| `Snorricam` | 斯诺里卡姆 | `Snorricam-style, camera attached to the subject's chest, subject in frame` |
| `Locked-On` | 锁定跟随 | `Locked-on shot, camera tracks the subject continuously` |
| `Falling` | 下坠 | `Camera falling with the subject, increasing speed` |
| `Levitation / Floating` | 漂浮 | `Slow floating camera movement, dreamlike` |
| `Wandering` | 漫游 | `Wandering handheld camera, exploring the space` |
| `Omnidirectional` | 全向 | `Omnidirectional camera move, free 360 rotation` |
| `Dolly Zoom` | 推拉变焦（眩晕） | `Dolly zoom (Vertigo effect), push in while zooming out` |
| `Double Dolly` | 双轨推车 | `Double dolly, subject walks on one dolly, camera on another` |

**AIGC 高频坑：**
- `Whip Pan` 要写**角度 + 时间**，否则模型会做成普通转镜。
- `Dolly Zoom` 是 **AIGC 最容易失败**的运镜之一，务必写 `push in while zooming out, background stretches`。
- `FPV Drone` 要写**穿过的物体**（`between pillars`），否则只是普通飞行。
- `Locked-On` 是**一致性神器**，角色/产品保持居中不动，背景后退。

---

## 二、剪辑 Editing（镜头怎么切）

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Jump Cut` | 跳切 | `Hard jump cut, same framing, time advanced 2s` |
| `Cut-ins` | 插接 | `Cut-in to a close-up of the hands` |
| `Flash Cut` | 闪切 | `Flash cut, 2-frame burst` |
| `Quick Cuts` | 快速剪辑 | `Series of quick cuts, 3 shots in 2s` |
| `Crash Transition` | 硬切转场 | `Crash cut transition, hard change with no dissolve` |
| `Match Cut` | 匹配剪辑 | `Match cut, the circle in one shot matches the circle in the next` |
| `Match Motion` | 动作匹配 | `Match motion cut, the arm swing continues across the cut` |
| `Match Split` | 匹配分割 | `Match split, screen divides into two, each side continues the action` |
| `Freeze Frame` | 定格 | `Freeze frame on the reaction for 1s` |
| `Slow Motion` | 慢动作 | `Slow motion at 1/4 speed, 3s` |
| `Fast Motion (Undercranking)` | 快动作 | `Time-lapse fast motion, clouds racing` |
| `Speed Ramp` | 变速 | `Speed ramp from slow to fast over 3s` |
| `Stutter` | 卡顿 | `Stutter frame effect, replay 2 frames 3 times` |
| `Step-Printing` | 逐帧印 | `Step-printing, frame holds with 1/4 advance` |
| `Split Screen` | 分屏 | `Split screen, two scenes side by side` |
| `Screen in Screen` | 画中画 | `Screen-in-screen, smaller video window inside the main frame` |
| `Aspect Ratio Switch` | 比例切换 | `Aspect ratio switches from 16:9 to 4:3 mid-shot` |
| `Breakdown (BTS)` | 幕后 | `Behind-the-scenes breakdown shot` |

**AIGC 高频坑：**
- 大多数视频 AIGC **做不了真正的剪辑**，只能做单镜头。要"多镜头"必须写成**逐秒分段**（见 `references/method-structure.md` 的时间轴块）。
- `Freeze Frame` 在 Seedance 2.5 支持好，其他模型可能直接静止不动。
- `Slow Motion` 要写**减速倍数**（`1/4 speed`），否则模型不知道多慢。

---

## 三、视觉特效 VFX（画面怎么变形）

### 经典特效

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Bullet Time` | 子弹时间 | `Bullet time effect, camera orbits 180 degrees while subject freezes in mid-air` |
| `Slit-Scan` | 狭缝扫描 | `Slit-scan effect, image stretches vertically over time` |
| `Datamosh` | 数据乱码 | `Datamosh glitch effect, pixel blocks smearing horizontally` |
| `Echo Printing` | 回声印 | `Echo printing, ghost trail follows the subject` |
| `Double Exposure` | 双重曝光 | `Double exposure, city skyline overlays the face` |
| `Duplication` | 分身复制 | `Subject duplicates into 3 identical versions` |
| `Morphing` | 形变 | `Morphing effect, face transitions into another face` |
| `Kaleidoscope` | 万花筒 | `Kaleidoscope effect, scene reflects symmetrically` |
| `Projections` | 投影 | `Projection mapping onto a building facade` |
| `Reflections` | 反射 | `Water reflections mirror the scene` |
| `Magnification` | 放大 | `Magnification effect, scene zooms to reveal hidden detail` |
| `Distortions` | 扭曲 | `Subtle distortion, edges wobble like heat haze` |
| `Glitch / Feedback` | 故障反馈 | `VHS glitch feedback, screen tearing` |
| `Stylistic Suck` | 视觉坍缩 | `Stylistic suck, whole scene gets pulled into a point` |
| `Pass Through` | 穿透 | `Camera passes through the subject's chest, revealing the other side` |
| `Object Portal` | 物体传送门 | `Object portal, a doorway opens in the wall, another scene visible inside` |

### 光学与特效

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Motion Blur` | 运动模糊 | `Strong motion blur on the background, subject sharp` |
| `Focal Shift` | 焦点移动 | `Focal shift from foreground to background over 2s` |
| `Shallow Focus` | 浅景深 | `Shallow depth of field, background completely bokeh` |
| `Halation` | 光晕 | `Soft halation around bright lights, filmic glow` |
| `Haze` | 雾 | `Thin atmospheric haze, softens contrast` |
| `Hard Light` | 硬光 | `Hard direct light, sharp shadows` |
| `Spotlight` | 聚光 | `Single spotlight on the subject, rest in darkness` |
| `Vignette` | 暗角 | `Strong vignette, edges darken` |
| `Night Vision` | 夜视 | `Night vision, green phosphor glow` |
| `Thermal` | 热成像 | `Thermal imaging, hot areas bright yellow` |
| `X-Ray` | X 光 | `X-ray vision, shows skeleton through skin` |
| `Photogrammetry` | 摄影测量 | `Photogrammetry, 3D point cloud reconstructing the scene` |
| `Color Shift` | 色移 | `Color shift, warm tones transition to cold` |
| `Split Diopter` | 分景镜 | `Split diopter, near and far planes both in focus` |
| `Zoom` | 变焦 | `Slow zoom-in over 4s, ending on the detail` |

**AIGC 高频坑：**
- `Bullet Time` 在多数模型上不稳定，需写 **"subject frozen + camera orbits"** 两个动作分开。
- `Datamosh` / `Slit-Scan` 效果强烈，建议加 `subtle` 或 `controlled` 防止失控。
- `Reflections` 要写明"哪个表面"（`water`, `mirror`, `glass`），否则模型随意加倒影。

---

## 四、构图 Framing（画面怎么摆）

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Central Framing` | 居中构图 | `Central framing, subject perfectly centered` |
| `Close-Up` | 特写 | `Extreme close-up on the eyes` |
| `Wide Shot` | 全景 | `Wide establishing shot, subject small in the environment` |
| `Two Shot` | 双人景 | `Two shot, both subjects in frame from waist up` |
| `Over the Shoulder` | 过肩 | `Over-the-shoulder, foreground shoulder soft` |
| `Fourth Wall` | 第四面墙 | `Subject breaks the fourth wall, looks directly at camera` |
| `Voyeur` | 窥视视角 | `Voyeuristic shot, viewed from behind a partially open door` |
| `Silhouette` | 剪影 | `Backlit silhouette, subject is pure black against bright background` |
| `Fisheye` | 鱼眼 | `Fisheye lens, strong barrel distortion` |
| `Interview` | 访谈 | `Interview shot, subject talking to camera, shallow DOF` |
| `Fixed Camera` | 固定机位 | `Fixed camera, no movement, subject enters frame` |
| `Profile Shot` | 侧面 | `Profile shot, seen from the side` |

**AIGC 高频坑：**
- `Central Framing` 适合产品/品牌（主体不动），比"居中"更准。
- `Fisheye` 是**AIGC 强项**，容易出彩；但要写明 `strong barrel distortion, edges curve`。
- `Fourth Wall` 是**互动型短视频**的杀手锏，写 `subject makes eye contact with camera, slight smile`。

---

## 五、风格 Style（整体质感）

### 复古与年代

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `VHS / Vintage` | 复古录像带 | `VHS home video aesthetic, tracking lines, dated overlay` |
| `Halation` | 光晕胶片 | `Kodak halation, soft glow around highlights` |
| `Wigglegram` | 立体照片 | `Wigglegram, lenticular 3D photo effect` |
| `Step-Printing` | 逐帧印 | `Step-printing, time-lapse feel` |

### 风格化视觉

| 术语 | 中文 | AIGC 提示写法 |
|---|---|---|
| `Dreamcore` | 梦境核 | `Dreamcore aesthetic, pastel, surreal, slightly uncanny` |
| `Weirdcore` | 怪异核 | `Weirdcore, unsettling, distorted perspective` |
| `Dystopian` | 反乌托邦 | `Dystopian atmosphere, cold industrial, muted colors` |
| `Maximalism` | 极繁主义 | `Maximalism, dense visual clutter, saturated colors` |
| `Void` | 虚空 | `Void aesthetic, emptiness, floating in space` |
| `Pixel Art` | 像素艺术 | `Pixel art, 8-bit retro style` |
| `Video Game` | 电子游戏 | `Video game aesthetic, third-person camera, HUD` |
| `Mixed Media` | 混合媒介 | `Mixed media, live action blended with 2D animation` |
| `Collage` | 拼贴 | `Collage style, fragmented imagery` |
| `Typography` | 文字排版 | `Kinetic typography, text animating on screen` |
| `Transformation` | 变形 | `Transformation sequence, subject changes form` |
| `Cinemagraph` | 动态照片 | `Cinemagraph, one element moves, rest static` |
| `Shadow Box` | 剪影盒 | `Shadow box, layered papercut aesthetic` |
| `Diorama / Model` | 模型微缩 | `Miniature diorama, tilt-shift, shallow DOF` |
| `Zoetrope` | 走马灯 | `Zoetrope effect, figures rotate on a spinning disc` |
| `Stop Motion` | 定格动画 | `Stop motion animation, 12fps, tactile clay texture` |
| `Generative` | 生成艺术 | `Generative art aesthetic, algorithmic patterns` |
| `Anthropomorphism` | 拟人化 | `Anthropomorphism, object with human behavior` |
| `Object POV` | 物体视角 | `Object POV, seen from the perspective of the object` |
| `Bolt Cam` | 高速快照 | `Bolt cam, multiple rapid stills like a bolt camera` |
| `Choreo` | 编舞 | `Choreographed movement, dancers move in unison` |
| `Conveyor` | 传送带 | `Conveyor effect, scene moves past like on a belt` |
| `Lazy Susan` | 转盘 | `Lazy Susan shot, subject on a rotating platform` |
| `Light Flash` | 光闪 | `Strobing light flash, subject revealed in pulses` |
| `Gesture / Digital Gesture` | 数字手势 | `Digital gesture, hand controls a floating UI` |
| `Floating UI` | 漂浮 UI | `Floating holographic UI, HUD elements in frame` |
| `Set Transition` | 场景转场 | `Set transition, scene changes via a set piece` |
| `Epiphany Shot` | 顿悟 | `Epiphany shot, dramatic realization moment` |
| `Altered State` | 迷幻状态 | `Altered state, distorted reality` |
| `Ultra Wide (Zero-D)` | 超广角 | `Ultra-wide zero distortion, expansive view` |
| `Tilt Shift` | 移轴 | `Tilt shift, miniature effect, extreme DOF` |
| `Underwater` | 水下 | `Underwater shot, light caustics, floating particles` |
| `Probe Lens` | 探针镜头 | `Probe lens macro, extreme close-up on surfaces` |
| `Architexture` | 建筑纹理 | `Architecture as texture, patterned structure fills frame` |
| `Photography` | 摄影质感 | `Documentary photography aesthetic, natural light` |
| `Video Portraits` | 影像肖像 | `Video portrait, subject talking, minimal movement` |
| `Product` | 产品展示 | `Product shot, orbiting, shallow DOF, studio lighting` |

**AIGC 高频坑：**
- `Dreamcore` / `Weirdcore` 是**Z 世代最吃香**的风格，但负面清单要加 `no realistic people, slightly unsettling`.
- `Stop Motion` 要写**帧率**（`12fps`），否则模型做成 24fps 就失去质感。
- `Product` 运镜和 `Central Framing` 是品牌片的黄金组合，务必一起用。
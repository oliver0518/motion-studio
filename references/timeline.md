# 时间轴：时间轴先于代码

把契约变成"第几秒发生什么"的完整时间轴，再写代码。

> 来源：融合 guizang 的镜头表 + motion-design 的 Stage 3（场景行/事件 t 表/T 块）；audio-first 时序 SSOT 与 rate-function 错峰借鉴 HyperFrames / Manim。

## 产出物

1. **场景行**：`start–end s · 名字 · 观众学到什么 · 携带元素进→出 · 转场出`。
2. **事件 t 表**：`t: 元素 · 动作 · 数字 · id`。
3. **T 块**：命名关键时间。
4. **音效 cue 表**：由同一批事件推导。

## 检查（写代码前）

- 拍点落在 60/BPM 的整数倍（密集片每拍一个事件，冷静片每小节一个）。
- 每场景的退出态 = 下一场景的进入态。
- 没有两个动作同时驱动同一属性。
- 一切在结束前完成；循环片 virtual t=D 帧 == 帧 0 且全部静止。

## 双时序范式（选择依据）

| 范式 | 引擎 | 何时用 |
|---|---|---|
| 纯函数帧（frame(N) 是纯函数） | B（Remotion） | 数据驱动、确定性优先、需批量渲染 |
| generator / 编排（顺序推进） | A（GSAP 时间轴） | 手工编排、逐镜头顺序推进 |
| audio-first 游标（外部实测时长驱动全片） | 两者 | 有配音/口播，TTS 重测后自动重定时 |

**audio-first 时序 SSOT**（借鉴 HyperFrames/调研）：TTS 逐句实测时长 → 推总帧数 → 运动层以"父持绝对时间、子为 beat 窗口"实现配音重测后全片自动重定时、零手工对轨。任何需要人工对轨的时间轴都是回归。

## 错峰编排（借鉴 Manim rate function + lag_ratio）

- 每个动画用 **rate function**（缓动族）+ **lag_ratio**（错峰系数）组合：`入场 = EASE.out + lag 0.05s`。
- 一批同类元素入场用错峰而非同时：`sequence(0.15, ...元素)` 或 Manim 的 `lag_ratio`。
- 内容哈希缓存（Manim）：确定性渲染才有资格缓存，帧函数稳定即可复用已渲染段。

## 引擎落地

- 引擎 A：时间只从 `plan.json` 读；GSAP 主时间轴 + `onRender`/`onDrive`。
- 引擎 B：只用 `useTime()` 绝对秒；无 CSS 动画/`Date`/`Math.random`/帧间状态；不用 `<Sequence>` 切场景。

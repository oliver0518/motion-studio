---
name: motion-studio
description: 代码驱动的影片工作室，一个 skill 覆盖两类片——产品宣传片/版本更新片（真实组件 + GSAP/Three.js）与任意主题动效短片（Remotion 确定性渲染）。共享一套「先定方向、写成设计契约、再排时间轴」的方法论，视觉手法从产品/提示词推导、不套模板。触发词：产品宣传片、版本更新片、release notes、changelog promo、产品视频、动效、动态设计、视频、短片、动画、Remotion、motion graphics、showreel、MV、品牌片、宣传片、标题序列、数据故事。
---

# motion-studio 代码驱动影片工作室

一个入口，两类片子，一套方法论，两条渲染引擎。

- **产品宣传片 / 版本更新片**：用真实业务组件讲真实功能 → **引擎 A（真实组件 + GSAP/Three.js）**。
- **任意主题动效短片**：把提示词/主题做成对齐顶级水准的动效片 → **引擎 B（Remotion 确定性渲染）**。
- 两者共用同一套骨架：**定方向 → 设计契约 → 时间轴 → 逐镜头 → 声音 → 审片 → 交付**。

## 术语

| 词 | 含义 |
|---|---|
| 引擎 A | 真实组件引擎：浏览器挂真实业务组件 + GSAP/Three.js。完整说明见 `engine-real-component.md`，起步工程见 `assets/starter/` |
| 引擎 B | Remotion 引擎：React + SVG 纯函数帧，确定性渲染。完整说明见 `engine-remotion.md`，起步工程见 `templates/remotion-starter/` |
| 方向文件 | 引擎 A 的 `DIRECTION.md` / 引擎 B 的 `src/spec.ts`，统一按 `references/direction.md` + `references/design-contract.md` 写 |
| 设计契约 | 把方向写成具体值的合同：palette / type / marks / texture-light / composition / motion / transition / sound / bans |

## Stage 0 — 路由：判定做哪种片、走哪条引擎

先回答三个问题（细则见 `references/engine-router.md`）：

1. **有没有真实仓库/产品，且要求"真实"？** 有 → 引擎 A；没有或不需要 → 引擎 B。
2. **输入是产品还是提示词？** 产品/更新日志/changelog → 偏引擎 A；一段创意/主题/参考 → 引擎 B。
3. **要不要复用真实组件当画面？** 要 → 引擎 A；从零设计元素 → 引擎 B。

| 任务 | 引擎 | 依据 |
|---|---|---|
| 产品宣传片、版本更新片、changelog 视频 | A | 真实功能/组件/设计语言是核心价值 |
| 产品 UI promo，但不想挂真实组件 | B | 用元素 playbook 忠实再现界面 |
| 品牌片、showreel、动态字体、数据故事、MV、角色片、抽象循环、片头 | B | 提示词/主题驱动，无真实产品 |
| 混合（产品片里要高质量装饰动效） | A 为主 + Lottie 通道 | 引擎 A 挂真组件，Lottie 补装饰资产 |

**范围与平台面必须由用户拍板**（全量产品 / 单版本区间 / 哪些平台面：桌面端·CLI·移动端·服务端 API），写进 `plan.json` 的 `scope` 并同步进 BRIEF。

## 共享流程（两条引擎都走）

### Stage 1 — 定方向 → `references/direction.md`
读目标、提炼气质/世界、提 2–3 个方向选一写理由、推导专属手法（"因为产品/主题有 X，所以用 Y"）、反重复。先有方向再写代码。

### Stage 2 — 写设计契约 → `references/design-contract.md` + `references/element-playbooks.md`
把方向写成具体值（不是形容词），逐元素套 playbook，过反 slop 检查（`references/anti-slop.md`）。

### Stage 3 — 排时间轴 → `references/timeline.md`
镜头表/事件 `t` 表/关键时间块/音效 cue；**audio-first 时序 SSOT**；rate function + 错峰编排；时间轴先于代码。

### Stage 4 — 逐镜头搭建（走引擎）
- 引擎 A：按 `engine-real-component.md` 挂真实组件、出静帧、对照镜头表。
- 引擎 B：按 `engine-remotion.md` 写 Remotion 纯函数帧、跑 Design Jury。

### Stage 5 — 声音 → `references/sound.md`
从内容推导配乐/音效，audio-first，混音让位，音画同步。

### Stage 6 — 审片 → `references/review.md`
共享 criteria + 各引擎工具；自动检查只提示，视觉/语义/听感靠实看实听。

### Stage 7 — 交付 → `references/delivery.md`
封面、诚实声明、四道击穿门、量产（batch）。

## 硬约束（两引擎通用）

- **先有方向，再写代码。** 正式片必须有方向文件/设计契约 + 镜头表/时间轴。
- **不套模板。** 每个视觉手法能追溯到产品/主题的某一点；同一工作区连续做片，不复用上一支的开场/章节/背景手法。
- **反 slop。** 禁未经请求的渐变、发光、模板布局、占位文案；`references/anti-slop.md` 是清单。
- **真实优先（引擎 A）。** 正式片至少一项可追溯的真功能主张，记录发布状态与来源。
- **交付诚实。** 说清哪些是自动检查、哪些实看实听、哪些未验证。
- **隔离工程。** 源码适配、展示依赖、构建配置放视频工程，不动原产品代码。
- **授权与来源。** 素材留来源与许可；引擎 A 默认样式受 BSL 约束（见 `COMMERCIAL_LICENSING.md`）。

## 工具入口

```sh
# 引擎 A（真实组件）
python3 <skill-dir>/scripts/init_project.py --output <video-dir> --style repo --repo <repo-dir>
python3 <skill-dir>/scripts/check_environment.py --project <video-dir> --engine browser

# 引擎 B（Remotion）：复制 templates/remotion-starter 后
npm install && npm run studio   # 预览；npm run render 出片；npm run check 自查
```

## 文档索引

- [路由与引擎选择](references/engine-router.md)
- [定方向](references/direction.md) · [设计契约](references/design-contract.md) · [时间轴](references/timeline.md)
- [元素 playbook](references/element-playbooks.md) · [反 slop](references/anti-slop.md)
- [声音](references/sound.md) · [审片](references/review.md) · [交付](references/delivery.md)
- [引擎 A：真实组件](engine-real-component.md) · [引擎 B：Remotion](engine-remotion.md)

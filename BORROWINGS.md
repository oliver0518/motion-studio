# 借鉴地图（BORROWINGS）

本 skill 从两个上游 skill 各取所长，并从 GitHub 开源项目借鉴范式。原则：**借鉴「范式/方法论」，不引入休眠或非 Web 栈的库**；每条借鉴都标注来源。

## 1. 两个上游 skill 的长处与互补

| 上游 skill | 所长（保留） | 短处（由另一方补齐） |
|---|---|---|
| guizang-product-video-skill | 真实功能/组件、产品设计语言（repo/default/hybrid）、三方向选一、专属手法推导、混音让位、封面、`check_delivery` 交付 | 缺「把形容词写成具体值」的设计契约、元素 playbook、评审门 |
| motion-design-prompt-generator | 设计契约、元素 playbook、S/X/E 三账本、真实变换/身份持续、Design Jury、反 slop、Remotion 确定性 | 缺真实组件/真功能、产品设计语言接入、封面交付 |

## 2. 开源项目借鉴（范式级）

| 项目 | 借鉴什么 | 落到本 skill 哪里 | 是否引入库 |
|---|---|---|---|
| HyperFrames（HeyGen 开源，Apache-2.0） | HTML/CSS/JS + GSAP 无头渲染、audio-first 时序 SSOT、agent 原生 | `references/timeline.md` 的 audio-first；引擎 A 参考范式 | 否（范式同源） |
| html-video（Apache-2.0） | `render(input, ctx)` 引擎适配契约、多引擎路由 | `references/engine-router.md` | 否 |
| video-shotcraft（Apache-2.0） | 152 镜头 recipe 卡 + 动效预览 Gallery | 引擎 A 视觉手法词汇的扩展思路 | 否 |
| [Revideo](https://re.video)（MIT） | 服务端 `renderVideo` API、模板/变量批量渲染、webhook 自动化 | `references/delivery.md` 的量产/batch | 否（引擎 B 用 Remotion 等价物） |
| [Manim](https://github.com/ManimCommunity/manim)（MIT） | rate function + `lag_ratio` 错峰编排、`Transform` 点对齐 morph、内容哈希缓存 | `references/timeline.md`、`element-playbooks.md` | 否（非 Web 栈） |
| [Motion Canvas](https://motioncanvas.io)（MIT） | generator / `yield*` 编排范式、scene graph | `references/timeline.md` 的双时序范式 | 否（上游停更，仅范式） |
| [Cavalry](https://cavalry.scenegroup.co) / [Jitter](https://jitter.video) → Lottie | 设计师资产通道（GUI 产 Lottie JSON → 挂进时间轴） | `references/delivery.md` 的 Lottie 通道 | 可选（`@remotion/lottie`） |
| [Rive](https://rive.app)（MIT runtime） | 状态机驱动的交互动画形态 | 备选通道 | 可选（`@remotion/rive`） |

## 3. 否决清单（带理由）

| 项目 | 否决理由 |
|---|---|
| [Theatre.js](https://github.com/theatre-js/theatre) | 停更约两年（npm 0.7.2 / 2024-05），不可托付；仅借鉴「可视化关键帧 → 确定性回放」概念 |
| Motion Canvas 上游 | v3 无 CLI 渲染入口、代码停更 18 个月；仅借鉴 generator 范式 |
| Manim / ManimGL | 非 Web 栈，与两条 Web 引擎零复用；仅借鉴 morph / rate-function 词汇 |
| Spline + `@remotion/spline` | 官方桥已从 npm 除名；整线否决 |

## 4. 主要参考来源

- Remotion vs Motion Canvas vs Revideo 对比（PkgPulse 2026）：https://www.pkgpulse.com/guides/remotion-vs-motion-canvas-vs-revideo-programmatic-video-2026
- 程序化动画引擎能力对比（sparkles 仓库）：https://github.com/PetarKirov/sparkles/blob/main/docs/research/manim/comparison.md
- 视频动效建模与 Web 可视化搭建工具全景调研（Negentropy，2026-09 快照）：https://threefish.site/negentropy/research/video-production/160-video-motion-modeling-web-visual-tooling/
- Rive vs Lottie：https://framer.rive.app/blog/rive-as-a-lottie-alternative

> 注：HyperFrames、html-video、video-shotcraft 的详细信息（星数、许可、维护快照）以上述 Negentropy 全景调研为准；此处不另行外链其仓库，避免陈旧链接。

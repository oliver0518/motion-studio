<p align="center">
  <a href="https://github.com/oliver0518/motion-studio/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-AGPL--3.0-blue.svg" alt="License: AGPL-3.0"></a>
  <img src="https://img.shields.io/badge/Remotion-4.0.537-0b84f3.svg" alt="Remotion">
  <img src="https://img.shields.io/badge/GSAP-3.15.0-0ae448.svg" alt="GSAP">
  <img src="https://img.shields.io/badge/Three.js-0.186.1-000000.svg" alt="Three.js">
  <img src="https://img.shields.io/badge/Playwright-1.58.1-2EAD33.svg" alt="Playwright">
</p>

# motion-studio · 代码驱动影片工作室

**一个 skill，两类影片，两条引擎，一套方法论。** 给 DeepSeek Harness（或任何支持 Agent Skill 的宿主）用的代码驱动制片 skill：

- 🎬 **产品宣传片 / 版本更新片** —— 用**真实业务组件**讲真实功能（引擎 A：真实组件 + GSAP/Three.js）
- ✨ **任意主题动效短片** —— 把一句话创意做成品牌片 / showreel / 数据故事 / MV（引擎 B：Remotion 确定性渲染）
- 🧭 **共享方法论** —— 先定方向 → 写设计契约 → 排时间轴 → 逐镜头 → 声音 → 审片 → 交付

> 由 [guizang-product-video-skill](https://github.com/op7418/guizang-product-video-skill)（真实组件）与 motion-design-prompt-generator（Remotion）两个 skill 融合而成，各取所长、互相补短。

## 🎬 Demo

用本 skill 的引擎 A 制作并渲染的成片（15 秒产品宣传片）：

| 1024 Lounge | 星潮防线 |
|---|---|
| <video src="demos/1024-lounge-15s.mp4" poster="demos/1024-lounge-15s.jpg" controls width="100%"></video> | <video src="demos/xingchao-15s.mp4" poster="demos/xingchao-15s.jpg" controls width="100%"></video> |
| [▶ 在线观看 / 下载](demos/1024-lounge-15s.mp4) | [▶ 在线观看 / 下载](demos/xingchao-15s.mp4) |

## 🚀 快速开始

```sh
# 1. 安装（复制或软链到 skills 目录，目录名即 skill slug）
cp -R motion-studio ~/.dsh/skills/motion-studio
```

```sh
# 2. 重启会话，在 skill 列表看到 motion-studio 后，直接对话即可：

# 产品宣传片（真实组件引擎）
"给 <某个产品> 做一个版本更新片"

# 任意主题动效短片（Remotion 引擎）
"做一个水墨风的品牌动效短片，15 秒"
```

## ✨ 能做什么

| 你想做 | 走哪条引擎 | 一句话说明 |
|---|---|---|
| 产品 / 更新 / changelog 宣传片 | 真实组件 | 把真实界面和真实功能搬进片子，画面即产品 |
| 品牌片 / showreel / MV / 角色片 | Remotion | 从提示词推导风格，逐元素设计、确定性渲染 |
| 数据故事 / 解说片 | Remotion | 图表、计数器、动态字体，按元素 playbook 做 |
| 产品片 + 装饰动效 | 真实组件 + Lottie | 真组件为骨，设计师资产为皮 |

## 🧭 为什么这样合并

两个上游 skill 各有所长、各有短板，本 skill 取长补短：

| 上游 | 所长（保留） | 短处（本 skill 补上） |
|---|---|---|
| guizang（真实组件） | 真实功能/组件/设计语言、三方向选一、专属手法推导、混音让位、封面、`check_delivery` 交付 | 缺"把风格写成具体值"的设计契约、元素 playbook、评审门 → 由 motion-design 补 |
| motion-design（Remotion） | 设计契约方法论、元素 playbook、S/X/E 三账本、真实变换/身份持续、Design Jury、反 slop | 缺"真实性"（真组件/真功能/封面交付）→ 由 guizang 的真实组件引擎补 |

## 📁 目录结构

```
motion-studio/
├── SKILL.md                  # 路由 + 共享流程（skill 入口）
├── README.md                 # 本说明
├── LICENSE                   # AGPL-3.0
├── COMMERCIAL_LICENSING.md   # 许可与商业使用说明
├── engine-real-component.md  # 引擎 A 完整说明书
├── engine-remotion.md        # 引擎 B 完整说明书
├── REFERENCE.md              # Remotion helper API 源码
├── demos/                    # 成片演示（mp4 + 封面 jpg）
├── references/               # 共享层 + 引擎参考
│   ├── engine-router.md      # 引擎选择门
│   ├── direction.md          # 定方向（融合两个上游）
│   ├── design-contract.md    # 设计契约
│   ├── timeline.md           # 时间轴 + audio-first
│   ├── element-playbooks.md  # 元素 playbook
│   ├── anti-slop.md          # 反 slop + 四道击穿门
│   ├── sound.md              # 声音
│   ├── review.md             # 审片（融合两个上游）
│   ├── delivery.md           # 交付
│   └── …（引擎 A 其余参考：repo-and-style / component-pipeline / starter /
│          visual-vocabulary / onboarding / audio-sourcing / audio-and-qa /
│          cover / case-study / story-and-copy）
├── assets/                   # 引擎 A 资产（音效 / 默认样式 / 起步工程 / fx-lab）
├── scripts/                  # 引擎 A 脚本（init / check / mix / sfx …）
├── templates/remotion-starter # 引擎 B 起步工程
├── design-systems/           # 引擎 B 设计种子（7 个）
├── examples/                 # 引擎 B 示例（character-rig / drafting-table）
├── extras/news-video/        # 引擎 A 附带的新闻视频管线
├── tests/                    # 引擎 A 测试
└── .github/                  # Issue / PR 模板
```

## 📦 安装

```sh
# 复制到 skills 目录（本目录名即 skill slug）
cp -R motion-studio ~/.dsh/skills/motion-studio

# 或软链，便于继续改
ln -s "$(pwd)/motion-studio" ~/.dsh/skills/motion-studio
```

安装后重启会话，即可在 skill 列表看到 `motion-studio`。旧的两个 skill 保留不动（本 skill 为增量，可回退、可对比）。

## 📄 许可与来源

- 本 skill 是 `guizang-product-video-skill`（AGPL-3.0）与 `motion-design-prompt-generator` 的派生合并，整体受 **AGPL-3.0** 约束（见 [`LICENSE`](LICENSE)）。
- 引擎 A 的默认样式资产（`assets/fallback/`）受 **BUSL-1.1** 约束，商用见 [`COMMERCIAL_LICENSING.md`](COMMERCIAL_LICENSING.md)。
- 运行时依赖（GSAP、Three.js、Playwright、Remotion、React 等）按各自许可使用，不随本仓库分发其代码。

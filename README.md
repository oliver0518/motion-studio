# motion-studio · 代码驱动影片工作室

一个 skill 覆盖两类片，共享一套方法论，两条渲染引擎。

- **引擎 A · 真实组件**：用真实业务组件讲真实功能（产品宣传片 / 版本更新片 / changelog）。来自 `guizang-product-video-skill`。
- **引擎 B · Remotion**：把提示词/主题做成动效短片（品牌片 / showreel / 数据故事 / MV / 角色片 …）。来自 `motion-design-prompt-generator`。
- **共享层**：定方向 → 设计契约 → 时间轴 → 反 slop → 声音 → 审片 → 交付。两引擎通用。

## 为什么这样合并

两个上游 skill 各有所长、各有短板，本 skill 取长补短：

| 上游 | 所长（保留） | 短处（本 skill 补上） |
|---|---|---|
| guizang（真实组件） | 真实功能/组件/设计语言、三方向选一、专属手法推导、混音让位、封面、`check_delivery` 交付 | 缺"把风格写成具体值"的设计契约、元素 playbook、评审门 → 由 motion-design 补 |
| motion-design（Remotion） | 设计契约方法论、元素 playbook、S/X/E 三账本、真实变换/身份持续、Design Jury、反 slop | 缺"真实性"（真组件/真功能/封面交付）→ 由 guizang 的真实组件引擎补 |


## 目录结构

```
motion-studio/
├── SKILL.md                  # 路由 + 共享流程（skill 入口）
├── README.md                 # 本说明
├── engine-real-component.md  # 引擎 A 完整说明书（原文逐字）
├── engine-remotion.md        # 引擎 B 完整说明书（原文逐字）
├── REFERENCE.md              # Remotion helper API 源码（原文）
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
│          cover / case-study / story-and-copy，逐字保留）
├── assets/                   # 引擎 A 资产（音效 / 默认样式 / 起步工程 / fx-lab）
├── scripts/                  # 引擎 A 脚本（init / check / mix / sfx …）
├── templates/remotion-starter # 引擎 B 起步工程
├── design-systems/           # 引擎 B 设计种子（7 个）
├── examples/                 # 引擎 B 示例（character-rig / drafting-table）
├── extras/news-video/        # 引擎 A 附带的新闻视频管线
└── tests/                    # 引擎 A 测试
```

## 安装

```sh
# 复制到 skills 目录（本目录名即 skill slug）
cp -R motion-studio ~/.dsh/skills/motion-studio

# 或软链，便于继续改
ln -s "$(pwd)/motion-studio" ~/.dsh/skills/motion-studio
```

安装后重启会话，即可在 skill 列表看到 `motion-studio`。旧的两个 skill 保留不动（本 skill 为增量，可回退、可对比）。

## 许可与来源

- 本 skill 是 `guizang-product-video-skill`（AGPL-3.0）与 `motion-design-prompt-generator` 的派生合并，整体受 AGPL-3.0 约束（见 `LICENSE`）。
- 引擎 A 的默认样式资产（`assets/fallback/`）受 BSL 约束，商用见 `COMMERCIAL_LICENSING.md`。

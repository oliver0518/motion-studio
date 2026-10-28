# 许可与商业使用说明

本仓库（motion-studio）是两个 skill 的派生合并，各部分许可需逐项核对。

## 主许可证

本项目整体采用 GNU AGPL-3.0（见 `LICENSE`）。AGPL 允许自由使用、修改、分发，但网络分发与修改后分发须遵守相应条款。

## 各部分许可

| 部分 | 来源 | 许可 |
|---|---|---|
| 引擎 A 说明书、脚本、参考 | guizang-product-video-skill（© op7418） | AGPL-3.0 |
| 引擎 B 说明书、Remotion 模板、设计种子 | motion-design-prompt-generator | 原文未附独立许可证文件 |
| `assets/starter/`（起步工程） | guizang-product-video-skill（© 2026 op7418） | AGPL-3.0，见 `assets/starter/NOTICE.md` |
| `assets/fallback/`（CodePilot 默认样式） | 改编自 CodePilot（© 2025–2026 op7418） | BUSL-1.1 + Additional Use Grant，见 `assets/fallback/LICENSE.CodePilot` |

## 关于 CodePilot 默认样式（BUSL-1.1）

`assets/fallback/` 中的默认样式组件与 tokens 提取/改编自 CodePilot，保留 BUSL-1.1 许可，**不是 MIT，不能当作无限制商用素材**。为其他产品制作或分发影片时，应依据 `LICENSE.CodePilot` 的 Additional Use Grant 判断用途；如需超出该授权的商用，请联系原作者 op7418。

## 第三方依赖

运行时依赖的库（GSAP、Three.js、Playwright、Remotion、React 等）在各自 `package.json` 中声明版本，按各自许可使用，不随本仓库分发其代码。

## 致谢

本 skill 融合自 op7418 的 guizang-product-video-skill 与 motion-design-prompt-generator，并借鉴若干开源项目的范式（见 `BORROWINGS.md`）。各部分的版权与来源声明保留在各自目录的 `NOTICE.md` / `SOURCE.md` / `provenance.json` 中。

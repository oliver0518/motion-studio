# 声音：配乐与音效

从内容推导声音，而非拼贴。

> 来源：融合 guizang 的配乐/音效 + motion-design 的 sound palette；audio-first 见 `timeline.md`。

## 原则

1. **从内容推导**：配乐情绪/音色从产品气质或主题世界推；音效从动作事件推。
2. **audio-first**：有配音时，实测时长驱动全片时间轴（见 `timeline.md`）。
3. **音乐让位**：人声/关键反馈在音乐之上，混音时 duck。
4. **完整声音**：默认音乐 + 独立动作音效都进音轨；用户要静音/省略时记 `audioExceptionReason`。

## 来源优先级

用户提供 → 本机可用的生成模型 → 代码合成。

## 引擎落地

- 引擎 A：`scripts/sfx_landmarks.py` 实测起音点/峰值；`scripts/mix_audio.py` 混音让位；内置 11 个 WAV（`assets/audio/sfx/`）；代码合成配乐示例 `assets/audio/score-example-*.py`。
- 引擎 B：`scripts/cues.json`（pitched bed + figure，或 ambience bed）+ `npm run score`；噪声强调 <1s；无 music 且无 ambience 的 score 拒绝生成。

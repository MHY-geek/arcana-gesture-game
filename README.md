# ARCANA · 手势法师

浏览器里的 3D 手势动作游戏。打开摄像头，用双手击碎迎面飞来的晶体。

**在线试玩：** https://mhy-geek.github.io/arcana-gesture-game/

## 玩法

| 手势 | 效果 |
|---|---|
| ☝️ 快速挥手 | 斩击，指尖划过的晶体被斩碎 |
| ✊ 握拳 → ✋ 张开 | 蓄力后释放冲击波，蓄得越久范围越大 |
| 🤏 捏住 → 甩出 | 隔空抓取晶体，甩出去贯穿其他晶体，得分 ×1.5 |
| 👏 双手合掌 | 能量槽满时释放超新星，清空全场 |

- 前 4 波每波教一个新手势，之后速度逐步提升
- 连击每满 5 次，得分倍率 +0.5（最高 ×4）
- 四类晶体：普通、金色护盾（斩两次或冲击波一击）、分裂、碎片
- 没有摄像头可以用鼠标模式：快速划动 = 斩击，按住空格或右键蓄力，按住左键抓取，`Q` 超新星

## 技术

- Three.js：3D 场景、泛光后处理、GPU 粒子
- MediaPipe Hand Landmarker：实时识别双手 21 个关键点，在浏览器本地运行，画面不上传
- 手势分类基于 3D 世界坐标，指尖轨迹用 One Euro 滤波去抖
- 音效全部由 WebAudio 实时合成
- 单个 HTML 文件，无需构建；所有依赖都放在 `vendor/` 里，不依赖外部 CDN

## 第三方文件

`vendor/` 中的文件原样来自以下项目，各自遵循原许可证：

- [three.js](https://github.com/mrdoob/three.js) r160（MIT，见 `vendor/three/LICENSE`）
- [MediaPipe Tasks Vision](https://github.com/google-ai-edge/mediapipe) 0.10.14 及 Hand Landmarker 模型（Apache-2.0）
- [Orbitron](https://fonts.google.com/specimen/Orbitron) 字体（SIL Open Font License 1.1）

## 本地运行

摄像头需要在 `localhost` 或 HTTPS 下才能使用：

```bash
python3 -m http.server 8765
```

然后打开 http://localhost:8765 。

借助 Claude Code 开发。

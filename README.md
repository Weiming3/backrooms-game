<p align="center">
  <img src="https://img.shields.io/badge/three.js-r128-049ef4?logo=threedotjs" alt="Three.js">
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="license">
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen" alt="PRs welcome">
  <img src="https://img.shields.io/badge/zero--maintenance-yes-brightgreen" alt="zero-maintenance">
</p>

---

<h1 align="center">🌀 Backrooms · 后室</h1>
<p align="center"><strong>3D 第一人称心理恐怖</strong> · 程序化生成 · 零依赖 · 单 HTML 即玩 · 坏了自己修</p>

---

[English](#english) | [中文](#中文)

---

## English

**Backrooms** is a zero-maintenance, vibe-coded 3D first-person psychological horror game. Just one `index.html` — that's the entire project. Three.js loads via CDN. No build tool, no framework, no dependency hell.

### Features

- **Infinite corridors** — wander identical yellow rooms alone
- **Procedural generation** — different layout every time you play
- **Entity AI** — patrol → chase → attack, full state machine
- **Sanity system** — staring at unknown entities drains your mind
- **Immersive audio** — 60Hz ambient hum, spatial footsteps, alert sounds (Web Audio)
- **3 escalating levels** — darker, harder, more entities each level

### Controls

| Key | Action |
|-----|--------|
| `WASD` | Move |
| Mouse | Look |
| `Shift` | Sprint (battery drain) |
| `F` | Flashlight |
| `Esc` | Pause / release mouse |

### How to Run

```bash
git clone https://github.com/Weiming3/backrooms-game
cd backrooms-game
python -m http.server 8080
# → http://localhost:8080
```

> ⚠️ Must use HTTP server. `file://` blocks Pointer Lock API. Needs internet for Three.js CDN on first load.

### Tech

- Three.js r128 via CDN (cdnjs + SRI integrity, no local file needed)
- Web Audio API (60Hz ambient + spatial footsteps + alert tones)
- Canvas 2D procedural textures (walls, floors)
- Single `index.html` → **zero merge conflicts, zero maintenance**

---

## 中文

**后室（Backrooms）** 是个零维护、vibe coding 出品的 3D 第一人称心理恐怖小游戏。就一个 `index.html`，Three.js 走 CDN 加载。不构建、不打包、不管维护。

### 游戏特性

- **无尽走廊** — 一个人在无限延展的黄色房间里游荡
- **程序化生成** — 每次进游戏，地图都不一样
- **实体 AI** — 巡逻 → 追击 → 攻击，完整行为状态机
- **Sanity 理智系统** — 盯着未知实体看太久会掉理智值
- **沉浸音频** — 60Hz 嗡嗡底噪、空间脚步声、警戒音（Web Audio）
- **逐层递进** — Level 0 → 1 → 2，越来越暗、怪物越多

### 操作

| 按键 | 动作 |
|------|------|
| `WASD` | 移动 |
| 鼠标 | 环顾四周 |
| `Shift` | 冲刺（耗电池） |
| `F` | 手电筒 |
| `Esc` | 暂停 / 释放鼠标 |

### 运行

```bash
git clone https://github.com/Weiming3/backrooms-game
cd backrooms-game
python -m http.server 8080
# → http://localhost:8080
```

> ⚠️ 必须 HTTP 服务器。`file://` 下 Pointer Lock 不可用。首次加载需要网络（Three.js CDN）。

### 技术栈

- Three.js r128 CDN 加载（cdnjs + SRI 完整性校验，无需本地文件）
- Web Audio API（60Hz 底噪 + 空间化脚步声 + 警戒音）
- Canvas 2D 程序化纹理（墙壁、地板）
- 单文件 `index.html` → **不可能有合并冲突、不可能有维护负担**

---

### 关于这个项目

> "写个后室游戏" — 我
> "……好" — DeepSeek
>
> 于是就有了这个东西。AI 是 vibe coding + 快速成型机，没用 Behavior Tree 也不用 GOAP，但看起来还挺唬人的。手电筒电量、Sanity 值、脚步声——这些后室经典元素都有了。
>
> 项目太大了。代码谈不上优雅，能跑就行。🤷

---

### Tweak it

想自己改？直接编辑 `index.html` 搜这些变量就行：

| 参数 | 作用 | 位置 |
|------|------|------|
| `TILE` `GRID_W` `GRID_H` | 地图格大小 | 顶部 |
| `state.health` `state.sanity` | 初始血量/理智 | 顶部 |
| `flickerSpeed` | 手电筒闪烁速度 | 约 L300 |
| `numRooms = 8 + levelNum * 2` | 每层房间数 | 约 L480 |

---

MIT · 随便用。

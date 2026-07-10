# Backrooms — 后室

一个基于 Three.js 的第一人称后室探索网页游戏。纯前端，无后端，无数据收集。

## 隐私与安全

- **无网络请求**：游戏运行后无任何 `fetch` / `XMLHttpRequest` / `WebSocket`
- **无设备权限**：不申请麦克风、摄像头、地理位置等权限
- **无数据收集**：没有分析、没有遥测、没有第三方追踪脚本
- **无本地存储**：不使用 cookie / localStorage / sessionStorage
- **CDN SRI 校验**：第三方脚本使用 SHA-384 Subresource Integrity 校验，防止 CDN 篡改
- **纯单文件**：`index.html` 自包含，可离线运行（除首次加载 CDN 外）

## 运行方式

由于浏览器 ES Module / SharedArrayBuffer 等限制，必须通过 HTTP 服务器运行（`file://` 协议下 PointerLockControls 不可用）。

```bash
cd backrooms-game
python -m http.server 8080
# 浏览器打开 http://localhost:8080
```

## 操作

| 按键 | 操作 |
|------|------|
| WASD | 移动 |
| 鼠标 | 环顾四周 |
| Shift | 奔跑（消耗电池） |
| 点击 | 锁定鼠标指针 / 重新锁定 |

## 游戏内容

- **Level 0 — 大堂**：经典的黄色壁纸、荧光灯、潮湿地毯
- **Level 1 — 仓库**：工业风格，更暗的通道
- **Level 2 — 管道**：狭窄走廊，红色应急照明

### 核心机制

- **探索**：程序化生成的房间和走廊，每次进入新层级都不同
- **实体**：后室中的生物会在房间中巡逻，发现你后会追逐
- **理智值**：实体靠近时理智下降，屏幕产生扭曲效果；远离后缓慢恢复
- **手电筒**：自动跟随视角，奔跑会消耗电池
- **层级切换**：找到发光的暗色门洞即可进入下一层
- **死亡**：被实体攻击会损失生命值，归零后游戏结束

### 氛围系统

- 60Hz 荧光灯嗡嗡声（Web Audio API 合成）
- 脚步音效
- 灯光闪烁效果
- 低理智时画面抖动 + 畸变
- 层级切换时的视觉过渡

## 技术栈

- **Three.js r160** — 3D 渲染
- **PointerLockControls** — 第一人称控制
- **Web Audio API** — 程序化音频
- **Canvas 2D** — 程序化纹理（壁纸、地毯、天花板）

## 文件结构

```
backrooms-game/
├── index.html    # 单文件游戏（所有代码内联）
└── README.md     # 本文件
```

## 许可

MIT
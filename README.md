# Backrooms · 后室

> "写个后室游戏"
> — 我
> 
> "……好"
> — DeepSeek

于是就有了这玩意儿。

## 它能干啥

- 在黄色迷宫里乱逛
- 被不明生物追
- 找发光的门洞换关卡
- 听滋滋啦啦的灯管嗡鸣

Level 0 → 1 → 2 循环往复。3 个层级，每层程序化生成，每次进去都不一样。

## 怎么玩

```bash
cd backrooms-game
python -m http.server 8080
# 浏览器开 http://localhost:8080
```

> ⚠️ 必须用 HTTP 服务，不能直接 file:// 打开（PointerLockControls 会罢工）。

进入后：

- `WASD` 走路
- `Shift` 跑（耗电池）
- 鼠标 = 眼珠子
- 找到那个发橙光的洞 → 进去下一层

## 技术栈

- Three.js r128（从 CDN，SRI 校验过）
- 原生 Web Audio（60Hz 嗡鸣器 + 噪声）
- 程序化纹理（Canvas 2D 画出来的）
- 没有框架没有打包工具没有依赖管理

## 关于这个项目


怪物 AI 是瞎写的巡逻 + 追逐状态机，没用 Behavior Tree 也没用 GOAP，但看起来挺唬人。手电筒电量、理智值、脚步声——这些 Backrooms 元素都齐了。

如果想改参数直接编辑 `index.html`：

- `TILE`、`GRID_W`、`GRID_H` → 地图大小
- `state.health` / `state.sanity` → 初始血量理智
- `flickerSpeed` → 灯管闪烁频率
- `numRooms = 8 + levelNum * 2` → 每层房间数

## License

MIT。随便用。

---

*Made by vibe coding. 🟡*

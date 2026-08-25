# Open Micro Kbd — $40 开源 AI 宏键盘

- 官网：<https://openmicrokbd.org/>
- 仓库：<https://github.com/conol-ai/openmicrokbd>（MIT）
- 一句话：13 键 + 旋钮 + 摇杆 + 触控板的开源宏键盘，成本不到 $40，为指挥 AI Agent 而生——硬件、固件、软件全开放。

## 硬件规格

| 项目 | 参数 |
|---|---|
| 按键 | 13 键（低轴 Choc V2 线性，安静） |
| 旋钮 | 1 个编码器（默认调 AI 推理力度；不聊 AI 时是音量轮） |
| 摇杆 | 模拟摇杆（移鼠标/方向键/达芬奇调色，按下循环模式） |
| 触控板 | 圆形金色触控板（点按已用，两个滑动槽位预留） |
| 灯光 | 21 颗 RGB（13 每键 + 8 底光） |
| 主控 | STM32F072，Rust 固件（embassy） |
| 更新 | 配置 App 里 USB 一键刷固件 |

## 为 AI 设计的按键

- **语音键**：按住说话，松开即整段转写发给 Agent（免打字 prompt）
- **旋钮**：左快答 ↔ 右深度思考，调推理力度
- **多任务键**：每个后台 Agent 一个键，轻点切换，工作不停
- **权限键**：Agent 请求权限时一按直达待审内容，不用翻终端
- **宏键**：把重复仪式（add → commit → build → test → push）压成一按
- **全可改**：24 个键位槽 + 配置文件（profile），配置 App 实时写入板子

兼容任何吃键盘输入的 AI（Claude Code、Codex、Conol…），也能用于 Premiere、达芬奇、Lightroom、游戏。

## 技术架构（全开放）

```
openmicrokbd/
├─ hw/v1/src/    原理图用 CoHDL 写成（"PCB 即程序"，编译器检查）
├─ hw/v1/out/    编译产物：网表、BOM、封装、布局约束
├─ hw/v1/pcb/    布好线的板子（KiCad 可开）
├─ hw/v1/fab/    Gerber/BOM/贴片文件，直接传工厂
├─ fw/           Rust 固件（embassy）：键阵、双 RGB 链、USB HID
└─ app/          配置 App：Rust + GPUI（macOS 官方签名包；Win/Linux 源码编译）
```

- 背后故事：对标某公司 $230 的闭源 Codex 键盘，"你买它但不拥有它"；Open Micro Kbd 反其道——克隆、改造、售卖都行
- CoHDL 语言与编译器同样开源：<https://cohdl.org/>
- 成本：料件 <$40 + 一个下午手工

# Omarchy 中文社区资源一页纸

> 整理自 Omarchy 中文社区分享的精选资源，供人和 AI 快速阅读。
> 详细笔记见 [`resources/`](resources/) 目录。整理日期：2026-08-25

## Omarchy 是什么

[Omarchy](https://omarchy.org) 是 DHH（Ruby on Rails 作者）打造的 **Arch Linux + Hyprland** 开箱即用桌面环境：一条命令安装，自带调校好的快捷键、主题、工作流。
上游仓库：<https://github.com/basecamp/omarchy>

## 资源总览

| 资源 | 类型 | 一句话简介 |
|---|---|---|
| [Omarchy Mac](https://github.com/omarchy-mac/omarchy-mac) | 系统分支 | Apple Silicon（M1/M2）一条命令装 Omarchy 4：Asahi Alarm + 全盘加密，与 macOS 共存（1.1k★） |
| [omarchy-rs](https://github.com/Omarchy-rs/omarchy-rs) | 性能增强 | Omarchy 用户态工具的 Rust 加速层：Agent 用量统计、工作区清理、技能管理、Learn 书架，可一键回滚 |
| [OmaPilot](https://github.com/spencerbull/omarchy-omapilot) | AI 插件 | 顶栏 AI 助手：语音对话、截屏问答、桌面上下文、邮件/日历/Basecamp/Signal 连接器，可移交 Herdr 续聊 |
| [Open Micro Kbd](https://openmicrokbd.org/) | 开源硬件 | 不到 $40 的 13 键 AI 宏键盘：旋钮调推理力度、摇杆、语音键、权限键，原理图即代码（[GitHub](https://github.com/conol-ai/openmicrokbd)） |
| [Zonda Zoom 主题](https://github.com/dhh/omarchy-zonda-zoom-theme) | 官方主题 | DHH 出品，帕加尼 Zonda HH 灵感的碳黑 + 冰蓝配色 |
| 实用功能速查表 | 速查表 | 13 类高频 `omarchy` 命令，图片转文字版见 [resources/cheat-sheet-commands.md](resources/cheat-sheet-commands.md) |

## 高频命令速查

```bash
 omarchy menu keybindings                  # 快捷键总览（新手先看这个）
 omarchy update                            # 更新系统
 omarchy commands                          # 全部命令总览
 omarchy theme list / theme set <name>     # 主题（同步 Hyprland/状态栏/终端/GTK/锁屏）
 omarchy capture screenshot region copy    # 区域截图进剪贴板
 omarchy capture text                      # OCR 提取文字
 omarchy install dev-env <语言>             # 开发环境：node/python/rust/go/ruby…
 omarchy default browser firefox           # 切默认应用（editor / terminal 同理）
 omarchy launch webapp <URL>               # 把网站变成独立桌面 App
 omarchy launch or focus <app>             # 未运行则启动，已运行则聚焦
```

**学习路线**：快捷键 → 工作区 → 剪贴板 → 截图/OCR → 主题
**注意**：`omarchy refresh shell` 会先备份（`.bak.时间戳`）再覆盖相应用户配置。
以上命令已逐条对照[官方手册](https://omarchy.org/manual/)与上游 [basecamp/omarchy](https://github.com/basecamp/omarchy) quattro 分支源码核验（2026-08）。

## 群友常用软件

- [Tailscale](https://tailscale.com/) — 零配置 WireGuard 组网，随时随地安全连回自己的 Omarchy 机器。官方已内置：`omarchy install service tailscale`。

## Apple Silicon 安装速记

```bash
# 1. macOS 终端运行 Asahi Alarm 安装器，选 "Asahi Alarm Minimal (BTRFS)"，分 ≥50GB
curl https://asahi-alarm.org/installer-bootstrap.sh | sh
# 2. 重启进 Arch（root / root），nmtui 连 WiFi
# 3. 一条命令装完 Omarchy 4（约 15 分钟、3 次重启，默认全盘加密）
curl -fsSL https://raw.githubusercontent.com/omarchy-mac/omarchy-mac/quattro/bin/omarchy-mac-setup | bash
```

普通 x86 机器直接用官方安装器：<https://omarchy.org>

## 详细笔记索引

| 文件 | 内容 |
|---|---|
| [resources/cheat-sheet-commands.md](resources/cheat-sheet-commands.md) | 速查表完整文字版（13 类命令 + 学习路线） |
| [resources/omarchy-mac.md](resources/omarchy-mac.md) | Apple Silicon 安装步骤、参数、排障 |
| [resources/omarchy-rs.md](resources/omarchy-rs.md) | Rust 加速层组件、安装与回滚 |
| [resources/omapilot.md](resources/omapilot.md) | AI 助手插件：功能、快捷键、安全模型 |
| [resources/openmicrokbd.md](resources/openmicrokbd.md) | 开源宏键盘：按键功能、技术架构 |
| [resources/theme-zonda-zoom.md](resources/theme-zonda-zoom.md) | 主题安装与完整配色 |
| [resources/The-Tao-of-DHH.pdf](resources/The-Tao-of-DHH.pdf) | 《The Tao of DHH》原书 PDF |

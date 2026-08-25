# Omarchy 实用功能速查表（文字版）

> 来源：微信群分享图片《Omarchy Linux 实用功能速查 — Arch Linux × Hyprland 高效桌面工作流》。
> 所有命令均为 Omarchy 4（Quattro）的 `omarchy` CLI。

## 01 窗口与工作区

自动平铺 / 快速切换 / 浮动、全屏；dwindle 瓦片布局 / 滚动布局。

```bash
omarchy menu keybindings
```

## 02 快捷菜单

应用启动 / 剪贴板历史 / Emoji / Wi-Fi / 蓝牙 / 音频。

```bash
omarchy menu clipboard
omarchy menu emoji
```

## 03 截图与识别

区域 / 窗口 / 全屏截图、录屏、OCR 文字识别、二维码识别。

```bash
omarchy capture screenshot region copy
omarchy capture text
omarchy capture qr
```

提示：`capture qr` 的解码结果只进剪贴板，且被标记为敏感内容、不会进入剪贴板历史（二维码常含密钥）。

## 04 主题与字体

一键同步 Hyprland、状态栏、终端、编辑器、GTK、锁屏。

```bash
omarchy theme list          # 列出可用主题
omarchy theme set <name>    # 应用主题
omarchy theme --help
omarchy font list
```

## 05 开发环境

Node / Python / Rust / Go / Ruby / Docker / 编辑器。

```bash
omarchy install dev-env <语言>
```

## 06 默认应用

统一切换浏览器、编辑器、终端。

```bash
omarchy default browser firefox
omarchy default editor nvim
omarchy default terminal ghostty
```

## 07 Web App

把网站作为独立桌面应用运行。

```bash
omarchy launch webapp <URL>
```

## 08 智能启动

未运行则启动，已运行则聚焦。

```bash
omarchy launch or focus <app>
```

## 09 状态栏与插件

位置、透明度、组件、插件管理。

```bash
omarchy bar position bottom
omarchy bar transparent toggle
```

## 10 音频与显示

切换输出、屏幕亮度、文字缩放、键盘背光。

```bash
omarchy audio output switch
omarchy brightness display +10%
```

## 11 夜间与锁屏

夜间色温、自动锁屏、休眠。

```bash
omarchy toggle nightlight
omarchy system lock
```

## 12 临时提醒

轻量定时通知。

```bash
omarchy reminder 15 "检查烤箱"
```

## 13 系统维护

更新、版本、命令总览、配置恢复。

```bash
omarchy update
omarchy commands
omarchy refresh shell
```

## 优先掌握

快捷键 → 工作区 → 剪贴板 → 截图/OCR → 主题

## 注意

`omarchy refresh shell` 会先备份（`*.bak.<时间戳>`）再覆盖相应用户配置。

## 核验说明

以上全部命令已逐条对照官方手册（omarchy.org/manual，2026-08）与上游 basecamp/omarchy `quattro` 分支 `bin/` 源码核验，均为有效命令。

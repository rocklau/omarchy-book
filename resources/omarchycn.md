# OmarchyCN — 面向中国开发者的 Omarchy 下游发行版

- 仓库：<https://git.zacharyzhang.com/ZacharyZhang-NY/omarchycn>（基于 basecamp/omarchy `quattro` 基线，MIT）
- 一句话：完整保留 Omarchy 的 Arch + Hyprland 桌面体验，为中国网络环境、中文使用习惯与国内 AI 服务做系统级增强的下游社区发行版。
- 当前版本：`4.0.0.alpha-cn` 系列（alpha 阶段）

## 特性亮点

继承自 Omarchy：

- Hyprland 动态平铺桌面 + Quickshell 顶栏/菜单/系统面板，键盘驱动工作流
- `omarchy` CLI 与 `Super + Space` 系统菜单，CLI 与 GUI 同构
- 内置主题系统一键换肤；Btrfs + Snapper 更新前快照与系统回滚
- AI coding agent 桌面集成（Claude Code、Codex、OpenCode 等）

OmarchyCN 新增（中国本地化层）：

- **中国镜像管理**：Arch / npm / pip / Cargo / Go 等软件源测速、自动选择与故障切换
- **中文环境开箱即用**：zh_CN locale、思源黑体/宋体字体栈、高分屏分数缩放预设
- **中文输入法**：Fcitx5 + Rime 预配置，Wayland / GTK / Qt / Electron 全栈兼容，快捷键冲突自动处理
- **AI Hub**：Kimi、DeepSeek、Z.AI/GLM 一等 Provider 支持，与 Claude Code、Codex、OpenCode、Kimi Code 等 Harness 的统一配置向导、凭据安全存储与连接诊断
- **国内应用中心**：微信、QQ、飞书、钉钉、腾讯会议、WPS 等的可信安装入口
- **Overlay 安装器**：在现有 Omarchy 上叠加 OmarchyCN，全程可逆、可卸载
- **统一诊断**：`omarchycn doctor` 覆盖网络、镜像、输入法、显示与 AI 配置

## 安装

1. 从 [Releases](https://git.zacharyzhang.com/ZacharyZhang-NY/omarchycn/releases) 页面下载 ISO 与 `SHA256SUMS.txt`
2. 校验并写入 U 盘：
   ```bash
   sha256sum -c SHA256SUMS.txt
   ```
3. U 盘 UEFI 启动，按安装器引导完成安装

已有 Omarchy 用户可用 Overlay 安装器叠加，不必重装。

## 声明

- 独立社区发行版，与 Basecamp / 37signals / Omarchy 官方无隶属或背书关系
- 代码沿用上游 [MIT License](https://git.zacharyzhang.com/ZacharyZhang-NY/omarchycn/src/branch/quattro/LICENSE)，保留 Omarchy 原始版权声明

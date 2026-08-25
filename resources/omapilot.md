# OmaPilot — Omarchy 顶栏 AI 助手插件

- 仓库：<https://github.com/spencerbull/omarchy-omapilot>（MIT，插件 ID `io.github.spencerbull.omapilot`）
- 一句话：Omarchy Quattro 原生顶栏小组件 + AI 问答面板——语音/打字对话、截屏提问、桌面上下文、应用连接器，聊完可移交 Herdr 继续。

## 核心功能

- 总结当前活动窗口、联网查资料
- 十字准星截取窗口或精确区域提问（装 Tesseract 可自动提取点击处文字）
- 环境语音（ambient voice）：平时隐藏，有料才出现
- 结果面板：Markdown、代码块、表格、图片、历史（保留最近 30 条完整对话）、Continue in Herdr
- 最多 5 个自定义快捷动作

## 安装

```bash
omarchy plugin add https://github.com/spencerbull/omarchy-omapilot.git
omarchy plugin validate ~/.config/omarchy/plugins/io.github.spencerbull.omapilot
omarchy plugin enable io.github.spencerbull.omapilot right
```

安装不改动 Hyprland 配置；全局快捷键需在 **Settings → Desktop → Install global hotkeys** 显式安装。

## 快捷键（安装后）

| 键 | 作用 |
|---|---|
| `Super + A` | 语音对话（流程关闭则新开；进行中则续说/结束听写） |
| `Super + Shift + A` | 强制新开语音对话 |
| `Super + Alt + X` | 取消语音模式 |
| `Super + Alt + N` | 新开打字对话 |
| `Super + Alt + H` | 把当前对话移交 Herdr |

## AI 后端（Harness，三选一）

- **Built-in (OmaPilot)**：基于 Pi 运行时，支持 Codex 订阅、OpenAI API、Grok、OpenAI 兼容端点；带结构化桌面工具（应用/窗口/工作区/显示器控制，走审批）
- **Codex ACP** / **OpenCode ACP**：需已安装并登录；权限策略各自独立，OmaPilot 只做归一化展示，绝不绕过任何 harness 的权限系统

## 能力连接器（Settings → Skills）

- Email / Calendar：HEY（`hey-cli`）
- Files：仅限用户指定的一个根目录
- Projects：Basecamp 官方 CLI
- Messages：Signal（仅限本机回环 API）
- Meetings：打开精确的 `zoom.us` 链接

读操作返回有界、标记为"不可信"的数据；**写操作永远需要当次人工确认**（会话授权/持久授权/危险自动批准都不覆盖）。

## 语音与集成（可选）

- TTS：ElevenLabs（引导默认，需 API key）/ Kokoro（本地）/ OpenAI
- 听写：Voxtype
- 浏览器增强：OmaPilot Browser Companion 扩展（Chromium/Firefox，按站点显式启用，可语义截取页面元素）

## 隐私要点

- 只持久化"已完成的对话"（≤30 条）；不存草稿、令牌、凭据、原始工具请求
- 桌面上下文默认只带：活动窗口 app/标题/工作区/显示器 + 最多 12 个打开应用 + MPRIS 正在播放信息；不碰剪贴板、历史、隐藏标签页、键盘输入
- 密码管理器类窗口一律禁止截取

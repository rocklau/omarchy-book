# omarchy-rs — Omarchy 的 Rust 用户态加速层

- 仓库：<https://github.com/Omarchy-rs/omarchy-rs>（MIT）
- 一句话：用 Rust 重写 Omarchy 部分用户态工具的热路径（减少进程创建、解析开销、重复 I/O），**可逆、不接管官方文件**，上游实现始终保留为回退。

## 设计原则

- 只移植"实测有收益"的热路径
- 保持原 CLI 与文件格式行为不变
- 每个替换可独立禁用；overlay 装在 `~/.local/share/omarchy-rs`，不碰 Omarchy 包自带的文件

## 安装

```bash
cargo install omarchy-rs
omarchy-rs usage doctor      # 体检
omarchy-rs install           # 安装用户 overlay（提供短命令 omrs，二者同一二进制）
omarchy-rs usage activate
omarchy-rs usage status
```

一键回滚到官方命令：`omrs usage rollback`

## 组件一览

| 组件 | 作用 |
|---|---|
| **Agent Usage** | AI Agent 用量统计 overlay，Rust 原生采集器支持 Codex、Claude Code、Octoscode、Grok（Grok 为原生新增）；Python 采集器保留为回退，面板显示 `collectorBackend` 来源 |
| **Workspace Cleaner** | 工作区清理：默认扫 `~/Work`，只识别项目验证过的 Rust/Node 构建产物；顶栏"扫把"插件，超过阈值（默认 400GiB）才高亮；删除前必须生成确认计划并二次确认 |
| **Local Skill Manager** | 把 `~/.agents/skills` 当便携源，展示在 Claude Code / Codex / Grok / Octoscode 的激活情况；不读技能正文与凭据 |
| **Learn Books** | 自定义 Learn 书架 + Agent 单章翻译（Codex/Claude/Grok）、静态书籍离线快照、每日 AI/Rust 简报（定时刷新进菜单） |
| **Crash Inbox** | 把错过的 systemd-coredump 事件做成顶栏徽标，只存已确认的事件 ID；点 Diagnose 才调 `omarchy agent crash PID` |
| **rust-lang 主题** | 附赠 Rust 风格 Omarchy 主题（含原创 4K Rust Forge 壁纸），以用户主题安装 |

## 常用命令示例

```bash
omrs doctor
omrs learn books --json
omrs cleaner scan --root ~/Work --json
omarchy-rs cleaner install-plugin && omarchy plugin enable omarchy-rs.cleaner
omarchy-rs skills install-plugin && omarchy plugin enable omarchy-rs.skills
omrs learn ai-info configure --agent codex --time 08:00 --topics ai,rust --limit 10
```

## 工程文档

架构、兼容性模型、基准策略、依赖策略、路线图均在仓库 `docs/`；机器可读的需求与决策在 `knowledge/`（用 `agent-spec` 校验）。

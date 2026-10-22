# ibara：让 Agent 在备用 Omarchy 电脑上完成第一个任务

ibara 为现有 Agent 提供你所拥有电脑的浏览器和桌面应用访问能力。Agent 在备用电脑上操作，你可以在自己的电脑上继续工作，并通过 ibara 控制台观看或接管。模型仍使用你现有 Agent 的配置，备用电脑负责运行桌面和应用。

这份指南先用一个无需登录的练习页面检查完整流程，再把同样的方法用于自己的测试应用。ibara 免费、开源；这里的任务不需要购买安装服务。

## 开始前

- 按 [ibara 当前要求](https://ibara.app/docs/requirements)确认系统和电脑适用。准备已安装 ibara、完成配对的 Omarchy 电脑，以及已连接 MCP 的 Agent。
- 两台电脑能通过 Tailscale 通信；备用电脑已开机、登录桌面并解锁。
- 尚未完成配置时，先看[安装与配对](https://ibara.app/docs/install)和[连接 Agent](https://ibara.app/docs/agents)。不要把安装成功或 MCP 已连接当作桌面任务已经成功。
- 若使用 Hyprland 输入插件，键盘布局需要 English (US)，关闭 Caps Lock 并释放按住的键。相关限制见[输入排障](https://ibara.app/docs/troubleshooting#keys)。

本指南沿用 ibara 当前的 Omarchy 支持范围，不据此推断 OmarchyCN、Apple Silicon 或其他系统已获得验证。控制台按钮保留英文名称，便于对照实际界面。

## 1. 给 Agent 一个明确任务

将下面的 `spare-mini` 换成已配对的备用电脑名称。英文提示词与官方首次任务指南一致；给 Agent 的提示词不必与本说明使用同一种语言。

```text
On spare-mini, open https://ibara.app/practice and check the Settings menu with the mouse and the keyboard. Take a screenshot and tell me what worked. Don’t change system settings.
```

练习页面的 Settings 菜单支持鼠标、Tab、Enter、Space、方向键和 Escape。任务不需要账号，也不需要提交真实数据。

## 2. 观看，或临时接管

右键点击顶栏的 ibara 图标，打开控制台并选择备用电脑。需要亲自操作时选择 **Take Control**。完成后选择 **Hand Back**；如果任务还没结束，再让 Agent 继续。不要假设交还控制权会自动恢复旧任务。

## 3. 检查结果

完成后确认：

1. Agent 逐项说明哪些检查通过、哪些失败，未测试的项目明确写出。
2. 至少有一张截图显示菜单已打开。
3. 任务结束时关闭本任务打开的窗口，释放对备用电脑的控制。

如果只有“已执行点击”或“任务完成”一句话，继续索要实际结果。工具接受输入和页面达到预期状态需要分别检查。

卡住时先区分问题发生在哪一步：电脑无法到达、MCP 未连接、浏览器未打开，还是菜单交互失败。把具体错误和预期行为记下来，再看[排障指南](https://ibara.app/docs/troubleshooting)。不要为了重试而反复重装、修改网络或扩大权限。

## 4. 换成自己的有用任务

练习成功后，选择自己拥有的测试应用中的一个小流程，说明预期结果、不要碰什么，以及需要哪些截图。例如用鼠标修改一个测试设置、保存并重新加载，再用键盘完成同样的检查。

备用电脑必须能访问测试应用的地址。使用合适的测试站点或 tailnet 地址；你自己电脑上的 `localhost` 指向它自己，备用电脑上的 `localhost` 则指向备用电脑。具体示例见[官方首次任务指南](https://ibara.app/docs/first-task#your-app)。

也可以试试[原生编辑器任务](https://gist.github.com/MayberryDT/3442e212b32d1b07896c842256d56dc8)：编辑虚构清单、保存、关闭并重新打开，再实际收取文件。该示例记录的是维护者的内部测试，不是独立用户使用报告。

---

资料核对：2026-10-22。本文由与 ibara 维护者合作的 AI 助手整理，依据上面链接的官方说明和已有任务记录；没有额外声称本地化界面、中文输入法兼容性或新的客户端测试结果。项目源码：[MayberryDT/ibara](https://github.com/MayberryDT/ibara)。

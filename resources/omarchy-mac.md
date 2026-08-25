# Omarchy Mac — Apple Silicon 上的 Omarchy 4

- 仓库：<https://github.com/omarchy-mac/omarchy-mac>（fork 自 basecamp/omarchy，1.1k★，MIT）
- 一句话：在 Apple Silicon（M1/M2 系列）Mac 上，通过 Asahi Alarm 一条命令安装 Omarchy 4，含全盘加密，可与 macOS 共存。

## 安装前检查

- macOS 已有近期备份（Time Machine 等）
- Apple Silicon Mac（M1/M2 家族），确认设备支持：<https://asahilinux.org/fedora/#device-support>
- 内置 SSD 至少 50GB 空闲（推荐 100GB）
- 可联网

## 三步安装

```bash
# 1. 在 macOS 终端运行 Asahi Alarm 安装器
#    选择 "Asahi Alarm Minimal (BTRFS)"，为 Linux 分 ≥50GB
curl https://asahi-alarm.org/installer-bootstrap.sh | sh

# 2. 重启进入 Arch，用 root/root 登录，连网（一切从下载开始）
nmtui

# 3. 一条命令安装（仍是 root）
curl -fsSL https://raw.githubusercontent.com/omarchy-mac/omarchy-mac/quattro/bin/omarchy-mac-setup | bash
```

无需预装 pacman 更新、locale、用户——脚本自己搞定用户创建和 sudo。

## 预期过程

- 约 15 分钟，3 次重启，中途只问两件事：
  - **gum 弹窗**：是否编译无 aarch64 预编译包的软件 → 选 **No**（默认即 No，obs-studio 会编译 3 小时然后失败）
  - **磁盘加密口令**：在控制台输入；加密约 1 GiB/s（M2 Max），可安全中断、下次开机续跑
- 加密机器之后直接登录桌面：开机口令即认证，无需再输一次

## 常用参数

| 参数 | 作用 |
|---|---|
| `--no-encrypt` | 跳过全盘加密及所需的开机分区迁移 |
| `--repo <owner/repo>` | 从 fork 安装 |
| `--status` | 查看安装进行到哪一步 |
| `--step <name>` | 单独重跑某一步 |
| `--abort` | 停止引导式安装（不回滚已做操作） |
| `OMARCHY_TRY_UNAVAILABLE=1 bash install.sh` | 手动安装时强制尝试无 ARM 包的软件 |

## 分支注意

- 默认分支 `quattro` = Omarchy 4.x（安装脚本默认装这个，会校验版本）
- `main` 分支仍是 Omarchy 3.x——手动 clone 安装前先 `cat version` 确认
- 3.x 升级 4.x 见仓库 `docs/upgrade-to-quattro.md`

## 排障速查

| 症状 | 处理 |
|---|---|
| 装完后 SSH 连不上 | 默认防火墙全拒绝且未开 22 端口：`omarchy-setup-security-sshd`（或菜单 Setup → Security → SSH） |
| 开机进 `grub rescue>` | `/boot` 必须先迁到 EFI 分区再加密，见仓库 `docs/btrfs.md` |
| 更新出问题想回滚 | `omarchy snapshot restore`（含 `@fresh`、`@factory` 快照） |
| 镜像源慢/失败 | 仓库根目录运行 `bash fix-mirrors.sh` |

> 快照说明：官方手册的快照恢复走 **Limine** 引导菜单（命令为 `omarchy-snapshot restore`，仅 Limine 可用、只恢复 root 不含 `/home`）。omarchy-mac fork 用 GRUB + snapper，在 Apple Silicon 上提供了自己的 `omarchy snapshot restore`，二者不要混淆。

## 其他

- 卸载：无自动卸载器，按 [Asahi 分区速查表](https://asahilinux.org/docs/sw/partitioning-cheatsheet/) 从 macOS 删除 Linux 分区（认准分区，别动错 macOS）
- Discord：<https://discord.gg/KNQRk7dMzy>
- 更多文档：仓库 `manual/`（Omarchy 手册）、`docs/btrfs.md`（快照与加密）

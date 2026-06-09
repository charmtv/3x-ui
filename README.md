# 3X-UI

3X-UI 是基于 Xray-core 的网页管理面板，用于部署、配置和维护代理服务。项目提供一键安装脚本、中文管理菜单、客户端管理、流量统计、证书管理和数据库配置能力，适合在个人服务器上快速搭建和维护节点。

> 本项目仅供合法授权的个人学习与自用，请勿用于任何非法用途。

## 主要功能

- 管理多种入站协议：VLESS、VMess、Trojan、Shadowsocks、WireGuard、Hysteria2 等。
- 管理客户端：流量额度、到期时间、IP 限制、在线状态、订阅链接和二维码。
- 支持常用传输与安全配置：TCP、WebSocket、gRPC、HTTPUpgrade、XHTTP、TLS、XTLS、REALITY。
- 支持证书管理：域名证书、IP 证书、自定义证书和 Cloudflare DNS 签发。
- 支持流量统计、日志查看、地理文件更新、Fail2ban 和防火墙辅助管理。
- 支持 SQLite 和 PostgreSQL，两种数据库可在安装或迁移时选择。
- 安装脚本和管理菜单使用简体中文交互。

## 快速安装

```bash
bash <(curl -Ls https://raw.githubusercontent.com/charmtv/3x-ui/main/install.sh)
```

安装完成后，脚本会生成随机用户名、密码和访问路径。请妥善保存安装结果，并运行以下命令打开管理菜单：

```bash
x-ui
```

## 常用命令

```bash
x-ui              # 打开管理菜单
x-ui start        # 启动服务
x-ui stop         # 停止服务
x-ui restart      # 重启服务
x-ui status       # 查看状态
x-ui settings     # 查看当前设置
x-ui update       # 更新面板
x-ui uninstall    # 卸载面板
```

## 支持环境

- 系统：Ubuntu、Debian、Armbian、Fedora、CentOS、RHEL、AlmaLinux、Rocky Linux、Oracle Linux、Amazon Linux、Arch、Manjaro、openSUSE、Alpine 等。
- 架构：`amd64`、`386`、`arm64`、`armv7`、`armv6`、`armv5`、`s390x`。

## 数据库

默认使用 SQLite，数据文件位于 `/etc/x-ui/x-ui.db`，无需额外配置。

如需大量客户端或多节点维护，可切换到 PostgreSQL：

```bash
x-ui migrate-db --dsn "postgres://xui:password@127.0.0.1:5432/xui?sslmode=disable"
systemctl restart x-ui
```

也可以通过环境变量指定数据库：

```bash
XUI_DB_TYPE=postgres
XUI_DB_DSN=postgres://xui:password@127.0.0.1:5432/xui?sslmode=disable
```

## 说明

- 建议安装后立即确认面板端口、访问路径、证书和防火墙配置。
- 如跳过 SSL，请仅在反向代理或 SSH 隧道后访问面板。
- 升级前建议先备份数据库和配置文件。
- 项目遵循 GPL-3.0 许可证。

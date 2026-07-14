# 米粒 3X-UI 简体中文版

基于 [MHSanaei/3x-ui](https://github.com/MHSanaei/3x-ui) 持续同步维护，提供简体中文安装脚本、更新脚本和管理菜单。

- 项目仓库：[charmtv/3x-ui](https://github.com/charmtv/3x-ui)
- 专属域名：[3xui.813099.xyz](https://3xui.813099.xyz)
- 上游项目：[MHSanaei/3x-ui](https://github.com/MHSanaei/3x-ui)

> [!IMPORTANT]
> 本项目仅供合法授权的个人学习与自用，请勿用于任何非法用途。操作前建议备份数据库和重要配置。

## 主要功能

- 支持 VLESS、VMess、Trojan、Shadowsocks、WireGuard、Hysteria2 等协议。
- 支持 TCP、WebSocket、gRPC、HTTPUpgrade、XHTTP、TLS、XTLS 和 REALITY。
- 支持客户端流量、到期时间、IP 限制、在线状态、二维码和订阅管理。
- 支持域名证书、IP 证书、自定义证书和 Cloudflare DNS 证书。
- 支持多节点、流量统计、Telegram 机器人、Fail2ban 和防火墙管理。
- 支持 SQLite 和 PostgreSQL。
- 安装、更新及管理菜单均使用简体中文。

## 一键命令

### 1. 安装最新稳定版

```bash
bash <(curl -Ls https://3xui.813099.xyz/install.sh)
```

### 2. 安装指定版本

将 `v3.5.0` 替换为需要安装的版本标签：

```bash
bash <(curl -Ls https://3xui.813099.xyz/install.sh) v3.5.0
```

### 3. 安装最新开发版

开发版跟随 `main` 分支更新，不建议用于重要环境：

```bash
bash <(curl -Ls https://3xui.813099.xyz/install.sh) dev-latest
```

### 4. 更新到最新稳定版

```bash
bash <(curl -Ls https://3xui.813099.xyz/update.sh)
```

### 5. 更新到最新开发版

```bash
XUI_UPDATE_TAG=dev-latest bash <(curl -Ls https://3xui.813099.xyz/update.sh)
```

### 6. 更新或修复简体中文菜单

适用于已经安装但菜单仍为英文的服务器：

```bash
curl -fL https://3xui.813099.xyz/x-ui.sh -o /tmp/x-ui &&
install -m 755 /tmp/x-ui /usr/bin/x-ui &&
rm -f /tmp/x-ui &&
x-ui
```

### 7. 打开管理菜单

```bash
x-ui
```

### 8. 卸载

```bash
x-ui uninstall
```

## 常用命令

| 命令 | 说明 |
| --- | --- |
| `x-ui` | 打开简体中文管理菜单 |
| `x-ui start` | 启动面板 |
| `x-ui stop` | 停止面板 |
| `x-ui restart` | 重启面板 |
| `x-ui restart-xray` | 重启 Xray |
| `x-ui status` | 查看运行状态 |
| `x-ui settings` | 查看当前设置 |
| `x-ui update` | 更新稳定版 |
| `x-ui update-dev` | 更新开发版 |
| `x-ui log` | 查看日志 |
| `x-ui uninstall` | 卸载面板 |

## 安装说明

安装完成后会生成随机用户名、密码、端口和访问路径，请妥善保存。安装结果同时写入：

```text
/etc/x-ui/install-result.env
```

若跳过 SSL，请仅通过反向代理或 SSH 隧道访问面板。

## 支持环境

- 系统：Debian、Ubuntu、Armbian、CentOS、RHEL、AlmaLinux、Rocky Linux、
  Fedora、Arch、Alpine、openSUSE 等。
- 架构：`amd64`、`386`、`arm64`、`armv7`、`armv6`、`armv5`、`s390x`。

## 数据库

默认使用 SQLite：

```text
/etc/x-ui/x-ui.db
```

大量客户端或多节点环境可在安装时选择 PostgreSQL，也可以通过 `x-ui` 菜单进行管理和迁移。

## Docker

SQLite 模式：

```bash
docker compose up -d
```

PostgreSQL 模式：

```bash
docker compose --profile postgres up -d
```

## 相关文档

- [项目 Wiki](https://github.com/MHSanaei/3x-ui/wiki)
- [部署说明](deploy/)
- [贡献指南](CONTRIBUTING.md)
- [GPL-3.0 许可证](LICENSE)

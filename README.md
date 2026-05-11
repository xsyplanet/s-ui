# S-UI

[English](https://github.com/xsyplanet/s-ui/blob/main/README_Backup.md) | [简体中文](https://github.com/xsyplanet/s-ui/blob/main/README.md)

**一个基于 SagerNet/Sing-Box 构建的高级 Web 面板 • 请支持原作者 alireza0**

> **免责声明:** 本项目仅供个人学习和交流使用，请勿将其用于非法用途

## 快速概览
| 功能列表                               |      支持状态       |
| -------------------------------------- | :----------------: |
| 多协议支持                         | :heavy_check_mark: |
| 多语言支持                         | :heavy_check_mark: |
| 多客户端/入站                   | :heavy_check_mark: |
| 高级流量路由界面     | :heavy_check_mark: |
| 客户端、流量和系统状态       | :heavy_check_mark: |
| 订阅链接 (link/json/clash + info)| :heavy_check_mark: |
| 深色/浅色主题                       | :heavy_check_mark: |
| API 接口                          | :heavy_check_mark: |

## 支持的平台
| 平台 | 架构 | 支持状态 |
|----------|--------------|---------|
| Linux    | amd64, arm64, armv7, armv6, armv5, 386, s390x | ✅ 已支持 |
| Windows  | amd64, 386, arm64 | ✅ 已支持 |
| macOS    | amd64, arm64 | 🚧 实验性支持 |

## 截图展示

!["Main_en-US"](https://imgbed-palonen.031114.xyz/file/Pictures/1778462002973_1778461914624.png)

!["Main_zh-CN"](https://imgbed-palonen.031114.xyz/file/Pictures/1778462684506_1778462637046.png)

## 默认安装信息
- 面板端口: 2095
- 面板路径: /app/
- 订阅端口: 2096
- 订阅路径: /sub/
- 用户名/密码: admin

## 一键安装/更新 S-UI 至最新版本

### Linux/macOS
```sh
bash <(curl -Ls https://raw.githubusercontent.com/xsyplanet1/s-ui/main/install.sh)
```

### Windows
1. 从 [GitHub Releases](https://github.com/xsyplanet/s-ui/releases/latest) 下载最新的 Windows 版本
2. 解压 ZIP 压缩包
3. 以管理员身份运行 `install-windows.bat` 
4. 跟随安装向导进行操作

## 安装 S-UI 历史版本

**注意：** 在安装命令的末尾，添加版本标签  `V`  加上对应的版本号，可安装指定的历史版本。

例如要安装 `V1.3.11` 版本：
```sh
VERSION=1.3.11 && bash <(curl -Ls https://raw.githubusercontent.com/xsyplanet/s-ui/$VERSION/install.sh) $VERSION
```

## 手动安装方法

### Linux/macOS
1. 根据你的系统/架构， 从 [GitHub Releases](https://github.com/xsyplanet/s-ui/releases/latest) 获取 S-UI 的最新版本
2. **可选：** 获取最新版本的 [`s-ui.sh`](https://raw.githubusercontent.com/alireza0/s-ui/master/s-ui.sh)
3. **可选：** 将 `s-ui.sh` 复制到 /usr/bin/ 目录下，并运行 `chmod +x /usr/bin/s-ui`。
4. 将 s-ui tar.gz 文件解压到你所选择的目录下， 并进入到解压 tar.gz 文件的目录。
5. 将 *.service 复制到 /etc/systemd/system/ 目录下，并运行 `systemctl daemon-reload`。
6. 使用 `systemctl enable s-ui --now` 命令，启用 S-UI 开机自启动，并启动 S-UI 服务。
7. 使用 `systemctl enable sing-box --now` 命令，启动 sing-box 服务。

### Windows
1. 从 [GitHub Releases](https://github.com/xsyplanet/s-ui/releases/latest) 获取最新的 Windows 版本
2. 下载适合您的 CPU 架构的 Windows 包 (例如 `s-ui-windows-amd64.zip`)
3. 将 ZIP 压缩包解压到您所选择的目录
4. 以管理员身份运行 `install-windows.bat` 
5. 跟随安装向导完成操作
6. 访问面板：http://localhost:2095/app

## 卸载 S-UI

```sh
sudo -i

systemctl disable s-ui  --now

rm -f /etc/systemd/system/sing-box.service
systemctl daemon-reload

rm -fr /usr/local/s-ui
rm /usr/bin/s-ui
```

## S-UI 支持的语言列表

- 英语
- 波斯语
- 越南语
- 简体中文
- 繁体中文
- 俄语

## S-UI 支持的功能

- 已支持的协议:
  - 通用协议:  Mixed、SOCKS、HTTP、HTTPS、Direct、Redirect、TProxy
  - 基于 V2Ray 的协议: VLESS、VMess、Trojan、Shadowsocks
  - 其他协议: ShadowTLS、Hysteria、Hysteria2、Naive、TUIC
- 支持 XTLS 协议
- 提供高级流量路由界面，支持 PROXY Protocol、External、透明代理、SSL 证书和端口配置
- 提供高级入站和出站配置界面
- 支持设置客户端流量上限和到期时间
- 支持显示在线客户端、入站、出站流量统计和系统状态监控
- 订阅服务支持添加外部链接和订阅
- Web 面板和订阅服务支持 HTTPS 安全访问 (需自行提供访问面板所需的域名和 SSL 证书)
- 支持切换深色/浅色主题

## 给 S-UI 配置环境变量

<details>
  <summary>点击查看详情</summary>

### 使用方法

| 变量名称       |                      类型                      | 默认值       |
| -------------- | :--------------------------------------------: | :------------ |
| SUI_LOG_LEVEL  | `"debug"` \| `"info"` \| `"warn"` \| `"error"` | `"info"`      |
| SUI_DEBUG      |                   `boolean`                    | `false`       |
| SUI_BIN_FOLDER |                    `string`                    | `"bin"`       |
| SUI_DB_FOLDER  |                    `string`                    | `"db"`        |
| SINGBOX_API    |                    `string`                    | -             |

</details>

## 给 S-UI 配置 SSL 证书

<details>
  <summary>点击查看详情</summary>

### 使用 Certbot 申请 SSL 证书

```bash
snap install core; snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot

certbot certonly --standalone --register-unsafely-without-email --non-interactive --agree-tos -d <你的域名>
```

</details>

## 原 S-UI 项目 Star 时间趋势表
[![Stargazers over time](https://starchart.cc/alireza0/s-ui.svg)](https://starchart.cc/alireza0/s-ui)

# S-UI

基于 SagerNet/Sing-Box 的**高级网络面板**

![](https://img.shields.io/github/v/release/Misaka-blog/s-ui.svg)
![](https://img.shields.io/docker/pulls/misakablog/s-ui.svg)
[![下载](https://img.shields.io/github/downloads/Misaka-blog/s-ui/total.svg)](https://img.shields.io/github/downloads/Misaka-blog/s-ui/total.svg)
[![License](https://img.shields.io/badge/license-GPL%20V3-blue.svg?longCache=true)](https://www.gnu.org/licenses/gpl-3.0.en.html)

> 免责声明：** 本项目仅用于个人学习和交流，请勿将其用于非法目的，也请勿将其用于生产环境。

**如果您认为本项目对您有帮助，不妨给予**:star2:

## 快速概览
| 功能 | 启用？      |
| -------------------------------------- | :----------------: |
| 多协议 | :heavy_check_mark: |
| 多语言 | :heavy_check_mark: |
| 多客户/入站 | :heavy_check_mark: |
| 高级流量路由接口 | :heavy_check_mark: |
| 客户、流量和系统状态 | :heavy_check_mark: |
| 订阅服务（链接 + 信息） | :heavy_check_mark: |
| 深色/浅色主题 | :heavy_check_mark: |


## 默认安装信息
- 面板端口： 2095
- 面板路径 /app/
- 订阅端口： 2096
- 订阅路径： /sub/
- 用户/密码： admin

## 安装并升级到最新版本

```sh
bash <(curl -Ls https://raw.githubusercontent.com/Misaka-blog/s-ui/master/install.sh)
```

## 安装自定义版本

**步骤 1:** 要安装所需的版本，请在安装命令末尾添加版本，例如，ver `0.0.1`：

```sh
bash <(curl -Ls https://raw.githubusercontent.com/Misaka-blog/s-ui/master/install.sh) 0.0.1
```

## 卸载 S-UI

```sh
systemctl disable sing-box --now
systemctl disable s-ui --now

rm -f /etc/systemd/system/s-ui.service
rm -f /etc/systemd/system/sing-box.service
systemctl daemon-reload

rm -fr /usr/local/s-ui
```

## 使用 Docker 安装

<details>
   <summary>点击查看详情</summary>

### 使用方法

**步骤 1:** 安装 Docker

```shell
curl -fsSL https://get.docker.com | sh
```

**第 2 步：** 安装 S-UI

```shell
mkdir s-ui && cd s-ui
docker run -itd \
    -p 2095:2095 -p 443:443 -p 80:80 \
    -v $PWD/db/:/usr/local/s-ui/db/\
    -v $PWD/cert/:/root/cert/ \
    --name s-ui --restart=unless-stopped （除非已停止
    misakablog/s-ui:latest
```

> 构建自己的映像

```shell
docker build -t s-ui .
```

</details>

## 语言

- 英语
- 波斯语
- 简体中文

## 功能

- 支持的协议：
  - 通用：Mixed, SOCKS, HTTP, HTTPS, Direct, Redirect, TProxy
  - 基于 V2Ray： VLESS、VMess、Trojan、Shadowsocks
  - 其他协议: ShadowTLS、Hysteria、Hysteri2、Naive、TUIC
- 支持 XTLS 协议
- 用于路由流量的高级界面，包括 PROXY 协议、外部和透明代理、SSL 证书和端口
- 用于入站和出站配置的高级界面
- 客户端流量上限和到期日期
- 显示在线客户端、入站和出站流量统计以及系统状态监控
- 可添加外部链接和订阅的订阅服务
- HTTPS 用于安全访问网络面板和订阅服务（自备域名 + SSL 证书）
- 深色/浅色主题

## 推荐操作系统

- CentOS 8+
- Ubuntu 20+
- Debian 10+
- Fedora 36+

## 环境变量

<details>
  <summary>点击查看详情</summary

### 使用方法

| 变量 | 类型 | 默认值
| -------------- | :--------------------------------------------: | :------------ |
| SUI_LOG_LEVEL | `"debug"`\| `"info"`\| `"warn"`\| `"error"` | `"info"` |
| SUI_DEBUG | `boolean` | `false` | SUI_BIN_BUG
| SUI_BIN_FOLDER | `string` | `"bin"` | SUI_DB_FOLDER
| SUI_DB_FOLDER | `string` | `"db"`。
| SINGBOX_API | `string` | - | SINGBOX_API

</details>

## SSL 证书

<details>
  <summary>点击查看详情</summary>

### Certbot

```bash
snap install core; snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot

certbot certonly --standalone --register-unsafely-without-email --non-interactive --agree-tos -d <您的域名>。
```

</details>

## Star 趋势

[![Stargazers over time](https://starchart.cc/Misaka-blog/s-ui.svg?variant=adaptive)](https://starchart.cc/Misaka-blog/s-ui)
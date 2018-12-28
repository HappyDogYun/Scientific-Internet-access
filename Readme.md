

[TOC]

### 1. 个人服务器

在进行工作之前，确保有一个可用的服务器，在这个服务器上进行的外网访问不会被限制。下面这个云服务器提供商可供选择，具体资费量力而行。

- 搬瓦工
  - https://bwh1.net/（支持支付宝）

- Vultr
  - https://www.vultr.com/（支持支付宝)

- SugarHosts
  - <https://www.sugarhosts.com/zh-cn/>

- Linode
  - <https://www.linode.com/>

- Virmach
  - [https://billing.virmach.com/（支持支付宝）

- RAKSmart

   <https://billing.raksmart.com/>

- Bluehost
  - <https://cn.bluehost.com/>

- DigitalOcean
  - [https://www.digitalocean.com](https://www.digitalocean.com/)

### 2. python环境

`以CentOS 7系统为例`

#### 2.1 服务器上安装配置python环境

```shell
[root@server ~]# curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
[root@server ~]# python get-pip.py
[root@server ~]# pip list
```

#### 2.2 利用pip安装shadowsocks

```shell
[root@server ~]# pip install --upgrade pip
[root@server ~]# pip install shadowsocks
```

#### 2.3 创建运行配置文件

```shell
[root@server ~]# vi shadowsocks.json
{
  "server": "0.0.0.0",
  "server_port": 8080,
  "password": "填写密码",
  "method": "aes-256-cfb"
}
```

#### 2.4 根据配置文件启动shadowsocks服务

```shell
[root@server ~]# ssserver -c shadowsocks.json -d start
```

#### 2.5 开放端口

```shell
[root@server ~]# firewall-cmd --zone=public --add-port=8080/tcp --permanent
[root@server ~]# firewall-cmd --reload
```

### 3. 检查命令

#### 3.1 查看所有python进程

```shell
[root@server ~]# ps -aux | grep python
```

#### 3.2 查看端口

```shell
[root@server ~]# yum -y install net-tools
[root@server ~]# netstart -ntlp
```

### 4. 客户端下载

#### 4.1 windows

```html
https://github.com/shadowsocks/shadowsocks-windows/releases/download/4.1.2/Shadowsocks-4.1.2.zip
```

#### 4.2 安卓

```html
https://github.com/shadowsocks/shadowsocks-android/releases/download/v4.6.3/shadowsocks--universal-4.6.3.apk
```

#### 4.3 MAC

```html
https://github.com/shadowsocks/ShadowsocksX-NG/releases/download/v1.8.2/ShadowsocksX-NG.app.1.8.2.zip
```


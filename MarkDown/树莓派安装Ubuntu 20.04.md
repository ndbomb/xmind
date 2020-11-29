## 树莓派安装Ubuntu 20.04

### 1.下载地址 

[Ubuntu20.04.1 LTS]: https://ubuntu.com/download/raspberry-pi/thank-you?version=20.04.1&amp;architecture=arm64+raspi

### 2.使用[balenaEtcher]: https://www.balena.io/etcher/安装Ubuntu镜像

> 32G及以上容量的内存卡
>
> 读卡器

### 3.配置Ubuntu系统网络

> 打开安装镜像后的```system-boot/network-config```的文件进行编辑
>
> 修改yaml文件：```sudo nano /etc/netplan/00-installer-config.yaml```

```
network:
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    version: 2
    wifis:
        wlan0:
            access-points:
               "无线网用户名":
                    password: "无线网密码"
            dhcp4: true
            dhcp6: true
            addresses: [固定ip/24]
            gateway4: 192.168.1.1
            nameservers:
                addresses: [8.8.8.8]
            renderer: networkd
            optional: true
```

### 4.下载net-tools

```
sudo apt install net-tools
```

### 5.更新环境软件包

```shell
sudo apt-get update
sudo apt-get upgrade
```

### 5.安装Docker

> 安装路径使用```which docker```查询：```/var/lib/docker``` ， 使用root可以查看

```shell
sudo curl -sSL https://get.docker.com | sh
```

> [Docker命令大全]: https://www.runoob.com/docker/docker-command-manual.html

### 6.安装Mysql

```shell
sudo docker pull mysql/mysql-server
```


# Debian 配置静态 IP

> TIME : 2024-07-17
> TAGS : Linux ; Debian

Kali 为例

## 静态 IP

- 临时生效：

`ifconfig eth0 192.168.120.56 netmask 255.255.255.0 broadcast 192.168.120.255`

- 文件配置：

/etc/network/interfaces

```interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet dhcp

# ---

#iface eth0 inet static
#address 192.168.31.222
#netmask 255.255.255.0
#gateway 192.168.31.1
#broadcast 192.168.31.255
```

## DNS 解析器

文件配置：

/etc/resolv.conf

```conf
nameserver 192.168.3.1
```

## 后续

配置后需要重启网络`systemctl restart networking`

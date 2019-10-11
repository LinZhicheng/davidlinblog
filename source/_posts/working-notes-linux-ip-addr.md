---
title: 工作笔记-Linux系统配置虚拟IP
date: 2019-09-03 08:15:14
category: 工作笔记
tags:
- Linux
- 虚拟IP
- ip addr
---

查看系统当前所有网络设备的IP

```(shell)
ip addr
```

为一个网络设备增加虚拟IP

```(shell)
ip addr add <ip>/<netmask> dev <device>
# ip addr add 192.168.1.60/24 dev eth0
```

为一个网络设备删除虚拟IP

```(shell)
ip addr del <ip>/<netmask> dev <device>
# ip addr del 192.168.1.60/24 dev eth0
```

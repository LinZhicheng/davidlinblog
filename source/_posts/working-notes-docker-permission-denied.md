---
title: 工作笔记-解决Linux下调用docker socket遇到permission denied的问题
date: 2019-10-11 23:41:28
tags: Linux, docker, usermod, permission
---

```(shell)
sudo usermod -a -G docker $USER
```

参考：<https://techoverflow.net/2017/03/01/solving-docker-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket/>

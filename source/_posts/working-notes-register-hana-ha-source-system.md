---
title: 工作笔记-注册HANA高可用集群的源系统
date: 2019-10-12 00:04:07
category: 工作笔记
tags:
- SAP HANA
- 高可用
---

1. 使用SSH登录到HANA备用主机的命令行界面

2. 切换至 `<sid>adm` 用户

3. 执行命令 `hdbnsutil -sr-register --remoteHost=<主节点hostname> --remoteInstance=<instance no.> --replicationMode=<mode> --name=<主节点hostname> --operationMode=logreplay`

4. 等待命令执行完成

参考：<https://help.aliyun.com/document_detail/112898.html>

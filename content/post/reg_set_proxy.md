---
date: '2025-07-14T21:08:26+08:00'
draft: false
title: '如何使用注册表来修改Windows的代理'
---

一般来说，使用程序修改代理可以修改注册表的方法实现。

### 修改代理开启状态

使用程序修改以下键来修改代理的开启状态  

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ProxyEnable
```

值为1时是开启状态，值为0时是关闭状态，此值的类型为**REG_DWORD**

### 修改代理服务器地址

修改以下键配置代理服务器地址

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ProxyServer
```

格式为`IP地址:端口`,例如`192.168.1.1:11451`。可以放入http和socks地址。此值的类型为**REG_SZ**  

### 修改不希望被代理的范围

如何让代理不代理部分地址呢，修改以下键

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ProxyOverride
```

为此键添加IP地址即可。可以用*/来通配，例如`192.168.\*`。如果有多个，以分号`:`来隔开多个IP地址。

在此键添加值`<local>`可以启用“**请勿将代理服务器用于本地（Intranet）地址**“选项。   

---


我用python写了一个小的示例  

地址:[github.com/qmzola/PythonSetWindowsProxy](https://github.com/qmzola/PythonSetWindowsProxy)

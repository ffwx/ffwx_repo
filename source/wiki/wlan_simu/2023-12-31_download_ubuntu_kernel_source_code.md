---
layout: wiki  # 使用wiki布局模板
wiki: wlan_simu # 这是项目名
title: Ubuntu系统下载Linux内核源码
date: 2023-12-31 20:16:50
---

安装 Ubuntu 系统后， 对应的 Linux 内核源码应该默认保存在 `/usr/src` 目录下， 但是实际上，默认情况下并没有对应的源码，只有Linux内核的headers文件夹，如下所示

```bash
w512@w512-pc:/usr/src$ tree -L 1
.
├── linux-headers-6.0.7-060007
├── linux-headers-6.0.7-060007-generic
├── linux-headers-6.5.0-13
├── linux-headers-6.5.0-13-generic
├── linux-headers-6.5.0-14
├── linux-headers-6.5.0-14-generic
└── python3.11
```

如果想阅读安装的 Ubuntu 系统对应的 Linux 内核源码，则需要按如下命令下载

## 更新数据源列表

```bash
w512@w512-pc:/usr/src$ sudo apt update
```

## 查看 Ubuntu 系统内核版本

```bash
w512@w512-pc:/usr/src$ sudo apt-cache search linux-source
linux-source - Linux kernel source with Ubuntu patches
linux-source-6.5.0 - Linux kernel source for version 6.5.0 with Ubuntu patches
```

可知对应的内核版本是 `linux-source-6.5.0`

## 下载 linux 内核源码

```bash
w512@w512-pc:/usr/src$ sudo apt install linux-source-6.2.0
```

下载完成后，查看 `/usr/src` 目录下就有对应的 linux 内核源码, 如下

```bash
w512@w512-pc:/usr/src$ ls -alh
total 40K
drwxr-xr-x 10 root root 4.0K 12月 31 20:12 .
drwxr-xr-x 14 root root 4.0K  8月  9  2022 ..
drwxr-xr-x 24 root root 4.0K 11月  8  2022 linux-headers-6.0.7-060007
drwxr-xr-x  7 root root 4.0K 11月  8  2022 linux-headers-6.0.7-060007-generic
drwxr-xr-x 26 root root 4.0K 11月 24 23:14 linux-headers-6.5.0-13
drwxr-xr-x  7 root root 4.0K 11月 24 23:14 linux-headers-6.5.0-13-generic
drwxr-xr-x 26 root root 4.0K 12月 10 17:49 linux-headers-6.5.0-14
drwxr-xr-x  7 root root 4.0K 12月 10 17:49 linux-headers-6.5.0-14-generic
drwxr-xr-x  4 root root 4.0K 12月 31 20:12 linux-source-6.5.0
lrwxrwxrwx  1 root root   45 11月 14 21:46 linux-source-6.5.0.tar.bz2 -> linux-source-6.5.0/linux-source-6.5.0.tar.bz2
drwxr-xr-x  4 root root 4.0K  2月 27  2023 python3.11
```

然后解压 `linux-source-6.5.0.tar.bz2`, 就可以通过 `vscode` 阅读源代码了


## 删除 Linux 内核源码

如果不需要 Linux 内核了，可以通过如下命令删除

```bash
w512@w512-pc:/usr/src$ sudo apt remove linux-source-6.5.0
```

## 参考

- [ubuntu 系统获取和阅读 linux 源码](https://blog.csdn.net/lanseliuxing/article/details/125743323)

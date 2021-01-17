---
title: win10+Linux(manjaro)双系统安装
date: 2021-01-17 19:05:35
tags:
- 系统安装
- Linux
- manjaro
- 环境配置
---

## 一、前言

`Manjaro`是一款基于Arch Linux的、用户友好的发行版，虽然`Manjaro is not Arch`，但它依然能够从`AUR(Arch User Repository)`中提取软件包，且有自己的独立库。

它有且不仅有如下特性：

- **Pre-installed** （在你还没正式安装时，你便可从启动盘直接流畅体验它的桌面系统）
- 快、强、高效
- 滚动发布，无需定期更新系统版本
- ......

官方网站：https://manjaro.org/

本教程仅适用于 **单硬盘 UEFI+GPT格式启动方式**

## 二、准备工作

### 1. 查看电脑的启动方式

目前主流的两种启动系统的方式：
**legacy**启动+**MBR**分区表

**UEFI**启动+**GPT**分区表

我们需要查看自己硬盘使用的哪种分区：

文件资源管理器->（右键）此电脑->管理->磁盘管理



![image-20210117192447505](https://i.loli.net/2021/01/17/9A4NmofOsgHFqrX.png)

可以看到只有一个磁盘0，所以是“单硬盘”

右键选择一个磁盘->属性->卷
在磁盘分区形式一栏中可以看到是GPT or MBR，我的是GPT分区

![image-20210117192601275](https://i.loli.net/2021/01/17/p71h9fNE4mxueqy.png)

### 2.下载manjaro镜像：

在官网下载可能速度会比较慢，可以选择在[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/osdn/storage/g/m/ma/manjaro/kde/)下载

![image-20210117192811144](https://i.loli.net/2021/01/17/DVi4aSotkdhUw8m.png)

![image-20210117192840115](https://i.loli.net/2021/01/17/ABOYwcg8zmCI6Ps.png)

我这里选择了20.1.1下载。

### 3. 制作启动盘

制作启动盘有很多种方法，我这里选择使用[Rufus](http://rufus.ie/)来制作

![image-20210117193028900](https://i.loli.net/2021/01/17/z4Jkx23AiV5TBgS.png)

下载完成之后插入U盘，打开rufus软件，选择下载好的镜像，点击开始即可

![image-20210117193245582](https://i.loli.net/2021/01/17/5igl7EAmPByWYTj.png)
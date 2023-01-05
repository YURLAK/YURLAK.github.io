---
layout: post
title: "ArchLinux安装配置指北"
date: 2022-12-18
categories: Linux
tags: [Arch,Linux,指北]
---
>继fedora后，ArchLinux一直是我梦寐以求的Linux滚动发行版，但是新手在安装时会遇到大量困难，当然我不推荐新手尝试Arch，Arch不能给你带来“开箱即用”的体验，安装完成后甚至需要额外配置桌面，你至少需要有一段时间的Linux使用经验，而整个安装过程中你最需要克服的是终端操作的心理障碍，并具备基本的计算机常识。

参考：

[ArchWiki](https://wiki.archlinuxcn.org/wiki/%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97)

## 前言

为了便携，我选择将ArchLinux安装在我500GB的Sandisk Extreme SSD上。具体的安装步骤我不在此赘述，你可以详见开头的**参考**部分。

### 安装前的工作

#### 制作启动盘

这里推荐使用[balenaEtcher](https://www.balena.io/etcher/)进行烧录，到[清华大学镜像站](https://mirrors.tuna.tsinghua.edu.cn/archlinux/iso/)获取ArchLinux的iso文件。烧录完成后进入`BIOS`，注意将启动顺序改为首选`USB Device`，并且`Disabled`掉`Secure Boot`选项。

*Loading...*

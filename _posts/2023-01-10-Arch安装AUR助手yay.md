---
layout: post
title: "ArchLinux安装AUR助手yay"
date: 2023-01-10
categories: Linux
tags: [Arch,Linux]
---
>“Arch 用户软件仓库（Arch User Repository，AUR）是为用户而建、由用户主导的 Arch 软件仓库。AUR 中的软件包以软件包生成脚本（PKGBUILD）的形式提供，用户自己通过 makepkg 生成包，再由 pacman 安装。创建 AUR 的初衷是方便用户维护和分享新软件包，并由官方定期从中挑选软件包进入 community 仓库。”

Pacman 是一个功能强大的包管理器，作为基于 Arch 的发行版的默认设置提供，但它缺乏从 Arch 用户存储库 (AUR) 下载包的功能，所以就有了yay（Yet Another Yogurt）这个工具（Arch不内置yay），本文将介绍ArchLinux下AUR助手 **yay** 的安装。

首先克隆yay仓库，执行`git clone https://aur.archlinux.org/yay.git`，然后cd到yay文件夹。

最后执行`makepkg -si`，安装完成！

**Tips:** 执行yay的所有命令时，不需要添加`sudo`。如果你遇到了类似*权限不足*的问题，那么更改目录所有者（授予操作权限）：

`sudo chown -R 你的用户名 ./yay`


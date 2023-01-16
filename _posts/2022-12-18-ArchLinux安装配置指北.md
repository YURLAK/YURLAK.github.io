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

#### 联网

启动后进入命令行界面，我们输入`iwctl`来联网，输入`device list`查看网卡，默认是`wlan0`，接着`station 网卡名 scan`，然后`station 网卡名 get-networks`获取周围的wifi扫描结果，最后`station 网卡名 connect wifi名`连接网络，注意不会有任何提示，你只需要ping一个网址来测试联网是否成功。

#### 换源

更换清华源，更换两个：[archlinux源](https://mirrors.tuna.tsinghua.edu.cn/help/archlinux/)和[archlinuxcn源](https://mirrors.tuna.tsinghua.edu.cn/help/archlinuxcn/)，官方有具体的步骤，在此不再赘述。

#### 分区

##### 新建分区

用`fdisk -l`查看磁盘，找到你要安装的磁盘，默认是`/dev/sda`，下面我们用`cfdisk /dev/sd~`进行分区，因为它可视化，操作简单。

我的分区方案是：

- *2G* `EFI System`（EFI分区）
- *4G* `Linux Swap`（交换空间分区）
- *其余* `Linux Filesystem`（根分区）

具体步骤详见[这里](https://blog.csdn.net/qq_32760901/article/details/90695462)。

分区完后`write`，记得询问时输入`yes`，回车不起作用。

##### 格式化分区

分区完成后执行：

```
mkfs.ext4 /dev/root_partition（根分区）
mkswap /dev/swap_partition（交换空间分区）
mkfs.fat -F 32 /dev/efi_system_partition（EFI分区）
```

##### 挂载分区

⚠️**ArchWiki安装指南中的一句话非常，非常，非常重要：`然后使用 mkdir(1) 创建其他剩余的挂载点（比如 /mnt/efi）并挂载其相应的磁盘卷。`，意思是你需要自己创建每个分区相应的挂载点，我在安装grub的时候就遇到了`cannot found EFI directory`的错误，因为EFI分区的挂载点未被创建。**

还有忠告一句：`挂载分区一定要遵循顺序，先挂载根（root）分区（到 /mnt），再挂载引导（boot）分区（到 /mnt/boot 或 /mnt/efi，如果单独分出来了的话），最后再挂载其他分区。否则您可能遇到安装完成后无法启动系统的问题。`

现在挂载根分区`mount /dev/root_partition（根分区） /mnt`；
挂载EFI分区`mount /dev/efi_system_partition /mnt/boot`；
启用交换空间分区`swapon /dev/swap_partition（交换空间分区）`。

### 安装系统

安装base包、软件包和Linux内核以及常规硬件的固件`pacstrap -K /mnt base linux linux-firmware`，配置系统`genfstab -U /mnt >> /mnt/etc/fstab`，最后`arch-chroot /mnt`进入新系统。

### 安装后的工作

Congratulations！至此你已经成功了一半。

#### 安装图形界面

知名的Linux桌面环境有`GNOME`，`KDE Plasma`，`Xfce`等等。这里我选择安装**GNOME**。

##### GNOME

安装GNOME包`pacman -S gnome gnome-extra（拓展软件，可不装）`.

编辑`.xinitrc`，在文件末尾添加如下代码（选一种添加）：

GNOME Classic（推荐）:

```
export XDG_CURRENT_DESKTOP=GNOME-Classic:GNOME
export GNOME_SHELL_SESSION_MODE=classic
exec gnome-session
```

GNOME on Xorg:

```
export XDG_SESSION_TYPE=x11
export GDK_BACKEND=x11
exec gnome-session
```

然后安装gdm显示管理器`pacman -S gdm`，最后`sudo systemctl enable gdm`，`reboot`！

##### KDE

首先安装plasma`pacman -S plasma`，安装sddm显示管理器`pacman -S sddm`。

现在在你的`.xinitrc`（需要自己拷贝一份`cp /etc/X11/xinit/xinitrc ~/.xinitrc`）文件中添加`export DESKTOP_SESSION=plasma`和`exec startplasma-x11`这两行代码。

最后`sudo systemctl enable sddm`，`reboot`重启后进入桌面。

其他桌面的安装详见ArchWiki。

#### 字体

这里推荐安装如下字体：`sudo pacman -S ttf-dejavu wqy-microhei wqy-zenhei`

#### 输入法

安装ibus拼音`pacman -S ibus ibus-libpinyin`，最后在`设置`->`键盘`中添加你的输入法（例如ibus的**Sunpinyin**）。

## 祝你成功！

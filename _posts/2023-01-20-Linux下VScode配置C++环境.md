---
layout: post
title: "Linux下VScode配置C++环境"
date: 2023-01-20
categories: Linux
tags: [VScode,Linux,配置,C++]
---
>用Linux写C++，不知道使用什么编辑器？VScode！

## 安装VScode

详见[ArchWiki](https://wiki.archlinux.org/title/Visual_Studio_Code)，推荐`yay -S visual-studio-code-bin`。

## 配置C++环境

首先安装**C/C++**拓展。

![image](https://user-images.githubusercontent.com/77920708/213618264-626d2ff9-bd60-498b-a953-68e69a6e17d5.png)

然后进入你的项目文件夹（我的是StudyCpp），创建`launch.json`、`settings.json`、`tasks.json`三个配置文件，如下：

![image](https://user-images.githubusercontent.com/77920708/213618686-12d2c979-e1d0-4276-929f-8fd68131d5a2.png)


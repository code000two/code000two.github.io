---
layout:     post                       # 使用的布局（不需要改）
title:      Linux中screen命令的使用        # 标题
subtitle:   screen命令使用记录          #副标题
date:       2019-01-22                 # 时间
author:     zzreo                     # 作者
header-img: img/20190101-1.jpg         #这篇文章标题背景图片
catalog: true                         # 是否归档
tags:                                #标签
    - Linux
    - screen
    - shell
    - 文件管理
---
### screen命令
#### 命令解释
screen命令时用来管理多重视窗的程序。我们在使用ssh或telnet远程登录时，亦或是本机终端中，有时可能遇到需要耗时很久的
任务，所以使用screen新建视窗保证任务不被关闭停止。每一个视窗都是一个文字模式的画面窗口。

#### 功能优势
* 多窗口
* 可恢复
* 会话共享

#### 语法格式


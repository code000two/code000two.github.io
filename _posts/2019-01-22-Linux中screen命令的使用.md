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
`screen [-AmRvx -ls -wipe][-d <作业名称>][-h <行数>][-r <作业名称>][-s <shell>][-S <作业名称>]`

#### 参数说明
* -A：将所有的视窗都调整为目前终端机的大小。
* -d<作业名称>：将指定的screen作业离线。
* -h<行数>：指定视窗的缓冲区行数。
* -m：即使目前已在作业中的screen作业，仍强制建立新的screen作业。
* -r<作业名称>：恢复离线的screen作业。
* -R：先试图恢复离线的作业。若找不到离线的作业，即建立新的screen作业。
* -s<shell>：指定建立新视窗时，所要执行的shell。
* -S<作业名称>：指定screen作业的名称。
* -v：显示版本信息。
* -x：恢复之前离线的screen作业。
* -ls或--list：显示目前所有的screen作业。
* -wipe：检查目前所有的screen作业，并删除已经无法使用的screen作业。

#### 操作实例
使用screen可以直接创建一个新的视窗，使用-S参数指定新建screen的名字：

`screen -S test1`

查看存在的screen列表：

`screen -ls`

将存在的screen状态置为离线：

`screen -d test1`

恢复已经离线的screen：

`screen -r test1`

退出并关闭screen中的所有程序：

`quit`


---------
**在每个screen session 下，所有命令都以 ctrl+a(C-a) 开始。**

C-a ? -> 显示所有键绑定信息

C-a c -> 创建一个新的运行shell的窗口并切换到该窗口

C-a n -> Next，切换到下一个 window

C-a p -> Previous，切换到前一个 window

C-a 0..9 -> 切换到第 0..9 个 window

Ctrl+a [Space] -> 由视窗0循序切换到视窗9

C-a C-a -> 在两个最近使用的 window 间切换

C-a x -> 锁住当前的 window，需用用户密码解锁

C-a d -> detach，暂时离开当前session，将目前的 screen session (可能含有多个 windows) 丢到后台执行，并会回到还没进 screen 时的状态，此时在 screen session 里，每个 window 内运行的 process (无论是前台/后台)都在继续执行，即使 logout 也不影响。

C-a z -> 把当前session放到后台执行，用 shell 的 fg 命令则可回去。

C-a w -> 显示所有窗口列表

C-a t -> Time，显示当前时间，和系统的 load

C-a k -> kill window，强行关闭当前的 window

C-a [ -> 进入 copy mode，在 copy mode 下可以回滚、搜索、复制就像用使用 vi 一样

    C-b Backward，PageUp

    C-f Forward，PageDown

    H(大写) High，将光标移至左上角

    L Low，将光标移至左下角

    0 移到行首

    $ 行末

    w forward one word，以字为单位往前移

    b backward one word，以字为单位往后移

    Space 第一次按为标记区起点，第二次按为终点

    Esc 结束 copy mode

C-a ] -> Paste，把刚刚在 copy mode 选定的内容贴上



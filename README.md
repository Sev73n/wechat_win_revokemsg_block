# 项目名称： wechat_win_revokemsg_block
微信 for windows 基于修改 wechatwin.dll 防撤回

利用x32dbg 步进调试二进制文件，找到revokemsg命令，跳过命令执行，已实现防撤回的效果。

理论上可以随着官方版本更新，不会被屏蔽，每次更新后重新打dll补丁就行了。

# 使用说明

按照教程手动修改，或者下载 [Releases](https://github.com/Sev73n/wechat_win_revokemsg_block/releases)里面的最新dll文件直接替换即可。

# 教程

1.下载x32dbg 官网下载地址：https://x64dbg.com/#start 或使用仓库内提供的x32dbg.7z

2.解压后打开x32/x32dbg.exe

3.打开微信，扫码登陆。

4.在软件中，点击右上角文件-附加，找到wechat进程，点击附加到x32dbg软件，（注意此时微信软件应该是假死的状态，暂时不要使用。）

5.点击菜单栏下面的**符号**页面，搜索“WeChatWin”，找到WeChatWin.dll，双击进入

6.在下方窗口，右键——搜索——当前区域——字符串

7.输入“**revokemsg**”

8.找到第一个命令push wechatwin右侧的字符串应该是revokemsg, 

**注意（不要选择mov命令的，也不要选择前面有L后加双引号的）**

9.双击push这个命令，跳转到二进制程序。

9.1.我们发现这个push命令前的一个命令，是**je**的命令，也就是说，当满足条件的时候，跳转到撤回进程，我们要做的就是忽略掉这个命令。

10.双击je命令，在弹出的汇编窗口中把je修改成**jmp**，注意勾选保持命令大小和剩余字符用nop填充。

10.1.修改成功后，je变成了jmp，同时会有一个nop命令夹在jmp和push之间，说明我们修改成功了。

11.右键nop命令，点击补丁，在弹出的窗口中点击右下角的**修补文件**，另存为新的wechatwin.dll。

12.关闭x32dbg和微信软件，在微信的安装目录中，把我们打过补丁的dll文件替换微信安装目录的原文件。

13.重新启动微信，扫码登陆，可以用手机给自己发信息撤回试试，在电脑上发现撤回信息还在，说明修改成功了。


# 参考 

https://github.com/TingliangZhang/Wechat-Non-Revoke-Win10

https://www.hackhp.com/919.html

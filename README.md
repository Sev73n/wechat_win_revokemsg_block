# 项目名称： wechat_win_revokemsg_block
微信 for windows 基于修改 wechatwin.dll 防撤回

利用x32dbg 步进调试二进制文件，找到revokemsg命令，跳过命令执行，已实现防撤回的效果。

理论上可以随着官方版本更新，不会被屏蔽，每次更新后重新打dll补丁就行了。

# 教程

1.下载x32dbg 官网下载地址：https://x64dbg.com/#start 或使用仓库内提供的x32dbg.7z

2.解压后打开x32/x32dbg.exe

3.打开微信，扫码登陆。

4.在软件中，点击右上角文件-附加


# 参考 

https://github.com/TingliangZhang/Wechat-Non-Revoke-Win10

https://www.hackhp.com/919.html

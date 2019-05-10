# wechatwin_revokemsg_block
微信 for windows 基于修改 wechatwin.dll 防撤回

利用x32dbg 步进调试二进制文件，找到revokemsg命令，跳过命令执行，已实现防撤回的效果。

理论上可以随着官方版本更新，不会被屏蔽，每次更新后重新打dll补丁就行了。

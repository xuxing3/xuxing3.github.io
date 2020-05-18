[TOC]

##### 终端类型

- Console: 控制台
- Pty: 物理终端（VGA）
- tty#：虚拟终端（附加在某个物理控制台上）
- ttys: 串行终端
- pts/#: 伪终端

##### who

> su USER, su 过去的用户，不算是登陆

```bash
-r:显示运行级别
-H:显示没列表示的含义
```

##### w

>  w - Show who is logged on and what they are doing.

##### last-显示登陆日志

> 显示/var/log/wtmp文件， 显示用户登陆历史

```bash
-n# 显示最近#次的相关信息
```

##### lastb-显示错误登陆日志

> 显示/var/log/btmp文件

```bash
-n# 显示最近#次的相关信息
```

##### lastlog-显示每一个用户上一次登陆时间




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

```bash
       -u, --user LOGIN|RANGE
           Print the lastlog record of the specified user(s).
```

##### basename-取一个path的文件名

```bash
[root@xuxing Linux]# basename /etc/abc/me
me

$0：特殊变量， 执行脚本时脚本路径及名称
```

##### mail-查看当前用户的邮件

```bash
[root@localhost bin]# mail -s "test" root < /etc/fstab 
[root@localhost bin]# 
[root@localhost bin]# mail
Heirloom Mail version 12.5 7/5/10.  Type ? for help.
"/var/spool/mail/root": 1 message 1 new
>N  1 root                  Mon May 18 02:40  29/1137  "test"
& 1
Message  1:
From root@localhost.localdomain  Mon May 18 02:40:07 2020
Return-Path: <root@localhost.localdomain>
X-Original-To: root
Delivered-To: root@localhost.localdomain
Date: Mon, 18 May 2020 02:40:07 -0400
To: root@localhost.localdomain
Subject: test
User-Agent: Heirloom mailx 12.5 7/5/10
Content-Type: text/plain; charset=us-ascii
From: root@localhost.localdomain (root)
Status: R


#
# /etc/fstab
# Created by anaconda on Mon Dec 16 05:00:58 2019
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/centos-root /                       xfs     defaults        0 0
UUID=ef3f6639-cda5-40ba-99b9-8ec1bf66e201 /boot                   xfs     defaults        0 0
/dev/mapper/centos-home /home                   xfs     defaults        0 0
/dev/mapper/centos-swap swap                    swap    defaults        0 0

& 

```

mail命令安装：

```bash
#yum install -y mailx sendmail
```

##### hostname-显示主机名

```bash
#如果当前主机的主机名不是www.magedu.com. 就将其修改为www.magedu.com
[ 'hostname' != 'www.magedu.com' ] && hostname www.magedu.com
```

##### 生成随机数 RANDOM 0-32768

随机数生成器：

/dev/random
/dev/urandom

利用RANDOM生成10个随机数， 并找出其中的最大值和最小值

```bash
[root@xuxing Linux]# cat 10.sh 
#!/bin/bash

declare -i MAX=0

for I in {1..10}; do 
        MYRAND=$RANDOM
        if [ $I -le 9 ]; then
                echo -n "$MYRAND,"
        else
                echo "$MYRAND"
        fi
        [ $MYRAND -gt $MAX ] && MAX=$MYRAND
done

echo $MAX
```




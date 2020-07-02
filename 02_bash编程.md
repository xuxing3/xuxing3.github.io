[TOC]

##### 添加十个用户

```bash
[root@xuxing Linux]# cat 6.sh 
#!/bin/bash

for I in {1..10}; do
	if id user$I &> /dev/null; then
		echo "user$I exists."
	else
		useradd user$I
		echo user$I | passwd --stdin user$I &> /dev/null
	fi
done
```

##### 删除十个用户

```bash
[root@xuxing Linux]# cat 7.sh 
#!/bin/bash

for I in {1..10}; do
	if id user$I &> /dev/null; then
		userdel -r user$I
		echo "Delete user$I finished"
	else
		echo "user$I not exsit."
	fi
done
```

##### 给定一个参数，如果是del删除用户，如果是add添加用户

```bash
[root@xuxing Linux]# cat 8.sh 
#!/bin/bash

if [ $# -lt 1 ]; then 
	echo "Usage : adminusers ARG"
	exit 7 
fi

if [ $1 == 'add' ]; then 
	for I in {1..10}; do
		if id user$I &> /dev/null; then
			echo "user$I exists"
		else
			useradd user$I
			echo user$I | passwd --stdin user$I &> /dev/null
			echo "Add user$I finished"
		fi
	done
elif [ $1 == 'del' ]; then 
	for I in {1..10}; do
		if id user$I &> /dev/null; then 
			userdel -r user$I
			echo "Delete user$I finished."
		else 
			echo "No user$I"
		fi
	done
else
	echo "Unknown ARG"
	exit 8
fi
```

```bash
[root@xuxing Linux]# cat 9.sh 
#/bin/bash

echo $1
if [ $1 == '--add' ]; then
        for I in `echo $2 | sed 's/,/ /g'`; do 
                if id $I &> /dev/null; then 
                        echo "$I exsit"
                else
                        useradd $I 
                        echo $I | passwd --stdin $I &> /dev/null
                        echo "add user $I finished"
                fi 
        done
elif [ $1 == '--del' ]; then
        for I in `echo $2 | sed 's/,/ /g'`; do
                if id $I &> /dev/null; then
                        userdel -r $I
                        echo "Delete $I finished"
                else
                        echo "$I Not exsit"
                fi
        done
else 
        echo "Unknown Options"
fi
```

##### Bash中存在的测试

###### 整数测试

```bash
	-eq：测试两个整数是否相等：比如$A -eq $B， 测试着两个数是否一样
	-ne：测试两个整数是否不等：不等为真，相等为假
	-gt：测试一个数是否大于另一个数，大于为真，否则为假
	-lt：测试一个数是否小于另一个数，小于为真，否则为假
	-ge：大于或等于
	-le：小于或等于
```

###### 字符测试

```bash
==：测试是否相等，相等为真，不等为假
!=: 测试是否不等，不等为真，等为假
>
<
-n string: 测试指定字符串是否为空，空则真，不空则假
-z string: 测试指定字符串是否不空，不空为真，空则为假
```

###### 文件测试

```bash
-e FILE：测试文件是否存在
-f FILE: 测试文件是否为普通文件
-d FILE: 测试指定路径是否为目录
-r FILE: 测试当前用户对指定文件是否有读取权限；
-w
-x
```

###### 组合测试条件

```bash
-a:与关系
-o:或关系
!:非关系
```

##### 组合测试示例

```bash
if [ $# -gt 1 -a $# -le 3 ]
if [ $# -gt 1 ] && [ $# -le 3 ]
```

面向过程

​	控制结构

​		顺序结构
​		选择结构
​		循环结构

选择结构

##### if：单分支，双分支，多分枝

```bash
if CONDITION; then
	statement
	...
elif CONDITION; then
	statement
	....
else
	statement
	...
fi
```

##### case 语句：选择结构

```bash
case SWITCH in
value1)
	staement
	...
	;;
value2)
	statement
	...
	;;
*)
	statement
	...
	;;
esac
```

##### case 示例1

```bash
[root@xuxing Linux]# cat 11.sh 
#!/bin/bash

case $1 in
[0-9])
        echo "A digit.";;
[a-z])
        echo "Lover";;
[A-Z])
        echo "Upper";;
*)
        echo "Special character";;
esac
```

##### case 示例2

```bash
[root@xuxing Linux]# cat 12.sh 
#!/bin/bash
#

case $1 in
'start')
        echo "start server ...";;
'stop')
        echo "stop server ...";;
'restart')
        echo "restart server ..";;
'status')
        echo "Runnig ...";;
*)
        echo "`basename $0` (start|stop|restart|status)";;
esac
```

##### case 示例3

```bash
#!/bin/bash
#
DEBUG=0
case $1 in
-v|--verbose)
  DEBUG=1;;
*)
  echo "Unknown options"
  exit 7
  ;;
esac
[ $DEBUG == 1 ] && echo "Hello"

```



##### Other/位置变量/特殊变量

```bash
	位置变量: 
		$1, $2, ...
		Shift   <<<< 踢掉一个参数
	特殊变量：
		$?
		$#：参数的个数
		$*: 参数列表
		$@：参数列表
```

##### 脚本1

```bash
#!/bin/bash
let I=1
let M=4096
for X in {200..231}; do
        for Y in {0..255}; do
                echo "ip dhcp pool statmac$I"
                echo "hardware-address 98bc.5782.`printf %x $M`"
                let M=M+1
                let I=I+1
                echo "host 10.52.$X.$Y 255.255.0.0"
                echo "default-router 10.52.0.1"
        done
done

```


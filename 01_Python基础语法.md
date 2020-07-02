[TOC]

##### Book List

《Python Cookbook》
《Learn Python The Hard Way》
《Google's Python Class》
《简明Python教程》

##### Pyenv

https://github.com/pyenv/pyenv-installer

```bash
[root@xuxing ~]# yum -y install gcc make patch gdbm-devel openssl-dev sqlite-devel readline-devel zlib-devel bzip2-devel

#pyenv install 3.6.4

[python@xuxing ~]$ pyenv versions

pyenv 
	global
	shell
	local : 和文件夹绑定，文件夹下的version都是一样的


[python@xuxing versions]$ ls
3.5.3  3.6.4
[python@xuxing versions]$ pwd
/home/python/.pyenv/versions
[python@xuxing versions]$
```

```bash
[python@xuxing project]$ cd cmdb/
[python@xuxing cmdb]$ pyenv virtualenv 3.5.3 xuxing 
[python@xuxing cmdb]$ pyenv versions
* system (set by /home/python/project/.python-version)
  3.5.3
  3.5.3/envs/xuxing
  3.6.4
  xuxing
[python@xuxing cmdb]$ pyenv local xuxing
```

```bash
(xuxing) [python@xuxing cmdb]$ pip install redis
(xuxing) [python@xuxing cmdb]$ 
```

```bash
(xuxing) [python@xuxing cmdb]$ pip install jupyter
(xuxing) [python@xuxing cmdb]$ jupyter notebook password
(xuxing) [python@xuxing cmdb]$ jupyter notebook --ip=0.0.0.0
http://10.x.x.x:8888
```

```python
#9*9 乘法表 制表符
for i in range(1,10,1):
    for j in range(1,10,1):
        if j > i:
            break
        print(str(i)+" * "+str(j)+" = "+str(i*j)+"\t",end=' ')
    print()
```

```python
#倒着9*9 乘法表
for i in range(1,10):
    line=""
    for j in range(1,10):
        if i > j:
            line += "       "
        else:
            line += "{}*{}={:<2} ".format(j,i,i*j)
    print(line)
```

| inv_sp |      | Inventory Agent RP process to support  inentory of the RSP FPGA/CPLD/ASIC, FRU (CF, SFP+) modules |
| ------ | ---- | ------------------------------------------------------------ |
|        |      |                                                              |
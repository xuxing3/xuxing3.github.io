[TOC]

#### Linux下的一些常见的工具

##### 网络可达性检测工具

- Nmap 
- Nping
- Iperf：测试网络吞吐量
- Fping：基于ICMP的工具
- MTR：结合了traceroute和ping的网络检测工具

##### 其他工具

- watch：在一个监视窗口反复执行某一条命令的功能

  ```bash
  watch -d -n 10 ssh -l cisco 9922a show route
  
  -d: 对每一次不一样的内容进行高亮
  -n：设置重复执行的时间间隔
  ```

- wget

  ```bash
  wget https://xxx/xxx --user=xxx --password=xxx
  ```

- curl：比wget功能丰富，支持HTTP/HTTPS的`get` `post` `delete` `put` 四种方法，可以用来作为一个`RESTful API` 的调试工具 

#### 处理网络设备输出的文本

##### 正则表达式 regex

##### grep

##### awk

##### sed

##### 文本编辑工具vi和vim






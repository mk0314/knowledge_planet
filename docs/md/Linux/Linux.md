<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-13 09:53:17
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-14 15:22:04
 * @FilePath: \knowledge_planet\docs\md\Linux\Linux.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### 基础信息

计算机是由软件和硬件构成

计算机硬件的五大部件： 运算器、控制器、存储器、输入设备、输出设备

计算机软件：系统软件和应用软件

操作系统只会负责管理和操作硬件，并提供简单的人机交互的接口

> ### Linux 概述

Linux 是一个操作系统，负责任务调度、内存分配、处理外围 I/O 等操作

操作系统通常由内核和系统程序两部分组成

> ### Linux 系统优缺点

1. 通用操作系统，不跟特定的硬件绑定
2. 用 c 语言编写，有可移植性，有内核编程接口
3. 支持多用户和多任务，支持安全的分层文件系统
4. 大量的实用程序，完善的网络功能以及强大的支持文档
5. 可靠的安全性和良好的稳定性，对开发者更友好

> ### 基础命令

Linux 系统的命令通常

```
命令名称 [命令参数] [参数对象]
```

> ### Linux 常用命令

1. w / who / whoami / last - 查看登录用户情况

2. addUser / passwd / userdel - 创建用户修改密码/删除用户

3. date / cal -查看日期日历

4. write / call / mesg - 发送信息

5. clear - 清除屏幕

6. logout / exit - 退出登录

7. man / info / --help - 查看帮助

8. history - 历史命令

9. reboot - 重启系统

10. shutdown - 关机

11. su - Switch user - 切换用户

> ### Linux 文件操作相关命令

1. pwd - print working directory - 打印工作目录

2. cd - change directory - 改变目录 - 相对路劲和绝对路径

3. ls - list directory contents - 列出目录下的目录

    l - 查看文件状态

4. cat - concatrenate - 链接多个文件（查看文件内容）

5. touch - 创建空文件或者修改已有文件的最后访问时间

6. mkdir - make directory - 创建文件夹

7. rm - remove - 删除

8. rmdir - remove empty directory - 删除空文件夹

9. wget - 通过网络获取文件

    例如： wget https://www.python.org/ftp/python/3.3.7/444.txt

10. gzip / gunzip - 文件压缩/解压 （gz/tgz）
    例如：gunzip Python.zip

11. xz - 文件压缩/解压
    -z - 压缩
    -d - 解压缩
    例如：xz -z python.xz

12. tar - archive - 文件归档
    -vxf - 解归档（将一个文件拆成多个文件） - 例如： tar -xvf Python.tar
    -cvf - 创建归档文件（将多个文件合成一个文件）

13. wc - word count - 查看文件行数、单词数、字符数

    -l - 查看行数

    -w - 查看单词数

    -c - 查看字符数

14. sort - 文件排序
    -r - 降序（默认是从小到大 - 升序）

15. uniq -unique - 文件去重

16. head / tail - 查看文件的开头和结尾部分

17. more / less - 分页查看文件 -例子：cat -n taobao.html | more

18. diff - different - 比较文件的差别

19. cp - copy -复制文件

20. mv - move - 移动文件

| - 管道 -将多个进程连接起来（把前一个命令的输出作为下一个命令的输入） -输出重定向 -追加输出重定向 -错误输出重定向 -错误追加输出重定向

Ctrl+D -结束输出

Ctrl+C -中断一个正在执行的命令

Ctrl+W -删除命令中的一块

Ctrl+A -光标到行首

> ### 包管理工具

```
 yum / rpm / apt
```

1. yum search nginx - 从默认的仓库搜索有没有指定的软件

2. yum install -y nginx - 安装软件

3. yum remove -y nginx - 卸载软件

4. yum info nginx -查看软件相关信息

5. yum list installed - 查看已安装的软件

6. yum update nginx - 更新软件

> ### vim

:w -保存文件，不退出 vim

:w file -将修改的文档另外保存到 file 中，不退出 vim

:w! -强制保存文件，不退出 vim

:wq -保存文件不退出 vim

:q -不保存文件， 退出 vim

:q! -不保存文件，强制退出 vim

:e! -放弃所有修改，从上次保存文件开始继续编辑

:set num - 显示行数

G -光标移动到末尾

gg -光标移动到头部

Ctrl + F - 向下翻一页

Ctrl + U - 向上翻一页

dd -删除光标所在行 10dd 删除 10 行

yy - 复制光标所在行 10yy 复制 10 行

p -张贴

u -撤销 ctrl+r 恢复

映射快捷键：
map <F2> gg8888dddd

ignoremap **main** if **name** == '**main**':

:vs 垂直拆分窗口

:sp 水平拆分窗口

：qa 退出所有窗口

vim -d 文件 1 文件 2 -打开多文件进行版本比较

宏操作：

录制宏 - qa(a 是寄存器的名字) - recording

结束录制 - q

播放录制 - @a(a 是寄存器名字)

查找命令：

grep - 搜索字符串（支持正则表达式）

find - 搜索文件

例子：find / -name "\*.html"

-name - 根据名字搜索

-size - 根据大小搜索 - -10M / + 10M

-type - 根据类型搜索 - d

-atime - 最后访问时间

-mtime - 最后修改时间

-ctime - 创建时间

> ### 网络相关命令

-   #### ssh

格式：

```linux
 ssh 用户名@服务器ip地址
```

例子：

```
ssh root@123.33.22.44
```

-   #### scp

scp 命令是可以上传文件到 linux 系统上， scp 命令通过 ssh 协议来进行加密传送，进而保证了数据的安全性

如果想上传某个文件到 linux 系统上，格式为

```
 scp 文件路径 用户名@服务器ip
```

例子：本地文件/home/user/myfile.txt 上传到远程服务器 192.168.1.100 的/home/server 目录下，可以在本地终端中执行以下命令：

```
scp /home/user/myfile.txt user@192.168.1.100:/home/server
```

如果需要上传整个目录，可以加上-r 参数，如：

```
scp -r /home/user/mydir user@192.168.1.100:/home/server
```

-   #### sftp

sftp（Secure File Transfer Protocol）是一种基于 SSH 协议的安全文件传输方式。它提供了类似 FTP 的文件传输功能，但使用 SSH 协议进行加密传输，保证了传输过程中的数据安全性。

与 FTP 不同的是，sftp 使用了加密的通道来传输数据，因此也需要进行身份验证。在使用 sftp 之前，需要确保已经成功连接到 SSH 服务器，并提供了正确的用户名和密码进行身份验证。

一旦登录成功，就可以使用 sftp 命令进行文件传输。以下是一些常用的 sftp 命令：

-   ls：列出当前目录下的文件和子目录。

-   cd：进入指定的目录。

-   pwd：显示当前所在的目录。

-   get：从远程服务器下载指定的文件。

-   put：上传本地文件到远程服务器。

-   rm：删除指定的远程文件。

-   mkdir：在远程服务器上创建一个新的目录。

-   rmdir：删除指定的目录。

-   sftp 的使用方法和 FTP 类似，但所有的传输数据都是加密的，比 FTP 更为安全。

-   #### ping

    ping 检测网络的可达性 - ICMP - Internet Controll Management Protocol -网络管理层

    -ttl -time to live

    -PING TO DEATH - DDoS - Distributed Deny of Service - 分布式拒绝服务攻击

-   #### ifconfig / ipconfig

ifconfig 命令是一个用于在 Linux 系统上查询、配置和管理网络接口的命令行工具。它的名字来自 “interface configuration”（接口配置）的缩写。

通过运行 ifconfig 命令，你可以查询当前系统中的所有网络接口，并显示有关每个接口的详细信息。这些信息可能包括接口的 IP 地址、子网掩码、MAC 地址、接收或发送的数据包数量等等。

以下是一些常用的 ifconfig 命令选项：

ifconfig：显示所有网络接口的详细信息。

ifconfig eth0：显示名为 eth0 的网络接口的详细信息。

ifconfig -a：显示所有网络接口的详细信息，包括未启用的接口。

ifconfig eth0 up/down：打开或关闭名为 eth0 的网络接口。

ifconfig eth0 192.168.0.2 netmask 255.255.255.0：将名为 eth0 的网络接口的 IP 地址设置为 192.168.0.2，子网掩码设置为 255.255.255.0。

使用 ifconfig 命令需要 root 权限或具有管理员权限的用户才能执行。如果当前系统中没有安装 ifconfig 命令，则可以使用其他网络管理工具（如 ip 命令）代替。

ipconfig 是一个 Windows 系统上的命令行工具，用于查询和配置系统的网络接口信息。它可以显示当前系统中所有的网络适配器（包括以太网适配器、无线局域网适配器、虚拟网络适配器等），以及每个适配器的 IP 地址、子网掩码、默认网关、DNS 服务器等详细信息。

以下是一些常用的 ipconfig 命令选项：

ipconfig：显示所有网络接口的详细信息。

ipconfig /all：显示所有网络接口的详细信息，包括未启用的接口。

ipconfig /release：释放当前所有网络接口的 IP 地址。

ipconfig /renew：为当前所有网络接口获取新的 IP 地址。

ipconfig /flushdns：清除本地 DNS 缓存。

ipconfig /displaydns：显示本地 DNS 缓存中的所有记录。

需要注意的是，ipconfig 只在 Windows 操作系统下可用。在 Linux 或其他操作系统中，需要使用相应的命令行工具（如 ifconfig）来查询和配置网络接口信息。

-   #### netstat

netstat 是一个用于显示活动的网络连接和各种网络统计信息的命令行工具。在 Windows 和 Linux 等操作系统中，netstat 命令通常用于诊断和监控网络连接。

下面是 netstat 常用的一些参数和其作用：

-a：显示所有网络连接和监听端口。

-n：使用数字形式显示地址和端口号，而不是名称形式。

-b：显示正在占用每个网络连接的可执行文件。

-o：显示正在占用每个网络连接的进程 ID。

-p：显示正在占用每个网络连接的进程名称和 ID。

-r：显示路由表。

-s：显示各种网络的统计信息，包括 IP、ICMP、TCP 和 UDP。

-t：显示 TCP 连接。

-u：显示 UDP 连接。

-e：显示以太网统计信息。

通过使用这些参数，我们可以了解当前系统中的网络连接情况、端口占用情况、网络传输统计信息、路由表等，从而对网络进行诊断和调试。

需要注意的是，netstat 命令需要在管理员权限下运行才能显示全部数据。

> #### 启动停止重启服务

systemctl 是用于一个管理系统服务的命令行工具，它通常用于 Linux 系统启动停止重启

-   systemctl start [SERVICE]：启动指定的服务。
-   systemctl stop [SERVICE]：停止指定的服务。
-   systemctl restart [SERVICE]：重新启动指定的服务。
-   systemctl status [SERVICE]：查看指定服务的状态。
-   systemctl enable [SERVICE]：设置指定的服务为开机启动。
-   systemctl disable [SERVICE]：取消指定服务的开机启动。

在 Linux 系统中，有许多服务是自动启动的，例如网络服务、系统日志服务、SSH 服务等。通过使用 systemctl 命令，我们可以启动或停止这些服务，也可以设置服务为开机启动或取消开机启动。

除了上述命令外，systemctl 还提供了许多其他的操作，如 mask（禁用指定的服务）、unmask（启用已禁用的服务）、list-unit-files（列出可用服务）等。综合运用这些命令，我们可以更好地管理 Linux 系统中的各种服务。

> ### 进程相关操作

-   ps - process

-   kill
    kill -进程号 -杀死进程

-   jobs - 查看后台运行或者停止的进程

-   fg / bg -foreground / background

-   top

下面是一些常见的进程相关操作：

创建进程：进程可以通过 fork() 或者 exec() 等系统调用来创建。fork() 调用会创建一个新的进程，该进程是原进程的副本，并且从父进程继承了所有的资源、文件描述符等；exec() 调用则用于启动一个新程序并替换当前进程所执行的内容。

终止进程：进程可以通过 exit() 调用来终止自己，或者通过 kill 命令向另一个进程发送信号来终止它。

查询进程信息：进程可以通过 getpid() 和 getppid() 等系统调用来获取自己和父进程的进程 ID，也可以使用 ps 命令查看系统中正在运行的进程列表。

暂停和恢复进程：进程可以通过 sleep() 系统调用来暂停自己的执行，并在指定的时间后恢复执行；也可以通过 signal 系统调用来捕捉信号，并根据信号来决定是否暂停或恢复执行。

进程间通信：进程之间可以通过管道、消息队列、共享内存等方式来进行通信，从而实现数据的传递和共享。

总的来说，进程是操作系统中非常重要的概念之一。通过掌握进程的创建、终止、查询和通信等相关操作，可以更好地理解和管理系统中正在运行的进程。

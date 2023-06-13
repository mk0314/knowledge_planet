<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-13 09:53:17
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-13 20:39:14
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

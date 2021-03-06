<!-- TOC -->

- [命令基本格式](#命令基本格式)
    - [命令提示符](#命令提示符)
    - [命令格式](#命令格式)
    - [查询目录中内容：ls](#查询目录中内容ls)
- [文件处理命令](#文件处理命令)
    - [目录和文件处理命令](#目录和文件处理命令)
    - [链接命令](#链接命令)
- [文件搜索命令](#文件搜索命令)
    - [文件搜索命令locate](#文件搜索命令locate)
    - [命令搜索命令whereis与which](#命令搜索命令whereis与which)
    - [文件搜索命令find](#文件搜索命令find)
    - [字符串搜索命令grep](#字符串搜索命令grep)
    - [find命令与grep命令的区别](#find命令与grep命令的区别)
- [帮助命令](#帮助命令)
    - [帮助命令man](#帮助命令man)
    - [其他帮助命令](#其他帮助命令)
- [压缩与解压缩命令](#压缩与解压缩命令)
    - [.zip](#zip)
    - [.gz](#gz)
    - [.bz2](#bz2)
    - [.tar.gz](#targz)
    - [.tar.bz2](#tarbz2)
- [关机和重启命令](#关机和重启命令)
    - [shutdown命令](#shutdown命令)
    - [其他关机命令](#其他关机命令)
    - [其他重启命令](#其他重启命令)
    - [系统运行级别](#系统运行级别)
    - [退出登录命令](#退出登录命令)
- [其他常用命令](#其他常用命令)
    - [挂载命令](#挂载命令)
    - [用户登录查看和用户交互命令](#用户登录查看和用户交互命令)
- [Shell 基础](#shell-基础)
    - [Shell概述](#shell概述)
    - [脚本执行方式](#脚本执行方式)
- [!/bin/bash](#binbash)
- [The first program](#the-first-program)
- [号表示注释](#号表示注释)
    - [Bash的基本功能](#bash的基本功能)
        - [命令别名与快捷键](#命令别名与快捷键)
            - [别名永久生效与删除别名](#别名永久生效与删除别名)
            - [命令生效顺序](#命令生效顺序)
            - [常用快捷见](#常用快捷见)
        - [历史命令](#历史命令)
        - [输出重定向](#输出重定向)
        - [多命令顺序执行](#多命令顺序执行)
        - [shell中特殊符号](#shell中特殊符号)

<!-- /TOC -->
# 命令基本格式

## 命令提示符

[root@localhost ~]#

其中：

root：当前登录用户

localhost：主机名

～: 当前所在目录（家目录）

<code>#</code> :超级用户

$ :普通用户的提示符

## 命令格式
 命令 [选项] [参数]

 注意：个别命令使用不遵循此格式，当有多个选项时，可以写在一起，简化选项与完整选项

 eg: -a 等于--all

## 查询目录中内容：ls

ls [选项] [文件或目录]

选项：

-a 显示所有文件，包括隐藏文件

-l 显示详细信息: ll相当于ls -l

-d 查看目录属性

-h 人性化显示文件大小

-i 显示inode

-rw-r--r--:

* 第一位-表示文件类型

   * -文件
   * d目录
   * I软链接文件
* 每三个为一组(r读，w写，x执行)
    * rw-(所有者) 
    * r--（所属组） 
    * r--（其他人）
# 文件处理命令

## 目录和文件处理命令

建立目录：mkdir

* makdir -p [目录名]
    * -p 递归创建
    * 命令英文原意：make directories

切换所在目录：cd

* cd [目录]
    * 英文原意：change directory
    * 简化操作

    cd ~进入当前用户的家目录

    cd -j进入上次目录

    cd ..进人上一级目录

    cd .进入当前目录

相对路径：参照当前的所在目录。进行查找

cd ..[目录]

绝对路径：从根目录开始指定，一级一级递归查找

cd [目录]

**tab键补全路径**

删除空目录：rmdir

* rmdir[目录名]
    * 命令英文原意：remove empty directories

删除文件或目录 ：rm

* rm -rf [文件或目录]
    * 命令英文原意：remove
    * -r删除目录
    * -f强制

复制命令：cp

* cp [选项] [原文件或目录] [目标目录]
    * 命令英文原意：copy
    * -r复制目录
    * -p连带文件属性复制
    * -d若源文件是链接文件，则复制链接属性
    * -a相当于 -pdr

剪切或改名命令：mv

* mv [源文件或目录] [目标目录]
    * 命令英文原意：move
    * 如果源文件和目标目录不在同一个目录下，就是剪切，若同个目录就是改名

常见的目录作用

* /根目录
* /bin命令保存目录（普通用户就可以读取的命令）
* /boot启动目录，启动相关文件
* /dev设备文件保存目录
* /etc配置文件保存目录
* /home普通用户的家目录
* /lib系统库（函数库）保存目录
* /mnt系统挂载目录
* /media挂载目录
* /root超级用户的家目录
* /tmp临时目录
* /命令保存目录（超级用户才能使用的目录
* /proc直接写入内存的
* /sys
* /usr系统软件资源目录
    * /usr/bin/系统命令（普通用户）
    * /usr/sbin/系统命令（超级用户）
* /var系统相关文档内容

**proc和sys不能直接操作，这两个目录保存的是内存的过载点**

**可以在家目录root或home，以及tmp目录下随便放内容**

## 链接命令

链接命令：ln

* ln -s [原文件] [目标文件]
* 命令英文原意：link
* 功能：生产链接文件
* 选项：-s 创建软链接（soft）一定要使用绝对路径

硬链接的特征：

1. 拥有相同的i节点和存储block块，可以看做是同一个文件
2. 可通过i节点识别
3. 不能跨分区
4. 不能针对目录使用

软链接特征：
1. 类似Windows快捷方式
2. 软衔接拥有自己的i节点和block块，但是数据库中只保留原文件的文件名和I节点号，并没有实际的文件数据
3. lrwxrwxrwx l软链接（软链接文件权限都为rwxrwxrwx，根据原文件确定权限）
4. 修改任意文件，另一个都改变
5. 删除原文件，软链接不能使用

# 文件搜索命令

## 文件搜索命令locate

* locate 文件名

在后天数据库中按文件名搜索，搜索速度更快

/etc/updatedb.conf配置文件

        * PRUNE_BIND_MOUNTS = "yes"
        开启搜索显示
        * PRUNEFS=
        搜索时，不搜索的文件系统
        * PRUNEFSNAME=
        搜索时，不搜索的文件类型
        * PRUNEFSPATH=
        搜索时，不搜索的文件路径

* /var/lib/mlocate

locate命令所搜索的后台数据库

* updatedb

更新数据库

## 命令搜索命令whereis与which

* whereis 命令名

搜索命令所在路径及帮组文档所在位置

选项：

-b:只查找可执行文件

-m:只查找帮助文件

* which 文件名

搜索命令所在路径及别名

PATH环境变量：定义的是系统搜索命令的路径

## 文件搜索命令find

1. find [搜索范围] [搜索条件]

搜索文件

find / -name install.log

* 避免大范围搜索，会非常耗费系统资源
* find是在系统当中搜索符合添加的文件名，如果需要匹配使用通配符匹配，通配符是完全匹配
   * <code>*</code>匹配任意内容
   * ？匹配任意一个字符
   * []匹配任意一个中括号内的字符

2. find /root -iname install.log

不区分大小写

3. find /root -user root

按照所有者搜索

4. find /root -nouser

查找没有所有者的文件

5. find /var/log/ -mtime +10

查找10天前修改的文件

* -10 10天内修改文件
* 10  10天当天修改的文件
* +10 10天前修改的文件

* atime 文件访问时间
* ctime 改变文件属性
* mtime 修改文件内容

6. find . -size 25k

查找文件大小是25KB的文件（.代表当前目录）
* -25k 小于25KB的文件
* 25k  等于25KB的文件
* +25k 大于25KB的文件

7. find . inum 262422

查找i节点是262422的文件

8. find /etc-size +20k -a -size -50k

查找/ect/目录下，大于20kb并且小于50kb的文件

* -a and 逻辑与，两个条件都满足
* -o or  逻辑或，两个条件满足一个即可

9. find /etc -size +20k -a -size -50k -exec ls -lh {} \;

* 查找/etc/目录下，大于20KB并且小于50KB的文件，并显示详细信息
* -exec/-ok 命令 {} \;对搜索结果执行操作
## 字符串搜索命令grep

grep [选项] 字符串 文件名

在文件当中匹配符合条件的字符串

选项：
* -i 忽略大小写
* -v 排除指定字符串

## find命令与grep命令的区别

* find命令：在系统当中搜索符合条件的文件名，如果需要匹配，使用通配符匹配，通配符是完全匹配
* grep命令:在文件当中搜索符合条件的只服从，如果需要匹配，使用正则表达式进行匹配，正则表达式时包含匹配

# 帮助命令

## 帮助命令man

* man 命令

获取指定命令的帮助

eg : man ls  查看ls的帮助

* man的级别

1. 查看命令的帮助
2. 查看可被内核调用的函数的帮助
3. 查看函数和函数库的帮助
4. 查看特殊文件的帮助（主要是/dev目录下的文件）
5. 查看配置文件的帮助
6. 查看游戏的帮助
7. 查看其他杂项的帮助
8. 查看系统管理员可用命令的帮助
9. 查看和内核相关文件的帮助

* man -f 命令 相当于 whatis 命令

查看命令拥有那个级别的帮助

eg:man -5 passwd

* man -k 命令 相当于 apropos 命令

eg:apropos passwd

## 其他帮助命令

* 命令 --help

获取命令选项的帮助

eg:ls --help

* help shell内部命令

获取shell内部命令的帮助

eg:

* whereis cd

确定是否是shell内部命令

* help cd

获取内部命令帮助

详细命令帮助info

info 命令
<code>-</code>
- <code>-</code> 回车 进入子帮助页面（带有*号标记）
- <code>-</code> u   进入上层页面
- <code>-</code> n   进入下一个帮助小节
- <code>-</code> p   进入上一个帮助小节
- <code>-</code> q   退出
# 压缩与解压缩命令

常用的压缩格式： .zip  .gz  .bz2  .tar.gz  .tar.bz2

## .zip

* .zip 压缩文件名 源文件

压缩文件

* .zip -r 压缩文件名 源文件

压缩目录

* unzip 压缩文件

解压缩.zip文件

## .gz

* gzip 源文件

压缩为.gz格式的压缩文件，源文件会消失

* gzip -c 源文件 > 压缩文件

压缩为.gz格式，源文件保留

* gzip -r 目录

压缩目录下所有的子文件，但是不能压缩目录

* .gz格式解压缩

    * gzip -d 压缩文件
    * gunzip 压缩文件

## .bz2

* .bzip 源文件

压缩为.bz2格式，不保留源文件

* .bzip2 -k 源文件

压缩之后保留源文件

* bzip2 -d 压缩文件

解压缩，-k保留压缩文件

* bunzip2 压缩文件

解压缩，-k保留压缩文件

## .tar.gz

其实.tar.gz格式是先打包为.tar格式，再压缩为.gz格式

tar -zcvf 压缩包名.tar.gz 源文件

* z：压缩为.tar.gz源文件
* c：打包
* v：显示过程
* f：指定打包后的文件名

tar -xcvf 压缩包名.tar.gz

* x：解压缩.tar.gz格式


## .tar.bz2

tar -jcvf 压缩包名.tar.bz2 源文件

* z：压缩为.tar.bz2源文件
* c：打包
* v：显示过程
* f：指定打包后的文件名

tar -jxvf 压缩包名.tar.bz2

* x：解压缩.tar.bz2格式

tar -jxvf 压缩包名.tar.bz2 -C /tmp/

解压到指定目录/tmp/

tar -jtvf 压缩包名.tar.bz2

查看压缩内容但是不解压

# 关机和重启命令

## shutdown命令

shutdown [选项] 时间

* c：取消前一个关机命令
* h：关机
* r：重启

## 其他关机命令

* halt
* poweroff
* init 0

## 其他重启命令

* reboot
* init 6

## 系统运行级别

* 0关机
* 1单用户
* 2不完全多用户，不含NFS服务
* 3完全多用户
* 4未分配
* 5图形界面
* 6重启

cat/etc/inittab

修改系统默认运行级别

runlevel

查询系统运行级别

## 退出登录命令

logout


# 其他常用命令

## 挂载命令

1. 查询与自动挂载

mount

查询系统中已经挂载的设备

mount -a

依据配置文件/etc/fstab的内容，自动挂载

2. 挂载命令格式

mount [-t 文件系统] [-o 特殊选项] 设备文件名 挂载点

选项：

-t 文件系统：加入文件系统类型来指定挂载的类型，可以ext3、ext4、iso9660等文件系统

-0特殊选项：可以指定挂载的额外选项

3. 挂载光盘

mkdir /mnt/cdrom

建立挂载点

/dev/cdrom/mnt/cdrom

挂载光盘

相当于mount /dev/sr0 /mnt/cdrom/

4. 卸载命令

umount 设备文件名或挂载点

umount /mnt/cdrom

5.挂载U盘

fdisk -l

查看U盘设备文件名

mount -t vfat /dev/sdb1 /mnt/usb/

注意：Linux默认是不支持NTFS文件系统的
## 用户登录查看和用户交互命令

w 用户名

命令输出：

* USER：登录的用户名
* TTY：登录终端
* FROM：从哪个IP地址登录
* LOGIN@：登录时间
* IDLE：用户闲置时间
* JCPU：指的是和该终端连接的所有进程占用的时间，这个时间里并不包括过去的后天作业时间，但却包括当前正在运行的后天作业所占用的时间
* PCPU:是指当前进程所占用的时间
* WHAT：当前正在运行的命令

who 用户名

命令输出：

* 用户名
* 登录终端
* 登录时间（登录来源IP地址）

last 查询当前登陆和过去登陆的用户信息

last命令默认是读取/var/log/wtmp文件数据

命令输出：

* 用户名
* 登录终端
* 登录IP
* 登录时间
* 退出时间（在线时间）

lastlog 查看所有用户的最后一次登陆时间

lastlog命令默认是读取/var/log/lastlog文件数据

命令输出：

* 用户名
* 登录终端
* 登录IP
* 最后一次登录时间

# Shell 基础

## Shell概述

* Shell是一个命令行解释器，它为用户提供了一个向Linux内核发送请求以便运行程序的界面系统级程序，用户可以用Shell来启动、挂起、停止甚至是编写一些程序
* Shell还是一个功能强大的编程语言，易编写，易调试，灵活性较强，Shell是解释执行的脚本语言，在Shell中可以直接调用Linux系统命令

## 脚本执行方式

1. echo [选项] [输出内容]

-e支持反斜线控制的字符转换

\e[1;31m 开启颜色显示

\e[0m 取消颜色
2. 第一个脚本

vi hello.sh

#!/bin/bash

标识一下程序是Linux的标准脚本

#The first program

#号表示注释

3. 脚本执行

* 赋予执行权限，直接运行

chmod 755 hello.sh

./hello.sh

* 通过Bash调用执行脚本

bash hello.sh

## Bash的基本功能

### 命令别名与快捷键

alias   查看系统中所有的命令别名

alias 别名=‘原命令’  设定命令别名

#### 别名永久生效与删除别名

vi ~/.bashrc 写入环境变量配置文件（或者删除）

unalias 别名  删除别名（临时删除）

#### 命令生效顺序

* 第一顺位执行用绝对路径或相对路径执行的命令
* 第二顺位执行别名
* 第三顺位执行Bash的内部命令
* 第四顺位执行按照$PATH环境变量定义的目录查找顺序找到的第一个命令

#### 常用快捷见

* Ctrl+c 强制终止当前命令
* Ctrl+l 清屏（clear）
* Ctrl+a 光标移动到命令行首
* Ctrl+e 光标移动到命令行尾
* Ctrl+u 从光标所在位置删除到行首
* Ctrl+z 把命令放入后台
* Ctrl+r 在历史命令中搜索

### 历史命令

history [选项] [历史命令保存文件]

选项：

-c:清空历史命令

-w：把缓存中的历史命令写入历史命令保存文件～/.bash_history(系统退出时会自动写入)

历史命令默认会保存1000条，可以在环境变量配置文件/etc/profile中进行修改

1. 历史命令的调用

* 使用上、下箭头调用以前的历史命令
* 使用”！n“重复执行第n条历史命令
* 使用“！！”重复执行上一条命令
* 使用“！字串”重复执行最后一条以该字串开头的命令

2. 命令与文件补全

在Bash中，命令与文件补全是非常方便与常用的功能，我们只要在输入命令或文件时，按”tab“键就会自动进行补全

### 输出重定向

1. 标准输入输出
2. 输出重定向

### 多命令顺序执行

* 命令1：命令2 顺序执行两者没有逻辑关系
* 命令1&&命令2 逻辑与
* 命令1||命令2 逻辑或

1. 管道符

命令1|命令2

命令1的正确输出作为命令2的操作对象

2. 通配符

？匹配一个任意字符
*匹配任何内容
[]匹配中括号中任意一个字符
[-]匹配中括号中任意一个字符，-代表一个范围
[^]表示匹配不是中括号内的一个字符

### shell中特殊符号

正则表达式
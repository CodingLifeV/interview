<!-- TOC -->

- [linux 基本操作](#linux-基本操作)
  - [一、文件和目录](#一文件和目录)
    - [1. 文件管理与操作](#1-文件管理与操作)
    - [2. 文件和目录的权限](#2-文件和目录的权限)
    - [3. 查找文件](#3-查找文件)
  - [二、重定向](#二重定向)
    - [1. 输出重定向](#1-输出重定向)
    - [2. 输入重定向](#2-输入重定向)
  - [三、进程与任务管理](#三进程与任务管理)
  - [四、系统信息相关](#四系统信息相关)
  - [五、网络相关](#五网络相关)
  - [六、包管理](#六包管理)

<!-- /TOC -->

# linux 基本操作

## 一、文件和目录

### 1. 文件管理与操作

**查看**

- `ls`：列出当前目录下的所有文件
- `ls -l`：显示文件和目录的详细资料
- `ls -al`：查看全部文件，包含隐藏文件
- `pwd`：查看当前工作目录
- `cat file`：查看 file 文件内容
- `head -n x file.txt`：查看文件的前 x 行
- `tail -n x example.txt`：查看文件的后 x 行

**切换**

- `cd /home`：进入`/home`目录
- `cd ..`：返回上一级目录
- `cd ../..`：返回上两级目录
- `cd`：进入个人的主目录
- `cd ~user1`：进入个人的主目录
- `cd -`： 返回上次所在的目录

**删除**

- `rmdir dir`：删除空目录 dir
- `rm -rf dir`：删除目录 dir，不管目录是否为空
- `rmdir -p /tmp/dir1/dir2/dir3`：删除目录 dir3
- `rm file1[file2]...`：删除文件

**创建**

- `mkdir dir`：创建目录 dir
- `touch file`：创建一个空文件
-

**复制**

- `cp -r dir1 dir2`：拷贝 dir1 目录 到 dir2
- `cp file1 file2`：复制 file1 文件到 file2 文件
- `cp SRC... DST`：拷贝多个文件到指定目录
- `-r`：递归持续复制，用于目录的复制行为

**移动**

- `mv /path/to/dir1 /path/to/dir2`：移动 dir1 目录且重命名为 dir2
- `mv /path/to/file1 /path/to/file2`：移动 file1 文件且重命名为 file2

**编辑**

- `nano file`：对 file 文件进行文本编辑，如果想搜索文件内容，按`ctrl + W` 输入内容后回车即可
- `vi file`：对 file 文件进行文本编辑，如果文件不存在，则创建一个 file 文件并对其编辑
- `vim file`：对 file 文件进行文本编辑，在 vi 的基础上改进和增加了很多特性
  - 普通模式
    - `ctrl+f`：下翻一屏
    - `ctrl+b`: 上翻一屏
    - `/字母`：查找某个单词/字母，`*` 来跳到下一个匹配目标
    - `cw`：查找到后，输入 cw 进行修改（此时会进入 insert 模式）
    - 修改后按 `esc` 退到 normal 模式，按 `n` 键到下一个匹配处，输入 `.` 重复之前修改
    - `：s/old/new/` 替换当前行第一个 old 为 new
    - `：s/old/new/g` 替换当前行所有 old 为 new
    - `：n，$s/old/new/g` 替换第 n 行开始到最后一行中每一行所有 old 为 new
    - `G`：跳到末尾，再开始搜索
    - `gg`：跳到文档开头，再开始搜索
    - `x`：删除当前光标字符
    - `dd`：删除当前行
    - `J`：是删除换行符，合并下一行
    - `u`：撤销上一次修改
    - `Ctrl + r`：撤销上一次的撤销
    - `ZZ`：退出 vim
    - `:wq!`：保存修改退出
    - `fx` 在当前行找 x 字符并光标跳过去

**解压缩**

- `tar -xvzf file.tar.gz`：解压文件
- `tar -tzf file.tar.gz`：列出压缩文件列表
- `tar -czf file.tar.gz /test1 /test2`：压缩文件
- `unzip www.war -d <目录>`：解压一个 war 包并放在相应目录中

### 2. 文件和目录的权限

- `sudo su`：用户权限切换，之后输入用户密码
- `chmod 777 file`：修改 file 文件权限为 -rwxrwxrwx，r 表示读、w 表示写、x 表示可执行。  
  八进制权限表示：权限可以用 3 个 bits 表示，如下表：

  ![八进制权限表](https://ws1.sinaimg.cn/large/d4556b75ly1g4nsfsyxm4j20sf0csjrq.jpg)

- `whoami`：显示用户名称
- `passwd [-k] [-l] [-u [-f]] [-d] [-S] [username]`：更改使用者的密码
  - `-d` 删除用户密码
  - `-S` 显示密码信息

### 3. 查找文件

[Java 开发必会的 Linux 命令](https://mp.weixin.qq.com/s?__biz=MzI3NzE0NjcwMg==&mid=2650120725&idx=1&sn=509097a810542f3cc2e3a308ed5981a0&chksm=f36bbf34c41c36222fe330a6ca0e99f15ed6724d7a023902af8b7dff8eeab32f3395f33da1ff&mpshare=1&scene=23&srcid=0602md7reWOxFollAaDWysLr#rd)

- `find`

  - 命令格式：`find [查找目录] [查找规则] [查找完后的操作]`
  - 举例：
    1. `find / -name filename.txt`：根据名称查找/目录下的 filename.txt 文件。
    2. `find . -name "*.xml"`：递归查找所有的 xml 文件

- `grep`：文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来
  - 举例：
    1. `grep -H 'spring' *.xml`：查找所以有的包含 spring 的 xml 文件
    2. `grep 'test' d*`：显示所有以 d 开头的文件中包含 test 的行

## 二、重定向

[linux 输入、输出重定向的概念和用法详解](https://blog.csdn.net/world_zheng/article/details/83110029)

### 1. 输出重定向

输出重定向就是把要输出的文件信息写入到一个文件中去，而不是将要输出的文件信息输出到控制台（显示屏）

- `n>`：将输出从文件描述符 n 重定向到文件。
- `n>>`：追加文件内容，而不是覆盖原文件
- `echo`：输出到终端

### 2. 输入重定向

输入重定向：是指不使用系统提供的标准输入端口，而进行重新的指定。换言之，输入重定向就是不使用标准输入端口输入文件，而是使用指定的文件作为标准输入设备。

- `<`：代表从其他某一文件接收输入
- `<<`：here-document 形式重定向, 代表将一段标记为 here-document 的文本作为输入

  ![here-document](https://ws1.sinaimg.cn/large/d4556b75ly1g4nsexjs28j20k9055jrd.jpg)

## 三、进程与任务管理

- 进程的查看
  - `ps`：查询进程列表
  - `ps aux`：长列表显示所有用户进程
  - `ps -ef`：显示 PPID，PPID 是程序的父进程号
  - `pstree -ap`：显示进程树
  - `ps aux|grep java`：查看 java 进程
- 给进程发送信号
  - `kill -l`：显示 kill 可以发送的信号列表，通常默认是 15，即 SIGTERM
  - `kill [参数] [PID]`：通过进程 PID 结束进程
  - `killall [进程名]`：可以通过进程名而不是 PID 来结束进程，且支持通配符
  - `kill -9 PID`：杀死进程 PID
  - `killall -9 进程名`:杀死进程 PID

## 四、系统信息相关

- `top`：用来进程监控命令，用来监控系统的整体性能。
  可以显示系统负载，进程，CPU，内存，分页等信息，常用 shift+m 和 shift+p 来按 memory 和 CPU 使用对进程进行排序。

  [linux top 命令详解](https://cloud.tencent.com/developer/article/1124765)

  [linux 每日命令(37)：top 命令](https://cloud.tencent.com/developer/article/1376653)

  前五行是系统整体的统计信息。第一行是任务队列信息，第二、三行为进程和 CPU 的信息，最后两行为内存信息：

  ![](https://ws1.sinaimg.cn/large/d4556b75ly1g4nsz8ki7hj20kc0c9760.jpg)

  - 命令格式：
    `top [参数]`

  - 命令参数：
    ![](https://ws1.sinaimg.cn/large/d4556b75ly1g4ntj4c6sgj20jr0att8z.jpg)

- `df`：检查 linux 服务器的文件系统的磁盘空间占用情况

- `uname`：用来获取电脑和操作系统的相关信息

## 五、网络相关

`ping`：测试主机之间网络的连通性

- 命令格式：`ping [参数][目标主机]`

  其中参数可以为 0 到多个，目标主机可以是 IP 或者域名

`telnet`：登陆远程

- 命令格式：`telnet [参数][主机名称或IP地址<通信端口>]`

`curl`：利用 URL 规则在命令行下工作的文件传输工具，它支持文件的上传和下载

- 命令格式：`curl [option] [url]`

- 基本用法：
  1. `curl https://www.baidu.com`：将 www.baidu.com 的 html 显示在屏幕上
  2. `curl https://www.baidu.com >> file.html`：将 www.baidu.com 的 html 重定向到 file 文件
  3. `curl -o file.html https://www.baidu.com`：使用 curl 的内置 option:-o(小写)保存网页到 file.html 文件中
  4. `curl -O http://www.linux.com/hello.sh`：使用 curl 的内置 option:-O(大写)保存网页中的文件要注意这里后面的 url 要具体到某个文件，不然抓不下来

`netstat`：用于显示各种网络相关信息，如网络连接，路由表，接口状态等

- 命令格式：`netstat -a`
- 基本用法：
  1. `netstat -a`：列出所有端口
  2. `netstat -at`：列出所有 tcp 端口
  3. `netstat -au`：列出所有 udp 端口
  4. `netstat -l`：列出所有处于监听的端口
  5. `netstat -lt`：列出所有处于监听的 tcp 端口
  6. `netstat -lu`：列出所有处于监听的 udp 端口
  7. `netstat -tln | grep 8080` 查看端口 8080 的使用情况

## 六、包管理

- `apt-get`：软件的安装、卸载和升级 （Ubtu 得 Linux 系统）
  - `apt-get install xxx`：安装 xxx 安装包
  - `sudo apt-get remove xxx`：卸载 xxx 安装包
  - `apt-get update`：将所有包的来源更新
- `wget`
  - `wget URL`：把 URL 中指定的文件下载到当前目录
  - `wget URL -O file_name`：指定下载目录
  - `wget -c URL`：重新启动下载中断的文件
- 添加软件源

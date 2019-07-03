<!-- TOC -->

- [linux 基本操作](#linux-基本操作)
  - [一、件和目录](#一件和目录)
    - [1. 文件管理与操作](#1-文件管理与操作)
    - [2. 文件和目录的权限](#2-文件和目录的权限)
    - [3. 查找文件](#3-查找文件)
  - [二、重定向](#二重定向)
    - [1. 输出重定向](#1-输出重定向)
    - [2. 输入重定向](#2-输入重定向)
  - [三、进程与任务管理](#三进程与任务管理)

<!-- /TOC -->

# linux 基本操作

## 一、件和目录

### 1. 文件管理与操作

- 查看

  - `ls`：列出当前目录下的所有文件
  - `ls -al`：查看文件，包含隐藏文件
  - `pwd`：查看当前工作目录
  - `cat file`：查看 file 文件内容
  - `head -n x file.txt`：查看文件的前 x 行
  - `tail -n x example.txt`：查看文件的后 x 行

- 删除

  - `rmdir dir`：删除空目录 dir
  - `rm -rf dir`：删除目录 dir，不管目录是否为空
  - `rmdir -p /tmp/dir1/dir2/dir3`：删除目录 dir3
  - `rm file1[file2]...`：删除文件

- 创建
  - `mkdir dir`：创建目录 dir
  - `touch file`：创建一个空文件
- 复制
  - `cp -r dir1 dir2`：拷贝 dir1 目录 到 dir2
  - `cp file1 file2`：复制 file1 文件到 file2 文件
  - `cp SRC... DST`：拷贝多个文件到指定目录
- 移动
  - `mv /path/to/dir1 /path/to/dir2`：移动 dir1 目录且重命名为 dir2
  - `mv /path/to/file1 /path/to/file2`：移动 file1 文件且重命名为 file2
- 编辑

  - `nano file`：对 file 文件进行文本编辑
  - `vi file`：对 file 文件进行文本编辑，如果文件不存在，则创建一个 file 文件并对其编辑

- 解压缩
  - `tar -xvzf file.tar.gz`：解压文件
  - `tar -tzf file.tar.gz`：列出压缩文件列表
  - `tar -czf file.tar.gz /test1 /test2`：压缩文件

### 2. 文件和目录的权限

- `sudo su`：用户权限切换，之后输入用户密码
- `chmod 777 file`：修改 file 文件权限为 -rwxrwxrwx，r 表示读、w 表示写、x 表示可执行。  
  八进制权限表示：权限可以用 3 个 bits 表示，如下表：

  ![八进制权限表]()

- `whoami`：显示用户名称
- `passwd [-k] [-l] [-u [-f]] [-d] [-S] [username]`：用来更改使用者的密码
  - `-d` 删除用户密码
  - `-S` 显示密码信息

### 3. 查找文件

## 二、重定向

[linux 输入、输出重定向的概念和用法详解](https://blog.csdn.net/world_zheng/article/details/83110029)

### 1. 输出重定向

输出重定向就是把要输出的文件信息写入到一个文件中去，而不是将要输出的文件信息输出到控制台（显示屏）

- `n>`：将输出从文件描述符 n 重定向到文件。
- `n>>`：追加文件内容，而不是覆盖原文件

### 2. 输入重定向

输入重定向：是指不使用系统提供的标准输入端口，而进行重新的指定。换言之，输入重定向就是不使用标准输入端口输入文件，而是使用指定的文件作为标准输入设备。

- `<`：代表从其他某一文件接收输入
- `<<`：here-document 形式重定向, 代表将一段标记为 here-document 的文本作为输入

## 三、进程与任务管理

- 查看端口占用情况
  - `netstat -tln | grep 8080` 查看端口 8080 的使用情况
- 进程的查看
  - `ps`：查询进程列表
  - `ps aux`：长列表显示所有用户进程
  - `ps -ef`：显示 PPID，PPID 是程序的父进程号
  - `pstree -ap`：显示进程树
- 给进程发送信号
  - `kill -l`：显示 kill 可以发送的信号列表，通常默认是 15，即 SIGTERM
  - `kill [参数] [PID]`：通过进程 PID 结束进程
  - `killall [进程名]`：可以通过进程名而不是 PID 来结束进程，且支持通配符

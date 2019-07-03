<!-- TOC -->

- [linux基本操作](#linux基本操作)
    - [文件和目录](#文件和目录)
        - [文件管理与操作](#文件管理与操作)
        - [文件和目录的权限](#文件和目录的权限)
    - [重定向](#重定向)
        - [输出重定向](#输出重定向)
        - [输入重定向](#输入重定向)

<!-- /TOC -->

# linux基本操作
## 文件和目录
### 文件管理与操作

* `ls`：列出当前目录下的所有文件
* `mkdir dir`：创建目录 dir
* `cp -r dir1 dir2`：拷贝 dir1 目录 到 dir2
* `cp file1 file2`：复制 file1 文件到 file2 文件
* `cp SRC... DST`：拷贝多个文件到指定目录
* `rmdir dir`：删除空目录 dir
* `rm -rf dir`：删除目录 dir，不管目录是否为空
* `rmdir -p /tmp/dir1/dir2/dir3`：删除目录dir3
* `rm file1[file2]...`：删除文件
* `mv /path/to/dir1 /path/to/dir2`：移动 dir1 目录且重命名为 dir2
* `mv /path/to/file1 /path/to/file2`：移动 file1 文件且重命名为 file2
* `touch file`：创建一个空文件
* `nano file`：对 file 文件进行文本编辑
* `vi file`：对 file 文件进行文本编辑，如果文件不存在，则创建一个 file 文件并对其编辑
* `cat file`：查看 file 文件内容


### 文件和目录的权限

* 用户权限切换：`sudo su`，之后输入用户密码

## 重定向

### 输出重定向

* `n>`：将输出从文件描述符 n 重定向到文件。 
* `n>>`：追加文件内容，而不是覆盖原文件

### 输入重定向

* `<`：
* `<<`：
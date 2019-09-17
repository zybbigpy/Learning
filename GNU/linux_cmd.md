# 1. linux 命令行

<!-- TOC -->

- [linux 命令行](#linux-命令行)
  - [1. 压缩解压常用](#1-压缩解压常用)
  - [2. 远程登陆与传送获取文件](#2-远程登陆与传送获取文件)
  - [3. 文件查询与匹配](#3-文件查询与匹配)
    - [3.1 通配符与正则表达式](#31-通配符与正则表达式)
    - [3.2 find 查找指令](#32-find-查找指令)
    - [3.3 grep 查找指令](#33-grep-查找指令)
    - [3.4 命令组合与高级连用](#34-命令组合与高级连用)
  - [4. 进程相关](#4-进程相关)

<!-- /TOC -->

---

## 1.1. 压缩解压常用

```bash
tar -cvf name.tar ./*   # 整合当前文件夹作为tar包
tar -xvf name.tar       # 解整合tar包至当前位置

tar -czvf name.tar ./*  # 创建tar.gz
tar -xzvf name.tar      # 解压tar.gz
```

---

## 1.2. 远程登陆与传送获取文件

```bash
# 远程登录
ssh usrname@ipaddr
# 指定端口号
ssh -p port_number usrname@ipaddr
# 向远程传送文件
scp name.tar username@ipaddr:/mwq/working_directory
# 指定端口号
scp -P port
# 获取远程文件
TODO:
# 通过url获得文件
wget [url]
```

ssh 免密登陆:
首先使用ssh-keygen在本地生成公钥和私钥, 将公钥追加在远程服务器.ssh文件下的
authorized_key 文件中. 首次登陆使用私钥登陆:

```bash
ssh -p port_number usrname@ipaddr -i secret_key
```

之后就可以方便的免密登陆了.

在vscode remote ssh插件中首先创建好本地和远程的免密登陆, 而后配置好ssh_config文件
即可. 示例:

```bash
Host wqmiao_delta             # 别名
    HostName 159.226.35.226   # IP
    User wqmiao               # user name
    Port 4693                 # port
```

---

## 1.3. 文件查询与匹配

### 1.3.1. 通配符与正则表达式

### 1.3.2. find 查找指令

### 1.3.3. grep 过滤指令

### 1.3.4. 命令组合与高级连用(xargs)

---

## 1.4. 进程相关

---

## 1.5. 环境变量

通常可以使用`export`仅在当前shell中添加环境变量. 如果希望该环境变量对于
某用户有效需要修改`$HOME`目录下的`.bashrc`文件. 并使用`source`指令读取`.bahsrc`
文件. 不同于在shell中直接`bash xx.sh`, `source`指令并不会开启一个子进程(子shell),因此对当前shell有效.

通常我们常用的一些环境变量有如下这些:

1. `$HOME`: 显示当前用户路径
2. `$PWD`: 当前工作路径
3. `$PATH`: 可执行程序安装路径
4. `LD_LIBRARY_PATH`: 动态链接库路径
5. `LIBRARY_PATH`: 静态链接库路径

往往在linux系统中安装软件后需要更新`$PATH`目录, 在`.bashrc`中增加下方代码:

```bash
export PATH=$PATH:路径1:路径2:...:路径n
```

路径使用冒号进行分隔.  `/etc/profile`此文件为系统所有用户设置环境信息, 需要
root权限.当shell是交互式登录shell时,读取`.bash_profile`文件,
如在系统启动、远程登录或使用su -切换用户时; 当shell是交互式登录和非登录shell时都会读取`.bashrc`文件,如：在图形界面中打开新终端或使用su切换用户时,均属于非登录shell的情况。简单的说,`.bash_profile`只在会话开始时被读取一次,而`.bashrc`则每次打开新的终端时,都会被读取. 使用`env`命令可以显示当前全部的环境变量.

---

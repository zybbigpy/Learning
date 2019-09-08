# linux 命令行

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

## 1. 压缩解压常用

```bash
tar -cvf name.tar ./*   # 整合当前文件夹作为tar包
tar -xvf name.tar       # 解整合tar包至当前位置

tar -czvf name.tar ./*  # 创建tar.gz
tar -xzvf name.tar      # 解压tar.gz
```

---

## 2. 远程登陆与传送获取文件

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

## 3. 文件查询与匹配

### 3.1 通配符与正则表达式

### 3.2 find 查找指令

### 3.3 grep 过滤指令

### 3.4 命令组合与高级连用

---

## 4. 进程相关

---

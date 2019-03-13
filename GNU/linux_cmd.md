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
# 向远程传送文件
scp name.tar username@ipaddr:/mwq/working_directory
# 获取远程文件
scp TOOD:
# 通过url获得文件
wget [url]
```

---

## 3. 文件查询与匹配

### 3.1 通配符与正则表达式

### 3.2 find 查找指令

### 3.3 grep 查找指令

### 3.4 命令组合与高级连用

---

## 4. 进程相关

---
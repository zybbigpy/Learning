# linux 命令行

<!-- TOC -->

- [linux 命令行](#linux-命令行)
  - [1. 压缩解压常用](#1-压缩解压常用)
  - [2. ssh远程登陆与scp传送文件](#2-ssh远程登陆与scp传送文件)

<!-- /TOC -->

## 1. 压缩解压常用

```bash
tar -cvf name.tar ./* # 压缩当前文件夹作为tar包
tar -zvf name.tar     # 解压tar包至当前位置
```

## 2. ssh远程登陆与scp传送文件

```bash
ssh usrname@ipaddr

scp name.tar username@ipaddr:/mwq/wd
```
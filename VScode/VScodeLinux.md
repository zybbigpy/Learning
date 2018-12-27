# 使用 VScode作为Linux开发工具

* [80%] Linux下VScode常用操作

* [20%] C/C++ 开发

* [TODO] Python 脚本

* [TODO] MarkDown 文本

* [TODO] LaTeX 写作 

## 1. VScode Linux 下常用操作

### 1.1 使用终端打开VScode

```{bash}
code     // open vscode in the terminal

code -h  // in the terminal you can use this command to show what you can do
```

### 1.2 常用快捷键

通用

1. CTRL + SHIFT + P 打开控制台

2. CTRL + P 搜索打开文件(VSCode排除一些目录和文件如.git,规则可以在files.exclude设定)

选中单词与查找替换

1. CTRL + D  ( CTRL+ F2 选中全部出现单词可以同时编辑 )

2. 查找 CTRL+ F 查找替换 CTRL+ H

3. TODO: 文件夹查找(匹配符)

重构代码

1. CTRL+ G 跳转指定行

2. CTRL+ P 打开文件

3. CTRL+ T 搜索符号打开文件

4. CTRL+ X cut line

5. CTRL+ V paste line

终端支持

1. 打开关闭终端 CTRL+ `

2. 终端分屏 CTRL+ \ , 切换分屏 ALT + L/R

3. TODO 关闭终端 切换终端

显示

1. F11 全屏

2. CTRL + B 侧边显示/隐藏

3. CTRL + K  V markdown 侧边预览

4. CTRL + 1/2/3... 切换工作分屏区

文件

1. CTRL + N New File

2. CTRL + O Open File

3. CTRL + W close file

4. CTRL + K O open folder

5. CTRL + TAB swich file in working zone

### 参考内容

* Microsoft: VScode keyboard shortcuts for Linux / VSCode DOCs
  
* [知乎相关回答链接](https://www.zhihu.com/question/37623310)

* [一篇不错的英文博客参考](https://scotch.io/bar-talk/my-top-8-visual-studio-code-tips-and-features)

## 2. C/C++ 开发

### 2.1 开发常用快捷键

查看定义与声明

1. CTRL+ shift + F10 查看定义

2. CTRL+ ALT + F12 查看声明

3. ALT + O 在头文件和源文件之间切换

重构代码

1. 跳转定义 F12

2. 跳转声明 CTRL + F1

3. CRTL + P 输入@(工作文件符号搜索) 输入#(工作目录符号搜索)

### 2.2 智能感知

### 2.3 Clang-Format

### 2.4 Debugger(GDB)

## 3. LaTeX 支持

推荐安装TeXLive2018作为LaTeX 发行版，安装插件LaTeXWorkshop.
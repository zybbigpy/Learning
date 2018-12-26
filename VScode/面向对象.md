# 使用 VScode作为Linux开发工具

* [80%] Linux下VScode常用操作

* [TODO] C/C++ 开发

* [TODO] Python 脚本撰写

* [TODO] MarkDown 文本撰写

* [TODO] LaTeX 学术写作

## 1. VScode Linux 下常用操作

### 1.1 使用终端打开VScode

```{bash}
code     // open vscode in the terminal

code -h  // in the terminal you can use this command to show what you can do
```

### 1.2 常用快捷键

通用

1. Ctrl + Shift + P 打开控制台

2. Ctrl + P 搜索打开文件(VSCode排除一些目录和文件如.git,规则可以在files.exclude设定)

C++/C 查看声明与定义(不建议直接使用跳转)

1. ctrl + shift + F10 (查看定义)

2. ctrl + alt + F12 (查看声明)

3. alt + o (在头文件和源文件之间切换)

选中单词与查找替换

1. ctrl + d (Ctrl + F2 选中全部出现单词可以同时编辑)

2. 查找 ctrl + F 查找替换 ctrl + H

3. TODO: 文件夹查找(匹配符)

重构代码

1. 跳转定义 F12

2. 跳转声明 ctrl + F12

3. ctrl + G 跳转指定行

4. ctrl + P 打开文件

5. ctrl + T 搜索符号打开文件

6. ctrl + x cut line

7. ctrl + v paste line

终端支持

1. 打开关闭终端 ctrl + `

2. 终端分屏 ctrl + \

3. TODO 关闭终端 切换终端

显示

1. F11 (全屏)

2. 侧边显示/隐藏 ctrl + B

3. markdown 侧边预览 ctrl + k + v

4. 切换工作分屏区 ctrl + 1/2/3...

文件

1. ctrl + N New File

2. ctrl + O Open File

3. ctrl + W close file

4. ctrl + k o open folder

5. ctrl + tab swich file in working zone

### 参考内容

* Microsoft: VScode keyboard shortcuts for Linux
  
* [知乎相关回答链接](https://www.zhihu.com/question/37623310)

* [一篇不错的英文博客参考](https://scotch.io/bar-talk/my-top-8-visual-studio-code-tips-and-features)

## 2. C/C++ 开发

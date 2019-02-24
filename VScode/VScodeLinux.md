# 使用 VScode作为Linux开发工具

<!-- TOC -->

- [使用 VScode作为Linux开发工具](#使用-vscode作为linux开发工具)
  - [1. VScode Linux 下常用操作](#1-vscode-linux-下常用操作)
    - [1.1. 使用终端打开VScode](#11-使用终端打开vscode)
    - [1.2. 常用快捷键](#12-常用快捷键)
    - [1.3 设置](#13-设置)
    - [1.4. 参考内容](#14-参考内容)
  - [2. C/C++ 开发](#2-cc-开发)
    - [2.1. 开发常用快捷键](#21-开发常用快捷键)
    - [2.2. 插件支持](#22-插件支持)
    - [2.3. 智能感知](#23-智能感知)
    - [2.4. Clang-Format](#24-clang-format)
    - [2.5. Debugger(GDB)](#25-debuggergdb)
  - [3. LaTeX 支持](#3-latex-支持)
    - [3.1. 安装 LaTeX 发行版](#31-安装-latex-发行版)
    - [3.2. LaTeX Workshop](#32-latex-workshop)
    - [3.3 编辑论文中出现的一些情况](#33-编辑论文中出现的一些情况)
      - [光标问题](#光标问题)
      - [TODO 中文路径问题](#todo-中文路径问题)
    - [3.4 参考内容](#34-参考内容)
  - [4. MarkDown 写作](#4-markdown-写作)
    - [4.1. MarkDown in all 常用快捷键](#41-markdown-in-all-常用快捷键)
  - [5. Python 开发](#5-python-开发)
  - [6. Git 版本控制](#6-git-版本控制)

<!-- /TOC -->

## 1. VScode Linux 下常用操作

### 1.1. 使用终端打开VScode

```bash
code     # open vscode in the terminal

code -h  # in the terminal you can use this command to show what you can do
```

### 1.2. 常用快捷键

通用

1. `CTRL` + `SHIFT` + `P` 打开控制台

2. `CTRL` + `P` 搜索打开文件(VSCode排除一些目录和文件如.git,规则可以在files.exclude设定)

选中单词与查找替换

1. `CTRL` + `D`  ( `CTRL`+ `F2` 选中全部出现单词可以同时编辑 )

2. 查找 `CTRL` + `F` 查找替换 `CTRL` + `H`

3. TODO: 文件夹查找 (匹配符)

重构代码

1. `CTRL` + `G` 跳转指定行

2. `CTRL` + `P` 打开文件

3. `CTRL` + `T` 搜索符号打开文件

4. `CTRL` + `X` cut line

5. `CTRL` + `V` paste line

终端支持

1. 打开关闭终端 `CTRL` + `

2. 终端分屏 `CTRL` + `\` , 切换分屏 `ALT` + `L / R`

3. TODO 关闭终端 切换终端

显示

1. `F11` 全屏

2. `CTRL` + `B` 侧边显示/隐藏

3. `CTRL` + `K` + `V` MarkDown 侧边预览

4. `CTRL` + `1 / 2 / 3 ...` 切换工作区

文件

1. `CTRL` + `N` 创建新文件

2. `CTRL` + `O` 打开文件

3. `CTRL` + `W` 关闭文件

4. `CTRL` + ( `K`, `O` ) 打开文件夹

5. `CTRL` + `TAB` 工作区切换文件

### 1.3 设置

VScode 的设置是基于JSON 文件的设置，因此修改相应的JSON 文件即可。

多终端同时配置 VScode 可以使用 [Syncing](https://github.com/nonoroazoro/vscode-syncing/blob/master/README.zh-CN.md) 这款插件，我的Gist：be487c3ba582fe7b31a4127c45b4184b8a5f3022。

### 1.4. 参考内容

- [Microsoft: VScode keyboard shortcuts for Linux / VSCode DOCs](https://code.visualstudio.com/docs)
  
- [知乎相关回答链接](https://www.zhihu.com/question/37623310)

- [一篇不错的英文博客参考](https://scotch.io/bar-talk/my-top-8-visual-studio-code-tips-and-features)

## 2. C/C++ 开发

### 2.1. 开发常用快捷键

查看定义与声明

1. `CTRL`+ `SHIFT` + `F10` 查看定义

2. `CTRL`+ `ALT` + `F12` 查看声明

3. `ALT` + `O` 在头文件和源文件之间切换

重构代码

1. 跳转定义 `F12`

2. 跳转声明 `CTRL` + `F1`

3. `CTRL` + `P` 输入 `@` (工作文件符号搜索) 输入 `#`(工作目录符号搜索)

### 2.2. 插件支持

- C/C++ Microsoft IntelliSence
- C++ STL Algorithm Mnemonics 强大的 STL 算法模板补全

### 2.3. 智能感知

TODO

### 2.4. Clang-Format

TODO

### 2.5. Debugger(GDB)

TODO

## 3. LaTeX 支持

### 3.1. 安装 LaTeX 发行版

发行版请使用最新的 TeXLive 发行版, 可以在清华 tuna 源 CTAN 下载镜像文件。

### 3.2. LaTeX Workshop

- 配置编译过程: 由于默认的编译引擎是 pdflatex, 中文环境需要且切换为xelatex.
- 出现某多行编辑如以下情况时, 使用 `TAB` 进入主环境编辑

相应的JSON 设置

```JSON
      "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "%DOC%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        }
    ],
```

### 3.3 编辑论文中出现的一些情况

#### 光标问题

```LaTeX
\begin{document|}
%% ``|'' presents cursors, and you can press `TAB`, cursor will be here and then write your contents.
\end{document|}
```

#### TODO 中文路径问题

### 3.4 参考内容

- [知乎相关专栏链接](https://zhuanlan.zhihu.com/p/38178015)

## 4. MarkDown 写作

### 4.1. MarkDown in all 常用快捷键

- 列表快捷键
  - 子列表 `ENTER` + `TAB`
  - 两次 `ENTER` 结束列表环境
- 字体调整快捷键
  - `CTRL` + `B` 加粗
  - `CTRL` + `I` 斜体
  - `ALT` + `S` 删除线
- 任务栏
  - `ALT` + `C` 完成 / 取消
- 目录 (设置中打开Github支持, 使用插件 Markdown TOC)
  - 当前该插件有小问题：解决方案将换行设置eol从auto改为\n 。

## 5. Python 开发

## 6. Git 版本控制

插件说明Gitlens
# 1. 使用 VScode作为Linux开发工具

<!-- TOC -->

- [1. 使用 VScode作为Linux开发工具](#1-使用-vscode作为linux开发工具)
  - [1.1. VScode Linux 下常用操作](#11-vscode-linux-下常用操作)
    - [1.1.1. 使用终端打开VScode](#111-使用终端打开vscode)
    - [1.1.2. 常用快捷键](#112-常用快捷键)
    - [1.1.3. 设置](#113-设置)
    - [1.1.4. 参考内容](#114-参考内容)
  - [1.2. C/C++ 开发](#12-cc-开发)
    - [1.2.1. 开发常用快捷键](#121-开发常用快捷键)
    - [1.2.2. 插件支持](#122-插件支持)
    - [1.2.3. 智能感知](#123-智能感知)
    - [1.2.4. Clang-Format](#124-clang-format)
    - [1.2.5. Debugger(GDB)](#125-debuggergdb)
  - [1.3. LaTeX 支持](#13-latex-支持)
    - [1.3.1. 安装 LaTeX 发行版](#131-安装-latex-发行版)
    - [1.3.2. LaTeX Workshop](#132-latex-workshop)
    - [1.3.3. 编辑论文中出现的一些情况](#133-编辑论文中出现的一些情况)
      - [1.3.3.1. 光标问题](#1331-光标问题)
      - [1.3.3.2. TODO 中文路径问题](#1332-todo-中文路径问题)
    - [1.3.4. 参考内容](#134-参考内容)
  - [1.4. MarkDown 写作](#14-markdown-写作)
    - [1.4.1. MarkDown in all 常用快捷键](#141-markdown-in-all-常用快捷键)
  - [1.5. Python 开发](#15-python-开发)
  - [1.6. Git 版本控制](#16-git-版本控制)

<!-- /TOC -->

## 1.1. VScode Linux 下常用操作

### 1.1.1. 使用终端打开VScode

```bash
code     # open vscode in the terminal

code -h  # in the terminal you can use this command to show what you can do
```

### 1.1.2. 常用快捷键

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

6. 多行编辑 `ALT` + cursor

终端支持

1. 打开关闭终端 `CTRL` + `

2. 终端分屏 `CTRL` + `\` , 切换分屏 `ALT` + `L / R`

3. TODO: 关闭终端 切换终端

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

### 1.1.3. 设置

VScode 的设置是基于JSON 文件的设置，因此修改相应的JSON 文件即可。

多终端同时配置 VScode 可以使用 [Syncing](https://github.com/nonoroazoro/vscode-syncing/blob/master/README.zh-CN.md) 这款插件，我的Gist：be487c3ba582fe7b31a4127c45b4184b8a5f3022。

### 1.1.4. 参考内容

- [Microsoft: VScode keyboard shortcuts for Linux / VSCode DOCs](https://code.visualstudio.com/docs)
  
- [知乎相关回答链接](https://www.zhihu.com/question/37623310)

- [一篇不错的英文博客参考](https://scotch.io/bar-talk/my-top-8-visual-studio-code-tips-and-features)

## 1.2. C/C++ 开发

### 1.2.1. 开发常用快捷键

查看定义与声明

1. `CTRL`+ `SHIFT` + `F10` 查看定义

2. `CTRL`+ `ALT` + `F12` 查看声明

3. `ALT` + `O` 在头文件和源文件之间切换

重构代码

1. 跳转定义 `F12`

2. 跳转声明 `CTRL` + `F1`

3. `CTRL` + `P` 输入 `@` (工作文件符号搜索) 输入 `#`(工作目录符号搜索)

### 1.2.2. 插件支持

- C/C++ Microsoft IntelliSence
- C++ STL Algorithm Mnemonics 强大的 STL 算法模板补全

### 1.2.3. 智能感知

TODO:

### 1.2.4. Clang-Format

Clang-format 是LLVM项目下格式化代码的工具, 通常情况下, 在vscode中C/C++插件中包含了Clang-format工具, 默认的格式化方式是Visual Studio格式. 在Linux开发环境下我们通常使用LLVM格式. 在vscode的设置中搜寻format, 更改格式即可.

如果需要自定义的格式化方式, 你需要在当前工作目录下设置.clangformat文件, 通过配置该文件, clang-format可以完成自动配置

```bash
# 基于那个配置文件
BasedOnStyle: LLVM
# 访问说明符的偏移(public private)
AccessModifierOffset: -4
# 括号之后,水平对齐参数: Align DontAlign AlwaysBreak
AlignAfterOpenBracket: Align
# 连续的赋值时,对齐所有的等号
AlignConsecutiveAssignments: true
# 连续声明时，对齐所有声明的变量名
AlignConsecutiveDeclarations: true
# 左对齐换行(使用反斜杠换行)的反斜杠
AlignEscapedNewlinesLeft: true
# 水平对齐二元和三元表达式的操作数
AlignOperands: true
# 对齐连续的尾随的注释  
AlignTrailingComments: true
# 允许函数声明的所有参数在放在下一行  
AllowAllParametersOfDeclarationOnNextLine: true
# 允许短的块放在同一行  
AllowShortBlocksOnASingleLine : false
# 允许短的case标签放在同一行
AllowShortCaseLabelsOnASingleLine: false
# 允许短的函数放在同一行: None, InlineOnly(定义在类中), Empty(空函数), Inline(定义在类中，空函数), All
AllowShortFunctionsOnASingleLine: Empty
# 是否允许短if单行 If true, if (a) return; 可以放到同一行
AllowShortIfStatementsOnASingleLine: false
# 允许短的循环保持在同一行
AllowShortLoopsOnASingleLine: false
# 总是在定义返回类型后换行(deprecated)
AlwaysBreakAfterDefinitionReturnType: None
# 每行字符的限制，0表示没有限制  
ColumnLimit: 100
# 描述具有特殊意义的注释的正则表达式，它不应该被分割为多行或以其它方式改变
CommentPragmas: '^ IWYU pragma:'
# 语言: None Cpp Java Objc Protp
Language: Cpp
#指针的*的挨着哪边
PointerAlignment: Right
#缩进宽度
IndentWidth: 4
# 连续的空行保留几行
MaxEmptyLinesToKeep: 1
# 在 @property 后面添加空格, \@property (readonly) 而不是 \@property(readonly).
ObjCSpaceAfterProperty: true
# OC block后面的缩进
ObjCBlockIndentWidth: 4
# 是否允许短方法单行
AllowShortFunctionsOnASingleLine: false
# 换行的时候对齐操作符
#AlignOperands: true
# 中括号两边空格 []
SpacesInSquareBrackets: true
# 小括号两边添加空格
SpacesInParentheses : false
#等号两边的空格
SpaceBeforeAssignmentOperators: true
# 容器类的空格 例如 OC的字典
SpacesInContainerLiterals: true
#缩进
IndentWrappedFunctionNames: true
#在block从空行开始
KeepEmptyLinesAtTheStartOfBlocks: true
#在构造函数初始化时按逗号断行，并以冒号对齐
BreakConstructorInitializersBeforeComma: true
#括号后添加空格
SpaceAfterCStyleCast: false
# 允许排序#include, 造成编译错误
# SortIncludes: true
# 缩进case 标签
IndentCaseLabels: true
#tab键盘的宽度
TabWidth: 4
UseTab: Never
```

参考

1. [腾讯云博客](https://cloud.tencent.com/developer/article/1394078)
2. [Clang-format说明文档](https://clang.llvm.org/docs/ClangFormatStyleOptions.html)

### 1.2.5. Debugger(GDB)

TODO:

## 1.3. LaTeX 支持

### 1.3.1. 安装 LaTeX 发行版

发行版请使用最新的 TeXLive 发行版, 可以在清华 tuna 源 CTAN 下载镜像文件。

### 1.3.2. LaTeX Workshop

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

### 1.3.3. 编辑论文中出现的一些情况

#### 1.3.3.1. 光标问题

```LaTeX
\begin{document|}
%% ``|'' presents cursors, and you can press `TAB`, cursor will be here and then write your contents.
\end{document|}
```

#### 1.3.3.2. TODO 中文路径问题

### 1.3.4. 参考内容

- [知乎相关专栏链接](https://zhuanlan.zhihu.com/p/38178015)

## 1.4. MarkDown 写作

### 1.4.1. MarkDown in all 常用快捷键

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

## 1.5. Python 开发

## 1.6. Git 版本控制

插件说明Gitlens

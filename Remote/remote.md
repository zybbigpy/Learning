# AWS 远程开发

<!-- TOC -->

- [AWS 远程开发](#aws-远程开发)
    - [ssh 链接](#ssh-链接)
        - [cmder 创建alias](#cmder-创建alias)
        - [vscode 远程链接](#vscode-远程链接)
    - [计算软件](#计算软件)
        - [Python](#python)
        - [C++ 科学计算](#c-科学计算)
            - [Eigen](#eigen)
        - [GNU-GSL](#gnu-gsl)

<!-- /TOC -->

## ssh 链接

前文已有描述.

### cmder 创建alias

再cmder安装目录中找到config文件夹, 找到`user_aliases.cmd`追加alias. 如:

```bash
ss_delta=ssh -p 4693 wqmiao@159.226.35.226
```

### vscode 远程链接

前文已有描述.

## 计算软件

### Python

命令行安装anaconda.

```bash
wget xxx.sh
bash xxx.sh
```

可能需要手动添加环境变量

```bash
# Anaconda3 Path
export PATH=/home/ubuntu/anaconda3/bin:$PATH
```

执行`source .bashrc`.

### C++ 科学计算

#### Eigen

直接下载解压, 编译指定Eigen路径就行. 在vscode的开发环境下. 修改.vscode目录下的json文件指定inlucdePath

```json
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "/home/ubuntu/eigen-eigen-323c052e1731"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/clang",
            "cStandard": "c11",
            "cppStandard": "c++11",
            "intelliSenseMode": "clang-x64"
        }
    ],
    "version": 4
}
```

```bash
g++ -I/home/ubuntu/eigen-eigen-323c052e1731
```

### GNU-GSL

下载并解压gsl, 创建新文件夹(如`/home/mwq/gsl`)存放编译出的库与头文件等.

```bash
./configure --prefix=/home/mwq/gsl
make
make check
make install
```

在`.bashrc`中添加环境变量:

```bash
# GSL
export C_INCLUDE_PATH=$C_INCLUDE_PATH:/home/ubuntu/gsl/include
export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/home/ubuntu/gsl/include
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH::/home/ubuntu/gsl/lib
export LIBRARY_PATH=$LIBRARY_PATH::/home/ubuntu/gsl/lib
```

执行`source .bashrc`.

```bash
g++ -Wall -I/home/ubuntu/gsl/include -c test.cpp
g++ -L/home/ubuntu/gsl/include  test.o -lgsl -lgslcblas -lm -o test
```

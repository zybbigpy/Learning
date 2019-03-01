# git相关学习

<!-- TOC -->

- [git相关学习](#git相关学习)
  - [初始化Git仓库](#初始化git仓库)
    - [从现有目录初始化](#从现有目录初始化)
    - [克隆现有仓库](#克隆现有仓库)
  - [Git文件管理说明](#git文件管理说明)
    - [Git 中文件的文件状态](#git-中文件的文件状态)
    - [Git 文件状态更迭的几种情况](#git-文件状态更迭的几种情况)
  - [版本回退的几种情况](#版本回退的几种情况)
  - [管理分支](#管理分支)
    - [远程分支](#远程分支)
      - [关联远程分支](#关联远程分支)
      - [查看远程分支信息](#查看远程分支信息)
      - [推送远程分支](#推送远程分支)
      - [拉取远程分支](#拉取远程分支)
      - [切换到远程某分支](#切换到远程某分支)
    - [本地分支](#本地分支)
      - [合并分支](#合并分支)
      - [变基](#变基)
  - [团队开发](#团队开发)
  - [参考阅读](#参考阅读)

<!-- /TOC -->

## 初始化Git仓库

### 从现有目录初始化

```bash
# 当前目录创建进行版本控制
git init .
```

### 克隆现有仓库

```bash
#在本地的分支名默认为master，默认远程关联分支origin/master
git clone [url] [branch name]
```

## Git文件管理说明

### Git 中文件的文件状态

- **Untracked**  未被Git跟踪，不在Git工作区，也不在Git暂存区
- **Unmodified** 被跟踪，与最新版本库一致，且未修改，在工作区
- **Modified**  被跟踪，有新修改，与版本库不一致，在工作区，未进入暂存区
- **Staged**  被跟踪，在暂存区，等待提交进去版本库

### Git 文件状态更迭的几种情况

要善于使用 `git status` 查询状态.

```bash
# 追踪文件或者目录: Untracked -> Staged
git add [file or directory]

# 放弃工作目录活文件的所有修改: Modified -> Unmodified
git checkout [file or directory]

# 文件在暂存区，Unstage暂存区的文件: Staged -> Modified
git reset HEAD [file]

# 放弃追踪某文件，但是本地保留: Unmodified -> Untracked -> Staged
git rm --cached [file]

# 放弃追踪某文件并且本地删除: Unmodified -> Untracked -> Staged
# 要注意的是在bash中使用rm 命令只是在本地移除该文件但是没有在版本库
# 移除该文件，仍需要git add来保存进行stage当前操作
git rm [file]

# 重命名文件
git mv [fileA] [fileB]

# 文件进入版本库: Staged -> Unmodified
git commit
```

## 版本回退的几种情况

1. `HEAD` 指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令 `git reset --hard commit_id` 。*注意, 我们可以会退后使用分支的功能新开一个测试分支*

2. 穿梭前，用 `git log` 可以查看提交历史，以便确定要回退到哪个版本。

3. 要重返未来，用 `git reflog` 查看命令历史，以便确定要回到未来的哪个版本。

## 管理分支

### 远程分支

#### 关联远程分支

 `git remote add [remote name] [url]` *我们往往将默认关联的远程分支命名为 `origin` ，如果要与多个远程分支关联需要取其他的别名*。

#### 查看远程分支信息

 `git remote -v` *以便我们 fetch 与 push*

#### 推送远程分支

 `git push [remote name] [local branch name]`

#### 拉取远程分支

`git fetch [remote name]` *本操作会更新本地所有的远程分支， 然后进行手动merge 例如当前在本地master分支，需要其更新至最新 `git merge origin/master`*

#### 切换到远程某分支

我们知道即使是在 `origin` 往往不止有 `origin/master` 分支, 例如有 `origin/dev` ，我们想在本地也创建一个与远程相同的dev分支操作如下：

```bash
# git 会提示以下会进入一个临时状态只供实验分析之用
git checkout orgin/dev

# 创建本地的 dev 分支, 并且切换进入该分支
git checkout -b dev
```

### 本地分支

使用 `git branch -a`检查所有的分支信息。

#### 合并分支

#### 变基

## 团队开发

## 参考阅读

1. Git 官方文档Git Pro 书籍
2. 廖雪峰的Git教学

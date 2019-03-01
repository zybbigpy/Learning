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
    - [解析远程拉取](#解析远程拉取)
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

### 解析远程拉取

`git pull` 命令用于从另一个存储库或本地分支获取并集成(整合)。`git pull` 命令的作用是：取回远程主机某个分支的更新，再与本地的指定分支合并，它的完整格式稍稍有点复杂。使用语法 `git pull [options] [<repository> [<refspec>…]]`

描述：将远程存储库中的更改合并到当前分支中。在默认模式下，`git pull` 是 `git fetch` 后跟 `git merge FETCH_HEAD` 的缩写。

更准确地说，`git pull` 使用给定的参数运行 `git fetch`，并调用 `git merge`将检索到的分支头合并到当前分支中。 使用 `--rebase` ，它运行 `git rebase` 而不是 `git merge` 。

以下是一些示例 

```bash
git pull <远程主机名> <远程分支名>:<本地分支名>
```

比如，要取回origin主机的next分支，与本地的master分支合并，需要写成下面这样

```bash
git pull origin next:master
```

如果远程分支(next)要与当前分支合并，则冒号后面的部分可以省略。上面命令可以简写为：

```bash
git pull origin next
```

上面命令表示，取回 `origin/next` 分支，再与当前分支合并。实质上，这等同于先做 `git fetch`，再执行 `git merge` 。

```bash
git fetch origin
git merge origin/next
```

在某些场合，Git会自动在本地分支与远程分支之间，建立一种追踪关系(tracking)。比如，在 `git clone` 的时候，所有本地分支默认与远程主机的同名分支，建立追踪关系，也就是说，本地的 `master` 分支自动"追踪" `origin/master` 分支。

Git也允许手动建立追踪关系。

```bash
git branch --set-upstream master origin/next
```

上面命令指定 `master` 分支追踪 `origin/next` 分支。

如果当前分支与远程分支存在追踪关系，`git pull` 就可以省略远程分支名。

```bash
git pull origin
```

上面命令表示，本地的当前分支自动与对应的 `origin` 主机 "追踪分支"(remote-tracking branch)进行合并。

如果当前分支只有一个追踪分支，连远程主机名都可以省略。如果合并需要采用rebase模式，可以使用–rebase选项。

```bash
git pull --rebase <远程主机名> <远程分支名>:<本地分支名>
```

`git fetch` 和 `git pull` 的区别

`git fetch`：相当于是从远程获取最新版本到本地，不会自动合并。

```bash
 git fetch origin master
 git log -p master..origin/master
 git merge origin/master
```

以上命令的含义：首先从远程的`origin`的`master`主分支下载最新的版本到`origin/master`分支上，然后比较本地的`master`分支和`origin/master`分支的差别，最后进行合并。

上述过程其实可以用以下更清晰的方式来进行：

```bash
# 本地创建一个临时分支 tmp
git fetch origin master:tmp
git diff tmp
git merge tmp
```

`git pull`：相当于是从远程获取最新版本并merge到本地

```bash
git pull origin master
```

上述命令其实相当于`git fetch` 和 `git merge`
在实际使用中，`git fetch`更安全一些，因为在`merge`前，我们可以查看更新情况，然后再决定是否合并。

## 团队开发

## 参考阅读

1. Git 官方文档Git Pro 书籍
2. 廖雪峰的Git教学

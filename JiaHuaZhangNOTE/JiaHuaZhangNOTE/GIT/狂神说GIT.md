# 狂神教程

[Git 最新教程通俗易懂](https://www.bilibili.com/video/BV1FE411P7B3?p=1&vd_source=f8d6cae7f7a9e1761d1efab8a7358013)

### 前言 版本控制

1.  用于版本迭代的版本管理器

2.  用于个人文件的提交历史、多人协同开发

3.  主流版本控制器 Git、SVN、CVS、VSS、TFS 等

### Git 和 SVN 的区别

1.  本地版本控制：记录所有文件每次的更新，适合个人使用

2.  集中版本控制：所有版本数据都保存在中央服务器上，协同开发者从服务器上更新或上传自己的修改

    1.  所有版本都存在服务器上，用户本地只有自己以前同步的版本，不联网就看不到历史版本，也无法切换版本验证问题，或在不同分支工作；

    2.  所有数据存在单一服务器上，服务器损坏则所有数据丢失

    3.  代表产品：SVN、CVS、VSS

3.  分布式版本控制：所有版本信息仓库全部同步到本地的每个用户，可以在本地查看所有版本历史，可以离线在本地提交，在联网时 push 到相应的服务器或用户那里。由于所有用户保存的都是所有的版本数据，只要有一个用户的设备，就可以恢复所有的数据，但增加了本地存储空间的占用

    1.  每个人都有全部代码（有一定的安全隐患）

    2.  不会因为服务器损坏或是网络问题，造成不能工作的情况

    3.  Git 可以直接看到更新了哪些代码和文件

### 安装 Git 和环境配置

1.  Git 直接从官网安装，如果速度慢，就找镜像地址下载（一般下载最新的就行）

2.  Git 卸载：先进入环境变量，删除与 Git 有关的环境变量，然后从控制面板的程序里卸载即可

3.  Git 的安装：无脑下一步就行

4.  Git 安装后，在开始菜单，有三个程序（任意文件夹下右键也可以看到对应的程序）

    1.  Git Bash：Unix 与 Linux 风格的命令行，使用最多，最推荐

    2.  Git CMD：Windows 风格的命令行（命令有些区别）

    3.  Git GUI：图形界面的 Git，不建议初学者使用

5.  调整命令行字体大小：Ctrl + 滚轮

### 基本的 Linux 命令

1.  切到上一级目录：cd ..

2.  改变目录：cd 改变目录

3.  查看当前目录：pwd

4.  清屏：clear

5.  显示当前文件夹的所有文件：ls

6.  新建一个文件：touch file-name.file-format

7.  删除一个文件：rm file-name.file-format

8.  新建一个文件夹：mkdir XXX

9.  ==格式化系统（删除电脑中所有文件）：rm -rf /== (不要随便玩！/不要再 Linux 中尝试)

10. 删除一个文件夹：rm -r XXX

11. 移动文件：mv index.html test
12. ![[1700538203040.png]]

13. 重新初始化终端/清屏：reset

14. 查看历史命令：history

15. 注释：#

16. 退出：exit

17. 帮助：help

### Git 的必要配置

> 所有配置文件都保存在本地
> 配置文件地址：
> 系统级配置文件：Git\etc\gitconfig
> 全局配置文件：C:\Users\Administrator\\.gitconfig
> 如果需要修改配置文件，可以直接在上述地址进行修改

1.  查看配置：git config -l

2.  查看系统默认配置：git config --system --list

3.  查看用户个人配置（全局）：git config --global --list

4.  ==Git 必须设置个人的名字和邮箱！！==

5.  配置个人名称：git config --global user.name "your-name"

6.  配置个人邮箱：git config --global user.email "your-email"

### Git 的工作原理（核心）

1.  Git 本地有三个工作区域：工作目录（Working Directory）、暂存区（Stage/Index）、资源仓库（Repository 或 Git Directory）外加远程的 Git 仓库
    !\[\[Git 区域关系图.jpg]]

2.  工作目录：平时存放代码、文件的地方

3.  暂存区：临时存放改动，实际上只是一个文件

4.  资源仓库：存放数据、有提交到所有版本的数据信息、HEAD 指向最新放入仓库的版本

5.  远程仓库：托管代码、文件的服务器

Git 本地仓库示意图![[Git本地仓库示意图.jpg]]
![[Git区域关系图.jpg]]

!\[\[Git 本地仓库示意图.jpg]]
![[2022924-193111.jpg]]
Git 主要操作流程图

Git 主要命令
!\[\[Git 主要命令.png]]![[Git主要命令.png]]

### Git 基础代码

```git
// 将文件放入暂存区
git add

// 将暂存区域的文件提交到git仓库（本地）
git commit


```

### Git 基础操作

#### 创建本地仓库

##### 创建全新的仓库

1.  创建全新的仓库，在需要用 Git 管理的项目的根目录执行代码

2.  执行后出现.Git 文件，说明初始化成功

```git
# 在当前目录新建一个git代码库
$ git init
```

##### 克隆远程仓库

1.  将远程仓库的内容，完全镜像下载到本地

```git
# 克隆一个项目和它的整个代码历史（版本信息）
$ git clone SSHAddress
```

### Git 文件操作

#### 文件的四种状态

- untracked：未跟踪，此文件在文件夹中，但没有加入到 git 库，不参与版本控制，通过 git add 指令，可以转换为 staged 状态

- unmodified：文件已经入库，未修改。即版本库中的文件快照内容与文件夹中一致。如果该文件被修改，则转变为 modified。如果使用 git rm 指令移出版本库，则变为 untracked

- modified：文件已被修改，但仅是被修改，并没有进行其他操作。通过 git add 指令可以进入暂存状态 staged，通过 git checkout 指令，则是放弃修改，返回 unmodified 状态，git checkout 指令就是从仓库中取出文件，覆盖当前的修改

- staged：暂存状态，执行 git commit 指令，则将该文件同步到库中，这时候库中文件与本地文件一致，则文件变为 unmodified 状态。若执行 git reset HEAD filename，则是取消暂存，使文件状态变为 Modified

#### 查看文件状态

```git
# 查看指定文件状态
$ git status [filename]

# 查看所有文件状态
$ git status
```

#### 提交文件

```git
# 添加所有文件到暂存区
$ git add .

# 提交暂存区中的文件到本地仓库
$ git commit -m "message/notes"

```

#### 忽略文件

1.  在主目录下建立".gitignore"文件，此文件有如下规则：

    1.  在.gitignore 文件中的空行和#开头的行将会被忽略

    2.  可以使用 Linux 的通配符。比如，星号代表任意多个字符，问号代表一个字符，方括号代表可选字符范围，大括号代表可选字符串

    3.  如果名称前面有一个感叹号，表示该文件将不会被忽略

    4.  如果名称前面是一个斜杠，表示忽略根目录的该文件夹，但不忽略其余目录下的同名文件

    5.  如果名称后面时一个斜杠，表示忽略该文件夹下的所有文件

2.  [Gitignore 忽略规则](https://zhuanlan.zhihu.com/p/52885189)

```bash
#               表示此为注释,将被Git忽略
*.a             表示忽略所有 .a 结尾的文件
!lib.a          表示但lib.a除外
/TODO           表示仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/          表示忽略 build/目录下的所有文件，过滤整个build文件夹；
doc/*.txt       表示会忽略doc/notes.txt但不包括 doc/server/arch.txt

bin/:           表示忽略当前路径下的bin文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
/bin:           表示忽略根目录下的bin文件
/*.c:           表示忽略cat.c，不忽略 build/cat.c
debug/*.obj:    表示忽略debug/io.obj，不忽略 debug/common/io.obj和tools/debug/io.obj
**/foo:         表示忽略/foo,a/foo,a/b/foo等
a/**/b:         表示忽略a/b, a/x/b,a/x/y/b等
!/bin/run.sh    表示不忽略bin目录下的run.sh文件
*.log:          表示忽略所有 .log 文件
config.php:     表示忽略当前路径的 config.php 文件

/mtk/           表示过滤整个文件夹
*.zip           表示过滤所有.zip文件
/mtk/do.c       表示过滤某个具体文件

被过滤掉的文件就不会出现在git仓库中（gitlab或github）了，当然本地库中还有，只是push的时候不会上传。

需要注意的是，gitignore还可以指定要将哪些文件添加到版本管理中，如下：
!*.zip
!/mtk/one.txt

唯一的区别就是规则开头多了一个感叹号，Git会将满足这类规则的文件添加到版本管理中。为什么要有两种规则呢？
想象一个场景：假如我们只需要管理/mtk/目录中的one.txt文件，这个目录中的其他文件都不需要管理，那么.gitignore规则应写为：：
/mtk/*
!/mtk/one.txt

假设我们只有过滤规则，而没有添加规则，那么我们就需要把/mtk/目录下除了one.txt以外的所有文件都写出来！
注意上面的/mtk/*不能写为/mtk/，否则父目录被前面的规则排除掉了，one.txt文件虽然加了!过滤规则，也不会生效！

----------------------------------------------------------------------------------
还有一些规则如下：
fd1/*
说明：忽略目录 fd1 下的全部内容；注意，不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略；

/fd1/*
说明：忽略根目录下的 /fd1/ 目录的全部内容；

/*
!.gitignore
!/fw/
/fw/*
!/fw/bin/
!/fw/sf/
说明：忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录；注意要先对bin/的父目录使用!规则，使其不被排除。
```

### IDEA 中集成 Git

1.  新建项目，然后将 Clone 的文件夹直接拷贝到项目中，即可将该项目和克隆的远程仓库绑定（偷懒版本）

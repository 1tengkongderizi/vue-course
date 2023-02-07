##### 1.安装

##### 2.配置

  1.配置name和email

```bash
git config --global user.name "lizhaoxia"
git config --global user.email "1426650613@qq.com"
```

##### 3.使用git

  查看当前仓库的状态

```bash
git status
```

  初始化仓库

```bash
git init
```

  文件状态：

  1.未跟踪

  2.已跟踪

  3.暂存

  4.未修改

  5.已修改

未跟踪 -> 暂存

```bash
git add <filename>将文件切换到暂存状态
git add * 将所有已修改（未跟踪）的文件暂存
```

暂存 -> 未修改

```bash
git commit -m "xxx" 将暂存文件存储到仓库中
git commit -a -m "xxx"提交所有已修改的文件（未跟踪的文件不会提交）
```

未修改 -> 修改 ：修改代码后文件会变为修改状态

##### 4.常用的命令

  1.重置文件

```bash
git restore <filename> #恢复文件
git restore --staged <filename>#取消暂存状态
```

  2.删除文件

```bash
git rm <filename>  #删除文件
git rm <filename> -f #强制删除
```

  3.移动文件

```bash
git mv from to #移动文件 重命名文件
```



#### 分支

git在存储文件时，每一次代码提交都会创建一个与之对应的节点，git就是通过一个一个的节点来记录代码状态的，节点会构成一个树状结构，树状结构就意味着这个树会存在分支，默认情况下仓库只有一个分支，命名为master。在使用git时可以创建多个分支，分支与分支之间相互独立，在一个分支下修改代码不会影响其他分支。

```bash
git branch #查看当前分支
git branch <branch name> #创建新的分支
git branch -d <branch name>#删除分支
git switch <branch name>#切换分支
git switch -c <branch>#创建并切换分支
git merge <branch name>#合并分支
```

在开发中，都是在自己的分支上编写代码，代码编写完成后，将自己的分支合并到主分支上



#### 变基

在开发中除了通过merge来合并分支外，还可以通过变基来完成分支的合并。

我们通过merge合并分支时，在提交记录中会将所有的分支创建和分支合并的过程全部显示出来，这样当项目比较复杂，开发过程比较波折时，必须反复地创建、合并、删除分支，这样一来会使得代码提交记录变得极为混乱。

原理（变基时发生了什么）：

1.当我们发起变基时，git 会首先找到两条分支的最近公共祖先

2.对比当前分支相对于祖先的历史提交，并且将他们提取出来存储到一个临时文件中

3.将当前部分指向目标的基底

4.以当前基底开始，重新执行历史操作

变基和merge对于合并分支来说最终的结构都是一样的。但是变基会使得代码的提交记录更整洁更清晰，大部份情况下合并和变基是可以互换的，但是注意，当代码提交到远程仓库时，那么这时尽量不要变基。



#### 远程仓库（remote）

目前对git的所有操作都是在本地进行的。在开发中显然不能这样，这时我们需要远程的git仓库。远程的git仓库和本地的实质上没有什么区别，不同点在于远程的仓库可以同时被多人访问使用，方便我们协同开发。在实际工作中git的服务器通常由公司内部使用或者购买一些公共的私有git服务器，我们学习阶段，直接使用一些开放的公共git仓库，常使用的库有：github和gitee。

将本地上传git：

```bash
git remote add origin https://github.com/1tengkongderizi/git-demo.git
git remote remove origin
#git remote add <remote name> <url>
git branch -M main #修改分支的名字为main
git push -u origin main #git push将代码传到服务器上
```

将本地上传到gitee:

```bash
git remote add gitee https://gitee.com/tengkongderizi/git-demo
git push -u gitee main
```






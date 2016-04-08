# 简单的git命令

git命令可以在本地使用。

但是通常我是在网络环境中使用git。

因为有github的存在，所以我使用git通常都是针对github而言。

如果你不想通过github来保存项目，你可以自己搭建git server服务。

## 开始使用

因为项目都是从github上clone来的,所以不需要git init来初始化项目目录.

使用`git clone` 从github上把repo复制下来(首先,github上要有repo)。

```
git clone https://github.com/xxx/xxxx
```

这样,github上的repo就被复制到你的机器上。

## 文件分支

本地repo有个默认的分支master,如果不建立其它分支或是切换的话,默认的修改都是在master上进行的。

如果对文件进行了修改，需要使用`git add xxx` 把修改的内容告知git。

再使用`git commit -m "xxx"` 来提交这次修改内容,commit后还未同步到github上,只是更新了master文件指针的位置。

可以进行多次修改后统一commit。

## 用户提交

如果你没有配置user.name和user.email的话，你使用git commit会提示你配置这些内容。

你可以这么做：

+ 在`~/`目录下建立名为`.gitconfig`的文件
+ 输入以下内容:
```
    [user]
        name="xxx"
        email="xxx@xx.com"
```
设置完成后git commit会以.gitconfig中设置的名字和email做为你这次提交的提交人。

`-m "xxx"`是本次提交的理由。最好每次提交都写上详细的理由，让每次提交都知道对项目做了哪些修改。

## 同步到github

本地默认的分支是master,github上默认的也是master,不过github上的master有些不一样,它叫做origin/master。

如果没有对remote的名称做过修改的话，默认项目的主分支都是叫做origin/master。

使用命令`git push origin master`

把本地的master提交到github中。

如果有冲突，git会提示你，使用`git status`可以查看哪些文件发生了冲突。

修改完成后，再次提交。

github中的项目就与你本地一致了。

## 使用ssh来提交repo

使用http的时候每次都要问你用户名和密码，输入多了就觉得麻烦。

github上有教程使用缓存区来保存一段时间的密码，但是这样使用起来也很麻烦。

使用ssh，可以解除快烦恼。

建key的过程见`linux.md`

+ 把生成的`public key`加放到github setting->ssh and gpg keys栏目中。
+ 修改项目的remote 地址
```
git remote set-url origin git@github.com:username/projectname
```

接下去你就可以使用ssh来push commit了


## 并不是结束语

学会使用git很简单。

如果你觉得太简单了，请深入学习[git](https://www.atlassian.com/git/tutorials)
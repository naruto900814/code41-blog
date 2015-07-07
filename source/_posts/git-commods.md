title: "TODO:GIT基础知识和命令"
date: 2015-06-25 22:40:36
tags:
- 基础
- 工具
- git
categories: 
- 基础知识
---

## GIT 常用命令及基本操作
0. 查看本地文件的git的状态
```
git status
```
1. 本地工程初始化
```
git init
```
2. 为本地仓库绑定远程仓库地址
```
git remote add origin URL
```
3. 查看提交日志
```
git log
```
4. 添加和提交操作
```

```

    #### *附：SSH操作*
    > 为了减少git提交时反复输入用户名和密码的操作，故大部分采取SSH连接的方式进行提交，而通过本机的公钥文件配置在git服务器上就可以完成不用密码的提交操作。

    - 查看本地是否存在SSH keys
    ```
    ls -al ~/.ssh
    ```
    + ssh-keygen生成新的id_rsa和id_rsa.pub文件（*rsa为加密方式*）
    ```
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```
    + 配置保存公钥和私钥的文件位置和文件名
    ```
    Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
    ```
    + SSH密钥使用密码（可不配置）
    + 在git仓库中配置(*如果将id_rsa.pub放到另外机器的 ~/.ssh.authorized_keys中，可以通过ssh和scp无密码登录访问*)


## TODO:GIT 分支操作
0. 查看远程分支
```
git branch -a
```
1. 查看本地分支
```
git branch
```
2. 推送分支到远程分支
```
git push origin BRANCH_NAME
```
3. 切换分支
```
git checkout BRANCH_NAME
```


## GIT Config 配置相关
0. 修改git请求URL中的协议头
```
git config --global url."https://".insteadOf git://
```
 > __[解决问题]__bower ECMDERR Failed to execute “git ls-remote ... exit code of #128

1. 查看当前配置信息
```
git config --list
```
2. 配置操作
    - 添加配置
    ```
    // 添加 'git add .' 的全局别名
    git config --global alias.a 'add .'
    ```
    - 删除配置
    ```
    // 删除别名
    git config --unset alias.s
    ```
3. 根据git仓库配置不同的用户名和密码
    - 根据不同的用户名生成不同的SSH keys
    - 去除全局的user.name和user.email的设置
    ```
    git config --global --unset user.name
    git config --global --unset user.email
    ```
    - 修改用户下的config文件（*\~/.ssh/config*）
    ```
    #Default Git
    Host github.com
        HostName github.com
        User code41
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa.code41.pub

    Host github.com
        HostName github.com
        User naruto900814
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa.naruto900814.pub

    Host demo.com
        HostName demo.com
        User shaw
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa.shaw.pub
    ```
    > 以上配置，访问github时，根据不同的用户名，使用不同的公钥文件；通过在git的repo中配置不同的user就可以使用以上配置按不同用户提交；当git提交到不同的GIT仓库的时候就会使用不同配置，从而使用不同的账户和公钥文件。

## TODO:GIT 的忽略设置 __.gitignore__
>__忽略规则__
>* 以斜杠“/”开头表示目录
>* 以星号“*”通配多个字符
>* 以问号“?”通配单个字符
>* 以方括号“[]”包含单个字符的匹配列表
>* 以叹号“!”表示不忽略(跟踪)匹配到的文件或目录
>* .gitignore配置文件是按行从上到下进行规则匹配的，意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效

## TODO:GIT的高级操作
1. commit查看提交日志 => *git reflog*
2. 丢失找回操作

## TODO:GIT的服务器搭建
0. 服务器的搭建
1. GIT的权限————gitolite
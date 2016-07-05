# git配置
[TOC]
## 配置文件的存储位置
这些变量可以被存储在三个不同的位置：
1./etc/gitconfig 文件：包含了适用于系统所有用户和所有库的值。如果你传递参数选项’--system’ 给 git config，它将明确的读和写这个文件。 
2.~/.gitconfig 文件 ：具体到你的用户。你可以通过传递--global 选项使Git 读或写这个特定的文件。
3.位于git目录的config文件 (也就是 .git/config) ：无论你当前在用的库是什么，特定指向该单一的库。每个级别重写前一个级别的值。因此，在.git/config中的值覆盖了在/etc/gitconfig中的同一个值。
## 配置你的用户名和密码
当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：
```
$ git config --global user.name "wirelessqa"  
$ git config --global user.email wirelessqa.me@gmail.com 
```
## 配置你的编缉器
你的标识已经设置，你可以配置你的缺省文本编辑器，Git在需要你输入一些消息时会使用该文本编辑器。缺省情况下，Git使用你的系统的缺省编辑器，这通常可能是vi 或者 vim。如果你想使用一个不同的文本编辑器，例如Emacs，你可以做如下操作：
```
$ git config --global core.editor emacs 
```
## 检查你的配置
如果你想检查你的设置，你可以使用 git config --list 命令来列出Git可以在该处找到的所有的设置:
```
$ git config --list  
user.name=wirelessqa  
user.email=wirelessqa.me@gmail.com  
color.status=auto  
color.branch=auto  
color.interactive=auto  
color.diff=auto  
...  

```
你可能会看到一个关键字出现多次，这是因为Git从不同的文件中(例如：/etc/gitconfig以及~/.gitconfig)读取相同的关键字。 在这种情况下，对每个唯一的关键字，Git使用最后的那个值。 
　　
你也可以查看Git认为的一个特定的关键字目前的值，使用如下命令 git config {key}:
```
$ git config user.name  
wirelessqa  
```
## 创建文件存储GIT用户名和密码
在%HOME%目录中，一般为C:\users\Administrator，也可以是你自己创建的系统用户名目录，反正都在C:\users\中。文件名为.git-credentials,由于在Window中不允许直接创建以"."开头的文件，所以需要借助git bash进行，打开git bash客户端，进行%HOME%目录，然后用touch创建文件 .git-credentials, 用vim编辑此文件，输入内容格式：
```
touch .git-credentials
vim .git-credentials
https://{username}:{password}@github.com
```
进入git bash终端， 输入如下命令：
```
git config --global credential.helper store
```
执行完后查看%HOME%目录下的.gitconfig文件，会多了一项：
```
[credential]
 helper = store
 ```
重新开启git bash会发现git push时不用再输入用户名和密码
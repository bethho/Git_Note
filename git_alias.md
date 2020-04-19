# git alias

###### tags: `git`
Reference: 
## The command about *git alias*
git alias主要用於建立個人化的shortcut。
#### Example
```
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
```
```
git co
$ git commit 

git st
$ git status
```
global設定會記錄在~/.gitconfig
```
[alias]
        co = checkout
            br = branch
            ci = commit
            st = status
```
### Usage of git alias
#### Using aliases to create new Git commands
```
git config --global alias.unstage 'reset HEAD --'
```
```
git unstage fileA
$ git reset HEAD -- fileA
```

#### <font color="#33F6FF">Warning
有部分麻煩是換一台Machine就要重設，可以想想如何將整包alias都搬到另一台電腦</font>
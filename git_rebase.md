# git rebase

###### tags: `git`
Reference:
https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase
https://www.youtube.com/watch?feature=youtu.be&v=tukOm3Afd8s&fbclid=IwAR10qxBx44pVyFtD_mEbs50Z0CPeoBS6MKWLwudQQnDyXMlnpu1tMlAdi2o&app=desktop
## The command about *git rebase*
用於修改commit history:
1. 只要用來整理branch來合併到master，準確來說是重新定義base。
2. 合併commit讓history更加簡潔乾淨，主要用在push到remote的時候，方便其他協作者了解。(squash)
3. 可以更會commit的順序。(利用pick)
4. 修改commit的內容。(reword)

#### <font color="#dd0000">Note
不能用於以push到remot的commit，這樣會造成協作者的困擾，因為會用到不同的base</font><br />
### Usage of git rebase
例如想要將*feature_branch master*這個branch rebase的master最新的commit上
```linux=
# Create a feature branch based off of master
git checkout -b feature_branch master
# Edit files
git commit -a -m "Adds new feature"
git rebase master
```

```linux=
git rebase <base>
```
此指令是使用在當你已經利用checkout切換到要rebase的地方，<base>是新的base的地方

也可以直接用
```linux=
# git rebase <newbase> <ref>
git rebase master feature_branch master
```

最方便使用的指令是
```linux=
git rebase --interactive <base>
```
此指令可以讓使用者在base以上(含)的commit進行調整。
以下是相關的configuration
```linux=
pick 2231360 some old commit
pick ee2adc2 Adds new feature
# Rebase 2cf755d..ee2adc2 onto 2cf755d (9 commands)
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
```

此為更進階的運用
```linux=
 git rebase --onto <newbase> <oldbase>
```
這可以讓特定的refs當base的tip

**For example**
原本commit history如下圖:
```
   o---o---o---o---o master
        \
         o---o---o---o---o featureA
              \
               o---o---o featureB
```

```
git rebase --onto master featureA featureB
```
當使用此指令時，會產出以下的結果:
```
                      o---o---o featureB
                     /
    o---o---o---o---o master
     \
      o---o---o---o---o featureA

```
#### <font color="#33F6FF">Warning
我還是看不懂為甚麼????</font>

#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning
補實作</font>
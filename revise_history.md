# git commit --amend, git relflog

###### tags: `git`
Reference:
https://www.atlassian.com/git/tutorials/rewriting-history#git-commit--amend
https://www.atlassian.com/git/tutorials/rewriting-history/git-reflog
## The command about *git commit --amend*
用於更改最後一次的commit內容。主要可以純粹更改commit message或是commit遺漏的檔案。
### Usage of git commit --amend

#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning
git commit --amend不能使用在已push remote的commit上，因為使其他協作者confuse</font>

## The command about *git reflog*
此為User做過哪些commit、reset、rebase等動作都會記錄下來。預設的expiration date是90，但可以藉由--expire=time來修改gc.reflogExpire上的git configuration。

### Usage of git reflog
Timed reflogs
每個reflog entry都由他對應的時間，因此我們可以藉由時間點來指定是哪個動作紀錄。
The following are some examples of available time qualifiers:
* 1.minute.ago
* 1.hour.ago
* 1.day.ago
* yesterday
* 1.week.ago
* 1.month.ago
* 1.year.ago
* 2011-05-17.09:00:00
* 1.day.2.hours.ago

Example
```linux
git diff master@{0} master@{1.day.ago}
```
#### <font color="#dd0000">Note
疑問!!!!!會有1天前有兩個動作紀錄的可能嗎?還是就現在查詢時間往前一天的時間點中最接近的動作紀錄嗎?
</font><br /> 

git reflog可以看branch、stash等ref的動作紀錄。可以藉由這些動作紀錄來知道當出現問題是可以reset到哪一個動作。

Example
```linux=
git reflog
37656e1 HEAD@{0}: rebase -i (finish): returning to refs/heads/git_reflog
37656e1 HEAD@{1}: rebase -i (start): checkout origin/master
37656e1 HEAD@{2}: commit: some WIP changes
```
若想要回到HEAD@{1}，即可使用以下指令
```linux=
git reset HEAD@{2}
```

#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning</font>

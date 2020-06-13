# git reset

###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/undoing-changes/git-reset
## The command about *git reset*
* git reset is equivalent to executing git reset --mixed HEAD
* git reset無法刪除untracked files，這個需要用git clean
### Usage of git
```linux
git reset --hard
```
此指令會將commit指回去最新的commit，會將所有tracked files還原到最新的commit。因此所有tracked modified或new file的 資料都會不見。(reset Staging Index and Working Directory)
```linux
git reset --mixed
```
將Staging Index move to Working Directory
General, --mixed是會將當下和還原特定commit之間的差異存在Working Directory
```linux
git reset --soft
```
只有改變commit history，不會改變Staging Index和Working Directory。If tracked files is unstaged, but difference between HEAD and speciic commit. After soft reset, the tracked files will be staged. But Stage Index don't change.
```linux
git reset <file>
```
改變 <file>的stage成unstaged，這可以協助區隔與下個commit不相關的檔案。
#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning</font>
## Problems
* 如果有modified or add tracking file，但是執行git reset到特定commit hash，Working Directory存的是tracked files到commit hash的差異嗎?
> > 是的
* 
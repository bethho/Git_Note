# git stash
###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/saving-changes/git-stash#re-applying-your-stashed-changes
## The command about *git stash*
stash是一個temporarily shelves。它可以將目前除了unracked、ingnored files的git status記錄下來。<font color="#FFFF00">這有個好處可以讓使用者將考慮commit的內容先暫存在stash，而且可以記錄multiple stash，working directory可以繼續做更改，發現最後想要commit stash暫存的staged就可以re-applying to working direction。</font>
> 但是若working directory檔案已存在，則無法re-apply。不懂git stash的好處是甚麼???是我寫的黃色內容嗎???
```linux
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
$ git stash
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
nothing to commit, working tree clean

```
注意git stash不會記錄untracked、ignored files，若要紀錄則須加其他flag，請看底下的用法介紹。
```linux
$ script.js
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Untracked files:
script.js
$ git stash
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
Untracked files:
script.js
```
### Usage of git stash
#### Re-applying your stashed changes
```lunix
$ git status
On branch master
nothing to commit, working tree clean
$ git stash pop
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Dropped refs/stash@{0} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```
*git stash pop*會將最新的stash reapply到目前的working directory，並且將會在stash裡面移除。

若不想要在stash中移除，則將pop改成apply。
```linux
$ git stash apply
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
```
##### <font color="#dd0000">Note
如果working directory裡tracked file有變動(也就是有跟stash有同樣的檔案也有變動)，則無法使用git stash pop/apply。</font><br />
> 需要跟二中確認一下
#### Stashing untracked or ignored files
若想要將untracked files記錄到stash，則需用-u option (or --include-untracked)
```linux
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Untracked files:
script.js
$ git stash -u
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
nothing to commit, working tree clean
```
若想要將ignored files記錄到stash，則需用-a option (or --all)
```linux
git stash -a
```
![](https://i.imgur.com/DsRAhAT.png)
##### <font color="#dd0000">Note
-u無法搭配save來記錄message。</font><br />
#### Managing multiple stashes
```
$ git stash list
stash@{0}: WIP on master: 5002d47 our new homepage
stash@{1}: WIP on master: 5002d47 our new homepage
stash@{2}: WIP on master: 5002d47 our new homepage
```
可以利用stash list來看目前使用者存了哪些stash。但是可以發現上面的主要的內容都是**WIP on master: 5002d47 our new homepage**毫無區別性。
因此會建議使用者可以利用在存stash的時候可用以下指令給message來區別其他stash。
```linux
$ git stash save "add style to our site"
Saved working directory and index state On master: add style to our site
HEAD is now at 5002d47 our new homepage
$ git stash list
stash@{0}: On master: add style to our site
stash@{1}: WIP on master: 5002d47 our new homepage
stash@{2}: WIP on master: 5002d47 our new homepage
```
#### <font color="#dd0000">Note</font><br />
預設git stash pop是re-apply最新的儲存的stash(stash@{0})，若要指定要re-apply哪個stash可以在pop後面加stash編號。
```linux
$ git stash pop stash@{2}
```
#### Viewing stash diffs
可以利用以下指令來檢視summary of a stash
```linux
$ git stash show
index.html | 1 +
style.css | 3 +++
2 files changed, 4 insertions(+)
```
若要看完整的差異則在後面加上 -p option (or --patch)
```linux
$ git stash show -p
diff --git a/style.css b/style.css
new file mode 100644
index 0000000..d92368b
--- /dev/null
+++ b/style.css
@@ -0,0 +1,3 @@
+* {
+ text-decoration: blink;
+}
diff --git a/index.html b/index.html
index 9daeafb..ebdcbd2 100644
--- a/index.html
+++ b/index.html
@@ -1 +1,2 @@
+<link rel="stylesheet" href="style.css"/>
```
##### <font color="#00dd00">小分享 
預設都是看stash@{0}(也就是最新的stash)，若想要看特定的stash，則在後面加上stash編號。</font><br />
```linux
$ git stash show stash@{2}
$ git stash show -p stash@{2}
```
#### Partial stashes
stash除了可以以檔案為單位儲存，也可以line為單位儲存，也就是可以將tracked file的部分內容存於stash。
```linux
$ git stash -p
diff --git a/style.css b/style.css
new file mode 100644
index 0000000..d92368b
--- /dev/null
+++ b/style.css
@@ -0,0 +1,3 @@
+* {
+ text-decoration: blink;
+}
Stash this hunk [y,n,q,a,d,/,e,?]? y
diff --git a/index.html b/index.html
index 9daeafb..ebdcbd2 100644
--- a/index.html
+++ b/index.html
@@ -1 +1,2 @@
+<link rel="stylesheet" href="style.css"/>
Stash this hunk [y,n,q,a,d,/,e,?]? n
```
此選項跟之前commit hunck的選項一樣，在此不多加敘訴。
#### Creating a branch from your stash
```linux
$ git stash branch add-stylesheet stash@{1}
Switched to a new branch 'add-stylesheet'
On branch add-stylesheet
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Dropped refs/stash@{1} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```
此指令可以建立new branch並且將stash re-apply到working directory，也會將此stash從list移除。若不是new branch則會有Error。

#### Cleaning up your stash
```linux
$ git stash drop stash@{1}
Dropped stash@{1} (17e2697fd8251df6163117cb3d58c1f62a5e7cdb)
```
可以利用此指令刪除特定的stash。

若要刪除全部的stash，則可用以下指令。
```linux
$ git stash clear
```
#### How git stash works
> 不懂!!!!!!


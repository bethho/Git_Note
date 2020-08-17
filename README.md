# Git 學習筆記
###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/setting-up-a-repository
Pratice: https://www.katacoda.com/courses/git/playground
<font color="#dd0000">Note
建議在文件或資料夾前面加上" -- "，用以和flag做區隔
> Ex: git init --bare -- tmp
> tmp是&lt;directory&gt;</font><br />

## Progress
Date |　Title| Status
--- | --- |---
20200304|[Setting up a repository](/BBuUT_yeRoOBd5ow0vTVKQ)|<font color="#dd0000">[未完成]</font><br />
20200412|[git init](/2w-fSCdUTCabcknYVkxUCw)
20200418|[git clone](/ZcxsJHRbSwaHWV8Bp1e6XQ) | <font color="#00dd00">[待確認]</font><br />
20200418|[git config](/nU-8x3JsSU6xGocBBiy8sw) | <font color="#00dd00">[待確認]</font><br />
20200418|[git alias](/Hcoiky9-SnGB5PQlfNX3Ng)|<font color="#00dd00">[待確認]</font><br />
20200418|[git add](/S6mMWXILRx6IpSvq4npA3w)
20200420|[git commit](/7zFjIoDGQUm6ilfCMrlHMA)|<font color="#00dd00">[待確認]</font><br />
20200421|[git diff](/ZmoOuyutTb2xoapxzVFmDg)|<font color="#dd0000">[未完成]</font><br />
20200426|[git stash](/KLpD4skuSiyJQIDjB4b3jw)
20200426|[.gitignore](/ypHVT4jsQFimO6c3kSp4MA)|<font color="#dd0000">[未完成]</font><br />
20200612|[git reset](/0_EfpMB0TvSHVbEcvfs-eQ#)|<font color="#dd0000">[未完成]</font><br />
20200613|[git rm](/RD3P5d1gQSqZx5eJqaTpJA)
20200816|[git commit --amend, git relflog](/jcD0H3klRyyqLrlx8DB1YQ)
20200817|[git rebase](/8mXYjFAMQqmvNS3RBZkY-g)|補實作

### Status
tag | meaning
-- | ---
<font color="#dd0000">[未完成]</font><br /> | 代表內容未寫完
<font color="#00dd00">[待確認]</font><br /> |代表內容寫完了，但有些需要確認或是之後需要回頭補充

## Problem
#### git stash
1. diff的部分，是否有和git diff stash@{1}~ stash@{1}
2. git stash -p有甚麼用處
3. log不會
#### .gitignore
1. 如何在subdirectory revert某個被wildcard的文件
2. git不認為空資料夾是檔案，若要使git偵測到，可以加.gitignore的檔案
#### git log
3. commit為base，看status
4. 看specific file的紀錄
#### git tag
1. tag版本紀錄
#### git blame
#### git log -S
#### git checkout
在master中git checout特定檔案,讓特定檔案到某個commit狀態
git commit commit-id -- file.name
好習慣
git checkout commit-id，之後檢查是否想要的，然後用git checkout -b branch
#### git checkout v.s. git clean v.s. git revert v.s. git reset
* git checkout: 主要是向pointer只到過去的commit去做編輯，在這狀態下做的任何更改和commit，再回到master之後就會變不見或變孤兒，需要記錄commit需要轉到在其他branch才會記錄
* git clean: 適用於清除untracked file以及untracked directory(option -d)，由於git clean是直接將資料刪除，所以在clean.requireForce defaults to true的情況下，是需要有option才能執行
* git revert: 主要用於與他人合作的Project上，因為他不會刪除commit，這樣不會造成和remote衝突，或其他合作者有不同
* git reset: 主要用在local working directory，它是會直接刪除commit，將之間diff會加到stage
#### git apply



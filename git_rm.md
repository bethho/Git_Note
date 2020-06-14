# git rm

###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/undoing-changes/git-rm
## The command about *git rm*
git rm就是通知git要刪除tracking files。主要結合shell rm和git add的功能。在Working Directory和Staging Index刪掉此文件。
#### Why don't use rm?
直接使用rm只是將Working Directory的file刪除，還需要git add才能改變Staging Index的狀態。
### Usage of git rm
#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning</font>

### Problem
1. 用git rm後此文件就變成untracked嗎?rm加上git add還會是tracked file嗎?
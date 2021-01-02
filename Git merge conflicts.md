# Git merge conflicts
###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts
看懂程度: 90%  
花費時間:
    讀: 20200102 14:54-17:47 (共53m 21s)  
    記: 20200102 17:47-16:01 (共12m 26s)
檢討: 此篇過程有恍惚，導致讀的效率下降
## Conclusion
Git merge
1. 會自動merge可merge的部分
2. 當conflict發生只會影響當下merge的developer

此篇主要說明如何處理conflict發生
* 如果merge一開始就出錯，主要是因為有修改的檔案尚未commit就無法merge。可用git stash將修改的部分暫存起來，或是將修改的file進行commit。
* 若是merge中間遇到Error，代表兩個branch有動到相同的地方或刪除有一方改動的文件，這部分需要developer手動解決，其餘由Git自動merge。

### Problems
1. 如果BranchB developerB會引用A檔案，但是BranchA developerA把A檔案刪掉，兩個Branch merge會怎樣?
2. Tools for when git conflicts arise during a merge 
    * git merge --abort 為還原到merge之前?
    * git reset將conflicted files到之前commit的狀態? 
這樣有神麼差別嗎?
4. 

#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning</font>
# git diff
###### tags: `git`
Reference: 
## The command about *git diff*
### Usage of git diff
#### git diff HEAD(可省略) ./path/to/file
Show the changes that are not staged.
也就是若此file之前staged就會是現在的檔案和staged時的內容做diff。若沒有diff則跟local repository做diff。
#### git diff --cached(或--staged) ./path/to/file
Compare staged changes with local repository
#### Comparing files between two different commits
```
git log --prety=oneline //此指令我無法用
957fbc92b123030c389bf8b4b874522bdf2db72c add feature
ce489262a1ee34340440e55a0b99ea6918e19e7a rename some classes
6b539f280d8b0ec4874671bae9c6bed80b788006 refactor some code for feature
646e7863348a427e1ed9163a9a96fa759112f102 add some copy to body
$:> git diff 957fbc92b123030c389bf8b4b874522bdf2db72c ce489262a1ee34340440e55a0b99ea6918e19e7a
```
此指令用於比較兩個commit的差異。若只有一個commit id則是working directory跟此commit id做diff。使用者也可以指定要比較的檔案，只要在後面加檔案路徑。
Example :
```
git diff 957fbc92b123030c389bf8b4b874522bdf2db72c ce489262a1ee34340440e55a0b99ea6918e19e7a ./path/to/file
```
#### Comparing two branches (未實際操作)
可以是比較兩個branch最新commit的差異，也可以比較tag。
```
git diff branch1..other-feature-branch
```
..就等於空格，會比較branch1和other-feature-branch兩者最新commit所有檔案的差異。
```
git diff branch1...other-feature-branch
```
...是比較branch1和other-feature-branch兩者最新commit的共同檔案的差異。
#### Comparing files from two branches (未實際操作)
```
git diff master new_branch ./diff_test.txt
```
Compare兩個branch/commit/tag上的特定檔案
#### <font color="#dd0000">Note</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning</font>
不懂
- [ ] git diff --color-words
- [ ] git diff -highlight
- [ ] Comparing two branches
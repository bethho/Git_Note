# git commit
###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/saving-changes/git-commit
## The command about *git commit*
git commit是將stage changed files(也就是被git add過的檔案)存入Project history(也就是Record snapshots)

Git Recording snapshots是記錄<font color="#dd0000">整個檔案</font>不是紀錄<font color="#dd0000">差異的地方</font>(SVN就是只記錄差異的地方)。這也是為甚麼很多Git的操作會比SVN快，因為Git不需要集結所有的差異才能得到資料。
> 為甚麼我印象中Git每次Commit是紀錄差異呢?記得書是這樣寫的?
### Usage of git commit
#### Commit the staged snapshot
```
git commit
```
此指令會開啟txt editor讓使用者編輯commit message。當使用者完成編輯即可以存入project history。
```
git commit -a
```
Commit所有被追蹤(過去曾被git add加入過)且有改變的文件。
```
git commit -m "commit message"
```
此指令可以跳過開啟text editor，只要在指令中寫下commit message。
```
$ git commit -a -m "commit message"
git commit -am "commit message"
```
這是更powerful shotcut。若使用者只要commit已被追蹤也有改變的資料且不想要開啟text editor，就可以用此指令。(這樣可以省掉git add，但是要<font color="#dd0000">記住</font>無法commit untracked file除非此檔案已被git add)
'''
git commit --amend
'''
此指令是為了修改上一次的commit。
可以將stage changed files存在上一個commit節點，也可以更改上一次commit message，不會在history新增節點，但是commit id會改變。
此指令會開啟上一次commit message的編輯畫面來提供使用者修改。

#### <font color="#00dd00">小分享</font><br />
commit message的標準形式:
第一行用於summary且不要超過50的字，空一行後在解釋此次commit改變什麼。
Example:
```
Change the message displayed by hello.py

- Update the sayHello() function to output the user's name
- Change the sayGoodbye() function to a friendlier message
```

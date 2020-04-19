# git add


###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/saving-changes
## The command about *git add*
專案的發展通常都是在edit/stage/commit做循環，git add是將edited files的stage進行更改 (也可以說是加入到**the staging area** (是一個介於working directory和local repository的暫存空間) )。若已將相關的檔案都加入the staging area (stage snapshot)，才會利用git commit將其加入project history。可以利用*git reset*來復原commit或是stage snapshot。因此git add並不會更動到local repository，只有到git commit才會將the staging area的files存到local repository。
git add通常會結合**git status**來看working directory的狀態，確認是否要commit的files都有被add to the staging area。

#### The staging area
有一個好處，就是當你有好幾個更動的files且有一些沒有相關性，就可以藉由the stagind area切割開來，用不同commit來做儲存紀錄，這也可以方便對版本進行管理以及可以有更精確的commit。


#### git status
可以觀看目前working directory的檔案狀況。主要分為以下幾種狀況:
* 未加入the staging area (<font color="#dd0000">標示為紅色</font>)
    * untracked: new file還未加入local repository
    * modified: 已加入local repository的file內容有進行更改
* 加入the staging area (<font color="#00dd00">標示為綠色</font>)


### Usage of git add
#### 針對檔案做add
```
git add <file>
```
將此<file>的stag更改，可以在下次進行commit
#### 針對資料夾做add
```
git add <directory>
```
將此<directory>中所有有變動的files的stag都更改，可以在下次進行commit
#### 針對檔案內容做add
```
git add -p
```
此指令會變成互動式staging seesion來選擇部分檔案加入到下次的commit。它會將所有hunk(就是有變動內容區域)顯示出來，讓使用者決定哪個hunk要add。
它有底下5個選項:
* y: stage the chunk
* n: ignore the chunk
* s: split it into smaller chunks
* e: manually edit the chunk
* q: exit

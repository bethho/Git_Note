# Git Merge Strategy Options and Examples
###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/using-branches/merge-strategy
看懂程度: 60%  
花費時間: 
讀: 2021/1/3 18:50-21:07 (實際1hr 17m 16s)
寫: 21:07-21:37 (30m)
檢討:
1. 此篇閱讀過程有恍惚，導致讀的效率下降(可能不是很懂導致很容易無法專注)
1. 打字速度因不熟悉鍵盤導致盲打太慢
## Conclusion
說明Merge Strategy有哪些選項。
```
git merge -s <option>
```
Option:
1. recusive
可以用於處理rename的檔案，但是無法用於偵測copies
2. resolve
只能用於3 way merge algorithm，視為安全和快速
4. octopus(???)
多個branch(> 2)merge的預設方法，通常用於多個相似的feature branch。
如果有conflict就不能merge(???)
6. Ours(???)
用於多個branch merge，他會忽略全部feature branch都有改變的地方，他企圖合併相似的feature branches。
8. subtree(???)
是recursive的擴充。跟tree有關

Merge type
* Explict merge
明確在commit history留下merge commmit，也會說明parents of the merge commit。有些team不喜歡，認為會在history造成noise。
* Implict merge
可以透過(1)git rebase, fast-forward merge, (2)squash
### Problems
#### <font color="#dd0000">Note
merge前target branch可用squash來精簡commit，但是建議用explict merge比較好追溯何處進行合併</font><br />
#### <font color="#00dd00">小分享</font><br /> 
#### <font color="#33F6FF">Warning</font>
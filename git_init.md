# git init
###### tags: `git`

## The command about *git init*
### Usage of git init
```
git init
```
此指令需要在Project資料夾底下執行才能建立new repository。
```linux
git init <directory>
```
此指令可以指定Project資料夾即會在指定Project資料建立new repository。
因此不需要在Project資料夾底下執行
#### *git init* v.s. *git clone*
git init是所有git相關功能的最起源。git clone其實有包含git init，只是git clone是有已存在repository需要把它過來。git clone是先git init建立new repository，再從existing repository複製資料過來。
### Bare repositories
```linux
git init --bare <directory>
```
若此資料不需要做儲存或變動資料就用 *--bare*
#### <font color="#dd0000">Note</font><br />
<font color="#dd0000">測試bare respository是否能push, pull, clone(clone應該是可以的)</font><br /> 

### git init templates
```
git init <directory> --template=<template_directory>
```
這是希望new repository能依據一個git受定的範本(例如:HOOK, remote, username, editor等等設定)，這個git範本就在&lt;template_directory&gt;，注意&lt;template_directory&gt;是absolute path
#### <font color="#00dd00">小分享
git init也是有一個git範本，只是這個範本是預設的，其存在/usr/share/git-core/templates，所以也根據這樣的架構建立範本</font><br /> 

### seperate the directory of *.git* from &lt;directory&gt;
```
git init <directory> --separate-git-dir=<GIT DIR>
```
這是一個可以將 *.git* 資料夾放在特定的儲存位置，執行此指定後就會將 *.git*資料夾搬到&lt;GIT DIR&gt;，Project directory(或&lt;directory&gt;)底下會建立 *.git*文件記錄the link to &lt;GIT DIR&gt; 
此指令的使用情境有以下幾種:
* 為了將跟設定相關的資料(ex: .bashrc, .vimrc等等)都放置在同一個資料夾進行管理
* git history太過於龐大需要放置在其他較大的儲存區
* 希望這個git project是公開大家都可以使用的

#### <font color="#00dd00">小分享
此指令可以在existing repository執行，它就可以將現有的 *.git*資料夾搬到&lt;GIT DIR&gt;</font><br />

### <font color="#dd0000">Note</font><br />
<font color="#dd0000">Configuration需要去參考官方文件因為這些flag會被更新或修改</font><br />
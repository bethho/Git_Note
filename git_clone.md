# git clone

###### tags: `git`
Reference: https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-clone
## The command about *git clone*
git clone主要用來copy已存在的repository
不管是remote/local/bare repository都可以做clone。
git沒有指定central repository，人人都可以當central repository。
git clone下來的repository會設定好remote指回原本的repository。
### Usage of git clone
#### Cloning to a specific folder
```
git clone <repo> <directory>
```
將repository clone to &lt;directory&gt;，如果沒有&lt;directory&gt;則會以clone下來project名稱命名。
##### <font color="#dd0000">Note
If project name include .git, it will omit .git.
Ex: MyProject.git -> MyProject</font><br />

#### Cloning a specific tag
```
git clone --branch <tag> <repo>
```
此指令可以只clone特定的分支，可以節省clone時間和儲存空間。&lt;tag&gt;可以是tag或是branch名稱。若是tag它會將它的parent nodes都clone下來。
##### <font color="#dd0000">Note
若是以tag來進行clone，則不會有branch的名稱。</font><br />

#### Shallow clone
```
git clone -depth=n <repo>
```
此指令可以只clone深度為n的commit下來，可以節省clone時間和儲存空間。
##### <font color="#00dd00">小分享
常用的使用情境為:</font>
<font color="#00dd00">1. 當使用者想做自動化測試，它只要clone下來當下commit的程式來進行測試即可
2. 當程式有進行大改版，新版可能不會用到舊版的程式，使用者就只要clone跟新版相關的commit即可。</font><br /> 

#### git clone -mirror vs. git clone -bare
<font color="#33F6FF">Warning
此部分目前不常用，之後需要再回頭研究</font>

#### git clone --template
```
git clone --template=<template_directory> <repo location>
```
可以依&lt;template&gt;的設定範本來clone repository。

## Git URL protocols
<font color="#33F6FF">Warning
為目前理解，之後要確認其正確性</font>
- SSH
需要事先儲存金鑰
- GIT
- HTTP
若是HTTPS每次下載都要密碼
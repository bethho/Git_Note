# git config
###### tags: `git`

## The command about *git config*

### Usage of git config
git config常用的configuration是 user.name, user.email。此兩個configuration是在commit時不可或缺的。
#### git config levels and files
git config分為底下三個level:
* --local
此設定是在project底下，這些設定會記錄在the project/.git/config
* --global
此設定是在user底下，這些設定會記錄在~/.gitconfig
* --system
此設定是在this machine底下，這些設定會記錄在$(prefix)/etc/gitconfig

在使用設定的priority:
local > global > system

#### Other configuration
<font color="#33F6FF">Warning
需要使用時再回頭研究</font>


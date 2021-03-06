## 一、Git Command

|commands|description|
| ------------------------------- | ---- |
| cd /home/joy/MachineLearning/ |   enter local repository |
| git status| show all of changes|
| git commit -m [message] | commit changes to cache |
| git push| push changes in cache to repository |
| git init [project_name] | initial repository using current folder/ new folder |
| git log [--stat]| show history of commits |
| git clone [url]| clone a repository to local |
| git config --list	| show current configuration |
| git config [--global] user.name "[name]"|set user name used when commit|
| git config [--global] user.email "[email]"|set user email used when commit |
| git fetch [url]|fetch all changes |
| git add [dir] / [file1]...|add direction or files to cache |
| git rm [file1]...| delete file in cache or repository |
| git mv [ini_file] [end_file]|rename or move file |

## 二、游標移動
* `h / 方向左 / Backspace`向左移動
* `j / 方向下 / Enter`向下移動
* `k / 方向上 / -`向上移動
* `l / 方向右 / Space`向右移動
* `0 / ^ / Home`移至行首
* `$ / End`移至行尾
* `gg`移至檔首
* `G`移至檔尾

## 三、常態模式 Normal Mode

* `Esc`按下Esc退回到常態模式

### 1. 刪除指令 (delete)
* `x`刪除游標處的字符
* `X`刪除游標前的字符
* `dd`剪切一整行
* `dw`刪除一個單詞（中文不適用）
* `dG`刪至文檔尾
* `d1G`刪至文檔首
* `D`刪至行尾
* `d0`刪至行首

### 2. 取代和還原 (replace & undo)
* `r + anychar`取代游標處的字符
* `R`進入取代模式，取代字符直至Esc退出
* `cc / S`取代整行內容
* `c$ / C`取代至行尾
* `c^ / c0`取代至行首
* `~`游標處大小寫切換，非英文無效
* `u`撤銷undo

### 3. 複製和查找 (yank)
* `yy / Y`複製一整行
* `2yy / y2y`複製兩行
* `y^`複製到行首，不包含游標
* `y$`複製到行尾，含游標
* `yG`複製到檔尾
* `y1G`複製到檔首
* `p`小寫p粘貼到游標後
* `P`大寫P粘貼到游標前
* `*`查找下一個遊標處的單詞
* `#`查找上一個遊標處的單詞

## 四、插入模式 Insert Mode

* `i`進入插入模式 (Insert mode)，鍵入內容
* `Del`刪除游標處的字符
* `Backspace`刪除游標前一個字符

### 1. 進入插入模式
* `i`在游標前鍵入
* `a`在游標後鍵入
* `O`在游標上另起一行鍵入
* `o`在游標下另起一行鍵入
* `I`在行首鍵入
* `A`在行尾鍵入
* `J`將下一整行接至本行行尾，用空格分割

## 五、命令列模式 Cmdline Mode

* `:`進入命令列模式 ，左下角出現冒號
* `/`查找字符模式，输完后回车，`n`下一处，`N`上一处
* `?`反向查找字符模式`n / N`同上
* `ls`列出緩衝區buffer所有檔案

### 1. 開檔存檔
* `vim text.txt`用命令新建档案
* `vim -r 文檔名`緊急恢復文檔
* `e text.txt`編輯档案（不存在則新建）
* `w text.txt`寫入档案（若存在则按`!`重写）
* `bp / e#`編輯上一個檔案，快捷鍵`ctrl + ^`
* `bn`編輯下一個檔案
* `b + 檔案名或編號`切換到該檔案

### 2. 離開
* `w`存檔
* `w + 檔案名`另存他檔
* `q`退出，若有修改而沒存檔則警告
* `!q`捨棄修改，強制離開
* `wq`存檔並離開
* `x / ZZ`存檔並離開，若未修改則不存檔

## 六、標示模式 Visual Mode
* `v`選中遊標字符，可以上下左右選中
* `V`選中遊標行，可以上下選中
* `d`刪除選中區域
* `y`複製選中區域
* `>`選中區域右移一格
* `<`選中區域左移一格

## 七、快捷鍵

* `shift + ctrl + t`新標籤頁
* `shift + ctrl + n`新窗口
* `shift + ctrl + q`關閉窗口
* `shift + ctrl + w`關閉標籤頁
* `shift + ctrl + c`複製
* `shift + ctrl + v`粘貼
* `F11`切換全屏
* `shift + ctrl + f`查找
* `ctrl + ^`编辑上一个档案

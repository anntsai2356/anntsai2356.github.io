# IT新人必備手冊

# IT新人必備手冊
## 一台電腦
### 熟悉 Mac 操作
1. 快捷鍵（請參考 [Apple 官方說明](https://support.apple.com/zh-tw/HT201236)）
2. 手勢（請參考 [Apple 官方說明](https://support.apple.com/zh-tw/HT204895)）
   亦可在系統偏好設定

### 個人化環境設定

在「系統偏好設定」中設定一開始會用到的幾個項目
![](https://i.imgur.com/W4c0MyZ.png)

### Linux 基本概念
學習資源：[鳥哥的 Linux 私房菜](http://old.linux.vbird.org/linux_basic/)

請掌握 **第 6 章（Linux 檔案與目錄管理）** 和 **第 9 章（vim 程式編輯器）** 的內容，有空的話至少看到基礎文件的第 13 章節，此目的是為了確保你清楚知道自己對電腦做了什麼事情，以免憾事發生。
![](https://i.imgur.com/kxearkt.png)

## 安裝 MacOS 的套件管理工具：Homebrew
1. 按照[官網](https://brew.sh/index_zh-tw)指示安裝，執行以下指令
   ```
   /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
   ```
2. 看到這個後，輸入密碼（電腦的密碼）
   ![](https://i.imgur.com/ApQ632m.png)

3. 重啟 iTerm2，並輸入以下指令確認 homebrew 有在運作
   ```
   brew doctor
   ```
   
:::danger
題外話：
若未來有需要更新，在執行 `brew update` 之前，請確認目前作業系統版本是否符合homebrew 最新版本的最低要求。（homebrew 僅支援最近三個 MacOS 版本）

若低於最低要求，請勿貿然進行更新，建議先進行環境評估。
:::

## 準備好用的 Terminal 環境（非必要）

### 安裝取代預設 Terminal 的工具：iTerm2

1. [官網下載](https://iterm2.com/)並解壓縮開啟
2. 將程式移到 應用程式（application） 資料夾（系統會跳出視窗詢問）
3. 之後都改用 iTerm2 執行

### 安裝取 BASH 的工具：ZSH （Z shell）
1. 執行以下指令
   ```
   brew install zsh zsh-completions
   ```
2. 設為預設 shell
   ```
   sudo sh -c "echo $(which zsh) >> /etc/shells"
   
   chsh -s $(which zsh)
3. 重啟 iTerm2，並輸入以下指令確認是否安裝成功
   ```
   echo $SHELL
   ```

### 安裝框架用以管理外掛及主題：[oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh)
透過 curl 安裝
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
或
透過 wget 安裝
```
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 修改主題
1. 選擇主題
   選擇喜歡的主題（[查看主題列表](https://github.com/ohmyzsh/ohmyzsh/wiki/themes)）
2. 進入 ~/.zshrc 
   ```
   vim ~/.zshrc
   ```
   修改 `ZSH_THEME=”robbyrussell”` ，改成欲改的主題名稱
   ```
   ZSH_THEME="主題的名稱" 
   ```
   也可以選擇隨機顯示
   ```
   ZSH_THEME="random" #隨機主題
   ```
   修改完離開，執行
   ```
   source ~/.zshrc
   ```
:::info
【補充】Vim 的使用方法

進入 ~/.zshrc 
```
vim ~/.zshrc
```
![](https://i.imgur.com/tMpglAj.png)
:::
   
3. 安裝字體：Nerd Fonts
   ```
   # 字體安裝軟體，只需執行一次
   brew tap caskroom/fonts 
   # 安裝字體
   brew cask install font-hack-nerd-font 
   ```
   也可以查詢其他字體
   ```
   brew cask search nerd
   ```
   安裝完可以在此路徑設定字型：左上角的 iTerm2 >Preferences > Profiles > Text > Change Font
   ![](https://i.imgur.com/2SJOuhs.png)
   
   ```
   # command line 右邊想顯示的內容
   # POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status time) # <= status/顯示return code
   ```
4. 修改配色
   設定路徑：左上角的 iTerm2 >Preferences > Profiles > Colors > Color Presets...
   ![](https://i.imgur.com/t9kJUe9.png)

   內建配色不喜歡的話可以到 [iTerm2 Color Schemes]() 把整個 repo 下載到自己的電腦，再 從剛才下載下來的資料夾中找到 schemes 資料夾，裡面選一個喜歡的 color scheme import 到 iTerm2。
   ![](https://i.imgur.com/U6gbGOT.png)
   
[範例主題參考資料](https://medium.com/statementdog-engineering/prettify-your-zsh-command-line-prompt-3ca2acc967f)
[iTerm2 詳細設定參考資料](https://dustinhsiao21.com/2019/04/09/%E9%80%8F%E9%81%8E%E5%9C%A8-mac-%E4%B8%8A%E5%AE%89%E8%A3%9Diterm2-%E6%B4%BB%E6%BD%91%E4%BD%A0%E7%9A%84%E7%B5%82%E7%AB%AF%E6%A9%9F/)

## 安裝 git
```
brew install git
```
:::info
【延伸閱讀】

因公司使用 GitHub 作為 remote reposity，故遠端連線的方式可參考以下文章：
1. [SSH Key 設定](https://hackmd.io/@ann-tsai-27/BJSSh1mJL)
2. [Connect to GitHub using SSH Key](https://hackmd.io/@ann-tsai-27/H1sfpiqBu)
:::

## 安裝資料庫：MySQL

1. 查看可安裝的版本
   ```
   brew search mysql
   ```
   ![](https://i.imgur.com/tfEbbKb.png)


2. 安裝公司使用的 5.6 版本
   ```
   brew install mysql@5.6
   ```
:::warning
不小心使用 `brew install mysql` 安裝到最新的話，可以用 `brew uninstall mysql` 解除安裝，再安裝正確的版本。要注意其他資料夾中有關 MySQL 的檔案都清乾淨，可自行搜尋「Mac/解除安裝/MySQL」。
:::

3. 啟動 MySQL 
   ```
   mysql.server start
   ```
   若要終止運作，可輸入以下指令
   ```
   mysql.server stop
   ```
4. 修改環境變量，並確認已加入此路徑到 ~/.zhsrc 檔案最下面
   ```
   export PATH="/usr/local/opt/mysql@5.6/bin:$PATH"
   ```
   
5. 設定密碼
   也可不設密碼，使用 `mysql -u root` 登入，但還是建議要有密碼比較安全。
   ```
   # 啟用 MySQL （已啟用則不需再執行）
   mysql.server start
   
   # 執行安全設定
   mysql_secure_installation
    
   NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
         SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

   In order to log into MySQL to secure it, we'll need the current
   password for the root user.  If you've just installed MySQL, and
   you haven't set the root password yet, the password will be blank,
   so you should just press enter here.

   Enter current password for root (enter for none): 第一次設定，直接按 Enter 鍵即可
   OK, successfully used password, moving on...

   Setting the root password ensures that nobody can log into the MySQL
   root user without the proper authorisation.

   Set root password? [Y/n] 按 Y 設定資料庫 root 密碼
   New password: 輸入新密碼
   Re-enter new password: 再次輸入新密碼
   Password updated successfully!
   Reloading privilege tables..
    ... Success!
    
   By default, a MySQL installation has an anonymous user, allowing anyone
   to log into MySQL without having to have a user account created for
   them.  This is intended only for testing, and to make the installation
   go a bit smoother.  You should remove them before moving into a
   production environment.

   Remove anonymous users? [Y/n] 按 Y 移除anonymous users
    ... Success!

   Normally, root should only be allowed to connect from 'localhost'.  This
   ensures that someone cannot guess at the root password from the network.

   Disallow root login remotely? [Y/n] 按 Y 關閉 root 遠端登入
    ... Success!

   By default, MySQL comes with a database named 'test' that anyone can
   access.  This is also intended only for testing, and should be removed
   before moving into a production environment.

   Remove test database and access to it? [Y/n] 按 Y 移除資料表 test
    - Dropping test database...
    ... Success!
    - Removing privileges on test database...
    ... Success!

   Reloading the privilege tables will ensure that all changes made so far
   will take effect immediately.

   Reload privilege tables now? [Y/n] 按 Y 重新載入資料表權限
    ... Success!

    
   All done!  If you've completed all of the above steps, your MySQL
   installation should now be secure.

   Thanks for using MySQL!
   ```

6. 使用密碼登入 Mysql 
   ```
   mysql -u root -p
   ```

### 其他指令

* 離開
  ```
  exit 或 quit 或 \q
  ```
* 忘記密碼，改密碼
  ```
  # 停止運作
  mysql.server stop
  
  # 跳過權限
  mysqld_safe --user=mysql --skip-grant-tables --skip-networking &
  
  # 以無密碼模式登入 MySQL
  mysql -u root
  
  # 進入 MySQL 修改密碼
  use mysql;
  update user set password=password("你的新密码") where user="root";
  flush privileges;
  quit
  ```
  
## 安裝 PHP
   公司新主機使用 7.4 版本，故下載此版本即可。
   ```
   brew install php@7.4
   ```

## 下載資料庫 GUI 工具：Sequel Ace
[官網下載](https://sequel-ace.com/)

## 下載 FTP 連線工具：Cyberduck

[官網下載](https://cyberduck.io/)

![](https://i.imgur.com/axZY2jR.png)

## 安裝程式編輯器：VS Code
[官網下載](https://code.visualstudio.com/)
這會是你工作時的好夥伴

## 安裝 API 測試工具：Postman
[官網下載](https://www.postman.com/downloads/)
   
###### tags: `教學` `後端` `前端` `新人`

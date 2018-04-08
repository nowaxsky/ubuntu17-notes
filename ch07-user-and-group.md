# Ch07 帳號與管理
## 1. 帳號
* 雖然系統有區分大小寫, 但email不分, 所以建立帳號時一律小寫
* UID是user ID的簡稱
* root的UID為0, 故只要將任意帳號的UID改為0則權限同root(並非完全相同, root還是有不可取代的權限)

## 2. 帳號管理
* 記載帳號的檔案為 /etc/passwd
* 記載密碼的檔案為 /etc/shadow
* 帳號相關指令(e.g, user1):
    * 新增帳號:
        ```
        $ useradd user1
    * 新增UID為1001, GID為2001的帳號:
        ```
        $ useradd -u 1001 -g 2001 user1
    * 修改帳號:
        ```
        $ usermod user1
    * 刪除帳號:
        ```
        $ userdel user1
    * 刪除帳號(連同家目錄):
        ```
        $ userdel -r user1

## 3. 群組管理
* 記載帳號的檔案為 /etc/group
* 群組相關指令(e.g, group1):
    * 新增群組:
        ```
        $ groupadd group1
    * 新增GID為2001的群組:
        ```
        $ groupadd -g 2001 group1
    * 將使用者user1加入群組:
        ```
        $ gpasswd -a user1 group1
    * 將使用者user1移除群組:
        ```
        $ gpasswd -d user1 group1
    * 刪除群組:
        ```
        $ groupdel group1
* 一個帳號可以擁有多個群組, 則該帳號將有所有群組的功能
* 有效群組:
    * 查詢該帳號所有支援的群組(第一個輸出的為有效群組)
        ```
        $ groups
    * 該帳號新增檔案或是目錄時將根據此有效群組
    * 切換有效群組: 只能在支援群組中切換(下例假設該帳號支援users群組)
        ```
        $ newgrp users



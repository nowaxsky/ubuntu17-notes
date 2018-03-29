# ubuntu17-05 Linux 開關機
## 1. 啟動層級(run level)
* 在ubuntu上面僅有定義三個層級分別如下: 
    1. 0 關機指令
    1. 2 圖形介面(default)
    1. 6 重新開機
* 可以輸入指令 `$ init 0-6` 來使用

## 2. 系統初始化
* 初始化相關指令
    ```
    $ systemctl start service  
    $ systemctl stop service  
    $ systemctl disable service  
    $ systemctl enable service
## 3. 關機
* 關機指令(以下同)
    ```
    $ init 0  
    $ shutdown -h now
## 4. 重新開機
* 重新開機指令(以下同)
    ```
    $ init 6  
    $ shutdown -r now  
    $ reboot
## 5. 程序
* 列出所有程序
    ```
    $ ps -ef   
* 列出程序1805開啟的所有檔案 
    ```
    $ lsof -p 1805  
* 列出開啟檔案 test.txt 的程序
    ```
    $ lsof /usr/cpm/test.txt   
* 顯示帳號 cpm 所執行的程序與相關資訊(按q離開)  
    ```
    $ top -u cpm 
* 顯示程序 1805 相關資訊(按q離開)
    ```
    $ top -p 1805  
## 6. 訊號管理
* 中斷程序(同Ctrl + c)
    ```
    $ kill -2 1805
* 強制中止
    ```
    $ kill -9 1805
* 根據指定名稱傳遞訊號, ex: 將所有關於cat指令的程序刪除
    ```
    $ killall -9 cat
* 查看內部程序溝通  
(有時使用kill會產生系統資源仍被占用無法釋出的問題,  
可以使用IPC來檢查是否有被占據的內部程序)
    ```
    $ ipcs  
    $ ipcrm []
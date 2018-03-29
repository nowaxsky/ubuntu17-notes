# ubuntu17-06 Linux 檔案系統
## 1. 硬碟分割
* 若使用VirtualBox需要先新增一個SATA硬碟, 這時候在/dev/下才會出現sdb可供操作使用
* 透過 `$ fdisk /dev/sdb` 劃分分割區
* 進入互動模式後, 相關指令如下:
    1. `$ p` 查看狀態
    1. `$ n` 建立新的分割區
    1. `$ w` 建立完成後儲存離開, 若不想保留可以 Ctrl + c 中止
    1. `$ t` 變更分割區的類型, 見 2. 硬碟分割類型, 在Hex code中輸入數字即可
    1. `$ t` 刪除分割區
* 當新增完三個主分割區後, 接下來剩餘的空間可做成延伸分割區(因為主分割區只允許四個)


## 2. 硬碟分割類型
* 一般使用有4種: 
    1. (82) Linux swap: 虛擬記憶體
    1. (83) Linux: 實體分割區
    1. (85) Linux extended: 劃分4個以上分割區則需使用此類型
    1. (8e) Linux LVM: 使用LVM時使用

## 3. 檔案系統格式化
* 檔案系統需要格式化後才能使用, 指令如下:
    * ext2: 
        ```
        $ mke2fs /dev/sdb1  
        $ mkfs.ext2 /dev/sdb1
    * ext3:
        ```
        $ mke2fs -j /dev/sdb1  
        $ mkfs.ext3 /dev/sdb1
    * ext4:
        ```
        $ mkfs.ext4 /dev/sdb1
## 4. 掛載
* 掛載意旨把裝置和某個特定目錄連接, 例如在Windows中插入USB可能是F槽,  
意旨USB被掛載到這個F槽的目錄下. 假設在Linux中, 要將sdb1的區域掛載到/opt, 語法如下:
    ```
    $ mount /dev/sdb1 /opt
* 使用umount可卸載:
    ```
    $ umount /opt
## 5. 檔案類型
* 輸入 `ls -l []` 可以查看目錄底下的檔案類型, 可由第一個英文字母來判斷:
    1. -為一般檔案
    1. d為目錄
    1. l為連結
    1. b為block special
    1. c為character special
    1. s為socket

## 6. 系統目錄介紹
* /bin 必要的指令執行檔
* /boot 靜態的開機啟動檔, 核心檔和設定檔
* /dev 硬體裝置
* /etc 本機的系統設定檔
* /media 可移動裝置的掛接點, 如CD, USB等
* /opt 額外的軟體或是套件
* /sbin 必要的系統執行檔, 僅供管理者使用

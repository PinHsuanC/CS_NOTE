# CS_NOTE 
## Linex指令
> * cd-變換目錄  
> * pwd-顯示目前的目錄  
> * ls-顯示目錄的的所有內容  
> * cat-查看檔案內容  
> * rmdir-刪除一個裡面是空的空目錄  
> * mkdir-建立一個新目錄  
## 編輯文檔
> * nano-在終端機編輯文字檔案   
>> **Ctrl+X-離開**  
>> **Ctrl+C-顯示游標所在**  
>> **Ctrl+W-查詢命令**  
> * vim-在終端機編輯文字檔案  
>> **i鍵-可進入編輯模**  
>> **esc-離開編輯模式**  
>> **:q-不儲存離開**   
>> **:wq-儲存離開**  
>> **:q!-強制離開**   
>> **:w-將編輯的資料寫入檔案中**  
## Linux使用者與群組  
* 身份分類：  
> * user (owner)  
> * group  
> * others	
* 群組 (group) 的主要功能  
> * 將帳號歸類，有助於類似專案開發  
> * 每個使用者均可加入多個群組  

**_Linux為多人多工系統，會有多人同時使用同主機進行工作的情況發生，  
考慮每個角色的使用權限及偏好不同，因此有不同的檔案擁有者角色。_**  

| d | r | w | x | r | w | x | r | w | x | root | root | 293 | test.txt |
|:-------:|:------:|:------:|:-------:|:------:|:------:|:-------:|:------:|:------:|:-------:|:------:|:------:|:-------:|:-----:|
| 目錄   | 可讀取(4) | 可寫入(2) | 可執行(1) | 可讀取(4) | 可寫入(2) | 可執行(1) | 可讀取(4) | 可寫入(2) |  可執行(1)  |  擁有者  |  擁有群組  | 檔案大小   |  檔案名稱  |  

**Q:MacOS系統有的無法退出Vim編輯模式?  
A:可用fn鍵+esc鍵，正常是esc鍵。**  

## Linux壓縮檔案  
* 壓縮檔案的優點：  
> * 備份資料的時候，方便整理。  
> * 將檔案變小，節省電腦硬碟的空間。  
> * 將無數個散亂的檔案打包成一個較小的檔案，亦方便資訊在網路上流通。  
> * 可以視情況進行加密。  
* 壓縮檔案的概念：  
> * 電腦最小的計量單位應該是 bits (1 byte = 8 bits)因此將許多閒置的空間釋出，即可將檔案占用的空間減少。  
> * 將重複的資料進行統計記錄。


* 需要在記憶體很小的機器（如小於 128MB）上解壓縮時，則選擇gzip格式。
* 需要在很簡單、沒有什麼工具可用的機器解壓縮時，則選擇gzip格式。
* 需要節省網路頻寬、縮短下載所需要的時間時，則選擇xz格式。
* 需要有最好的壓縮率時，則選擇tar.xz格式。 
 
* gzip
> * 壓縮：gzip FileName
> * 解壓縮：gunzip FileName.gz , gzip -d FileName.gz

* xz  
> * 壓縮：xz -z FileName  
> * 解壓縮：xz -d FileName.xz

* tar.gz
> * 壓縮：tar -zcvf FileName.tar.gz DirName
> * 解壓縮：tar -zxvf FileName.tar.gz  

## Linux檔案搜尋  
* find [path] [option] [action] filename  
> * option  
> -size EX：找出大於500M的檔案 → **-size +500M**  
> -name EX：找出為照片的檔案 → **-name "*.jpg"**  
> -type EX：**-type f → 一般檔案**;**-type d → 一般目錄**  
> -user EX：同時找兩個擁有者的檔案 → **-user user1 -o -user user2**  
>  * action - exec  
>  -ls  
>  -print  

## Linux檔案內容查閱  
### cat-從第一行顯示檔案內容、形成新檔案  
> * cat -n file1 > file2→把file1的檔案內容加上行號後輸入file2檔案  
>> * -n → 由1開始對所有輸出的行數編號  
>> * ">" → 將多個文件覆蓋到目標文件中  
>> * ">>" → 將多個文件追加到目標文件中

### tac-從最後一行開始顯示  
> * tac -r -s 'x\|[^x]' test.log → 一個接著一個字符的反轉一個文件   
>> * -r → 將分隔符作為基礎正規表達處理  
>> * -s → 使用**String**作為分隔符代替默認的換行符

### more 一頁一頁的顯示檔案內容  
> * more +20 testfile→從第20行開始顯示testfile的文檔內容  
>> * ENTER：向下n行(default為1行)  
>> * Ctrl+F/SPACE：向下滾動一屏  
>> * Ctrl+B：返回上一屏

### ess 與 more 類似，顯示檔案室允許用戶既可以向前又可以向後翻頁閱讀檔案  
> * ps -ef |less→ps查看進程信息並通過less分頁顯示	   
>> * j→下一行  
>> * k→上一行  
>> * G→移動到最後一行  
>> * g→移動到第一行

### head/tail 只看頭/尾巴幾行
> * head -n 20 state.txt | tail -10 → 顯示11~20行的內容

## Port通訊埠 
* Port通訊埠是什麼？有什麼用途？   
> * 若將電腦比喻成郵局，**連接埠就像窗口，負責各種不同的業務**    
> * 通訊埠是一種在電腦網路中藉由軟體所建立的服務   
* 按Port號分佈劃分  
> * 知名Port（Well-Known Ports）  
> * 動態Port（Dynamic Ports） 
* 按協議類型劃分  
> * TCP   
> * UDP   
> * IP   
> * ICMP（Internet控制消息協定）  

## TCP/IP   
* TCP/IP是什麼？  
> * 指傳輸控制協議、網際網路互聯協議，又名網絡通訊協議，是**Internet最基本的協議**、**Internet國際網際網路的基礎**。
> * 是供連接網際網路的計算機進行通信的**通信協議**  

* TCP/IP依其功能不同分到四個階層之中（這四個模型常視為是簡化的七層OSI模型）
> * 應用層application layer
> * 表現層presentation layer  
> * 會議層session layer  
> * 傳輸層transport layer  
> * 網路層network layer  
> * 資料連結層data link layer  
> * 實體層physical layer3

## Linux網路相關  
> * add : 新增一條路由規則   
> * del : 刪除一條路由規則  
> * -net : 目的地址是一個網路  
> * -host : 目的地址是一個主機  
> * target : 目的網路或主機  
> * netmask : 目的地址的網路掩碼   
> * gw : 路由資料包通過的閘道器  
> * dev : 為路由指定的網路介面












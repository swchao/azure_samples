# 3.3 新增服務端點

新增虛擬機器後，在虛擬機器內開啟的連接埠並不會直接對外服務，需要額外開啟**服務端點**（endpoint）來對應虛擬機器的連接埠（port），比方說 Web 伺服器可能會開在 8080 這個連接埠，這時需要開啟一個服務端點在 80 對應到虛擬機器的 8080 連接埠，這樣使用者才能透過網路存取到這個虛擬機器的連線服務。

本文介紹如何開啟對應到虛擬機器的連接埠，並且以 Ubuntu Linux 的操作來做示範。

## 事前準備

* 瞭解如何建立虛擬機器，可以參考 [3.1 建立虛擬機器](chapter03/01_create_virtual_machine.md)。

## 如何操作

假設已經在虛擬機器裡安裝了一個 MySQL 伺服器，在預設狀況下，MySQL 伺服器會開啟連接埠 **3306** 來提供服務，但還必須在虛擬機器的管理後台新增一個服務端點，指向這個連接埠。登入管理後台之後，在**端點**的頁面來進行服務端點的修改。

![修改服務端點的設定](https://skgitbook.blob.core.windows.net/azurerecipestw/3-3-1-setting-endpoint.png)

點擊下方命令列的**加入**按鈕，在跳出的對話盒中，點選**加入獨立端點**：

![加入獨立端點](https://skgitbook.blob.core.windows.net/azurerecipestw/3-3-2-add-a-new-endpoint.png)

下一步，先在**名稱**的欄位設定這個服務端點的用途，然後指定**通訊協定**（大部份的網路服務會開在_TCP_），而**公用連接埠**就是對外開放的連接埠位置，**私用連接埠**則是對應到虛擬機器中開啟的連接埠位置，因為我們要開啟的是 MySQL 的服務，所以填寫的內容就如圖所示（如果虛擬機器開了一個 Web 服務在連接埠 8080，而對外開放的連接埠是 80，那在這裡公用連接埠就是設 _80_ 而私用連接埠則是設定為 _8080_）。

![設定端點對應](https://skgitbook.blob.core.windows.net/azurerecipestw/3-3-3-setting-port-mapping.png)

最後按下完成的按鈕，就會開始建立服務端點了。若要刪除這個服務端點，也是在同一個頁面中，選擇欲刪除的服務端點，再點擊下方命令列中的**刪除**按鈕來刪除服務端點。

## 注意事項
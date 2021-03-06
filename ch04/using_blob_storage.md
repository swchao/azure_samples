# 使用 Blob 儲存體服務儲存檔案及提供檔案服務

## 需求

將檔案儲存在 Blob 儲存體中，並且經由公開或驗證後取得到的 URL 來存取檔案，以用在分散網站靜態檔案存取以及其它永久儲存或提供其它 Azure 服務使用。
  
## 事前準備

  * 擁有 Microsoft Azure 訂閱服務

## 解決方法

### 建立儲存體帳號

進入 [Microsoft Azure 管理後台](https://portal.azure.com/)，在左側面板找到 **新增** 的按鈕，按下後選擇 _儲存體_

![建立儲存體帳號](https://skgitbook.blob.core.windows.net/azurerecipestw/ch04/create_new_storage.png)

_**圖 1**_. 建立儲存體帳號

建立儲存體服務的步驟很簡單，一樣是要設定_名稱_、_資源群組_、_資料中心位置_這樣的欄位，不過因為儲存體提供的是永久性（persistant）的資料儲存，最基本就會在同一個資料中心裡複寫三份備援（不會算 3 倍價錢），但若您願意用費用換來更多的備援，還可以選擇異地備援等方案，這可以在 **定價層** 的欄位中選擇。

![選擇不同等級的備援](https://skgitbook.blob.core.windows.net/azurerecipestw/ch04/storage_price_plan.png)

_**圖 2**_. 選擇不同的定價方案

不同的價格方案最主要的差異就是備援的方式，除了高階（premium）的儲存體方案是 10 倍的效能之外（單一檔案 _5,000_ IOPS）。而顯示的價格是 _**100GB 一個月**_的預估價格，你可以根據實際用量按比例去計算出預估花費。

設定完成後就可以立即建立，如果沒有其它的錯誤就會顯示儲存體的管理面板，比較常用的功能會像是找到存取的金鑰，因為預設狀況下要透過帳戶名稱 + 金鑰(主要或次要其中一把)來驗證存取。而金鑰資訊要妥善保存使用，如果不慎外流的話，也可以利用上面的 **重新產生** 按鈕產生新的金鑰並且註銷原本的金鑰。

![取得金鑰內容](https://skgitbook.blob.core.windows.net/azurerecipestw/ch04/get_storage_key.png)

_**圖 3**_. 取得金鑰內容

另外，在建立儲存體帳號時，也會根據選用的名稱配發一個 URL （_http://名稱.blob.core.windows.net/_）使用，如果想要換成自己的網域，也可以在自訂網域中設定。

![自訂網域](https://skgitbook.blob.core.windows.net/azurerecipestw/ch04/setting_custom_domain.png)

_**圖 4**_. 自訂網域

### 容器以及上傳檔案

### 存取檔案
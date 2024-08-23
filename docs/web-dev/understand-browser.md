# [Web]理解瀏覽器進程   
## 打開一個新的 Chrome 裡面會包括    
### Browser Process    
    功能：主要負責介面顯示、使用者互動、子進程管理，同時提供 儲存等功能。   
    數量：1   
### GPU Process   
    功能：用於 3D 繪製等   
    數量：1   
### Network Process   
    功能：主要負責頁面的網路資源下載。   
    數量：1   
### Render Process （瀏覽器內核）   
    功能：核心任務是將 HTML、CSS、Javascript、轉換成使用者可以互動的網頁，排版引擎 Blink 和 Javascript 引擎 V8 都是運行在此進程中。   
    數量：默認情況下，Chrome 會為每個 Tab 標籤創建一個 Render Process。   
### Plugin Process   
    功能：主要負責插件的運行，因插件進程容易發生崩潰，因此需要透過單獨的插件進程來隔離以保證插件崩潰不會對瀏覽器和頁面造成影響。   
    數量：使用插件時創建   
   
## 瀏覽器內核（Render Process）的多線程   
### GUI 渲染線程   
    功能：負責渲染瀏覽器介面，解析 HTML、CSS、創建 DOM tree 以及 RenderObject tree、佈局、繪製等。   
    GUI渲染線程與JS引擎線程是互斥的   
### JS 引擎線程   
    功能：負責解析執行 Javascript 的主線程，在一個 Render Process 中，永遠都只會有一個 JS 線程在執行 Javascript    
### 事件觸發線程   
    功能：主要用於控制事件，例如游標、鍵盤等，當事件被觸發時，就會把事件的處理 function 推進事件對列中，等待 JS 線程來執行。   
### 定時器觸發線程   
    功能：主要控制 setInterval 和 setTimeout ，用來計時，計時完畢後把定時器的處理 function 推進事件對列中，等待 JS 線程來執行。   
### 異步 http 請求線程   
    功能：通過 XMLHttpRequest 連接後 ，通過瀏覽器新開的一個線程，監控 readyState 狀態變更時，如果設置了該狀態的 callback function ，則將該狀態的處理 function 推進事件對列中，等待 JS 線程來執行。   
   
   

# **02 - JS and CSS Clock**

## **Intro**

用 JS 與 CSS 搭配製作一個實時的時鐘效果。

[DEMO](https://yangjiesu.github.io/JavaScript30/02 - JS and CSS Clock/index-CloudSu.html)

## **Step**

#### Step1. 製作時針、分針、秒針
利用 class`hand` 樣式來表現出時分秒針的樣式

#### Step2. 設定定時器
利用 ` setInterval(setDate, 1000);` 每秒取得當前時間

#### Step3. 利用當前時間來取得對應角度
將每秒取得的時間在 `setData` 裡面取出，並計算出對應角度
再透過 `element.style.tranform` 來變更CSS效果，產生位移的感覺。

### **Date()**
取得時間的函數，一定要搭配 new 來使用 `new Date()`
`date.getSeconds()`：取得當前秒數
`date.getMinutes()`：取得當前分鐘
`date.getHours()`：取得當前小時

### **setInterval()**
定時器，有兩個參數 `setInterval(callback, time)`
第一個是要執行的function，第二個是時間(ms)

## **CSS語法&備註**

### **transform-oragin**
變形的軸心，預設為物件的中心點，
設定為 100%(right) ，設定中心點在最右方，可以使其從時鐘面的中心點開始旋轉。

## 修正

### 調整角度及指針樣式
為了要讓指針從12點方向(0點)開始計算，  
原始範例將指針 `.hand` 都加上了 rotate(90deg) 來轉，  
並在計算時間的function內最終結果也都 +90，  
修正成 `.clock-face` 直接將整個區塊轉90度，  
這樣在計算時就不用+90，可以用最大360來做計算了。

### transform:rotate的彈跳問題
作者最後有提到一個小問題，若指針在354度切到0度時，
會使指針往前彈回去，這是因為有使用transtion，在角度做切換時會加上的動畫效果，
354→0度會認為是往前，而非轉一圈回到起點，所以動畫先往前轉到0。
為了避免這個反彈的怪現象，加上了一個function來處理角度
````javascript
function setRotate(deg) {
if (deg === 0) {
    document.querySelector('.hand').style.transition = 'all 0s';
} else {
    document.querySelector('.hand').style.transition = 'all 0.05s';
}
return `rotate(${deg}deg)`;
}
````
判斷計算角度為0時，把動畫效果關閉，這樣就可以避免了！

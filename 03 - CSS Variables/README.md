# **03 - CSS Variables**

## **Intro**

用 JS 與 CSS 搭配製作一個即時濾鏡效果。

[DEMO](https://yangjiesu.github.io/JavaScript30/03 - CSS Variables/index-CloudSu.html)

## **Step**

#### Step1. 定義變數
利用 :root 與 var() 來定義 css 參數;

#### Step2. 綁定控制列
利用 addEventListener 綁定 HTML 控制列，
並更新 CSS 變數來達到即時調整效果。

## **JavaScript語法&備註**
#### **dataset**
用 `dataset` 可以取出對象的 `data-*` 屬性，也等同於 `getAttribute`
````javascript
<div id="test" data-number="123"></div>
document.querySelector('#test').dataset.number // 輸出123
document.querySelector('#test ').getAttribute('data-number'); // 輸出123
````

### **style.setProperty()**
等同於style.cssPropertyName
````javascript
style.setProperty('padding', '15px');
/* 等同於 */
style.padding = '15px';
````

## 探索
在CSS中要使用兩個以上的濾鏡效果寫再一起就好，
如果分開來的話會變成覆蓋：
````css
/* 這樣會變成覆蓋，剩下garyscale的效果 */
img {
    filter: blur(10px);
    filter: grayscale(10%);
}
/* 寫在同一處，才能有兩個效果 */
img {
    filter: blur(10px) grayscale(10%);
}
````

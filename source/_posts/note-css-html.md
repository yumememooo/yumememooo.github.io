---
title: "[HTML & CSS][✍ 筆記] 初學 HTML & CSS 與練習"
tags:
  - note
  - css
  - html
  - ing
categories:
  - [Tech., Web,front-end,html]
  - [Tech., Web,front-end,css]

date: 2020-09-15 20:27:29
---

[✍ 持續更新]

> 練習CSS & HTML 操作相關筆記．

<!--more-->

### HTML

#### Html 基礎
- HTML 文件 (HTML document) 
- 標籤 (tag)<tagname>...</tagname>包圍著語意 (semantic) 內容(Content)區塊稱作 HTML 元素 (HTML element)，不同標籤表達不同語意
- 空元素 (Empty Element / Void Element)
有些 HTML 元素是不允許有內容的，稱之為空元素。沒有結束標籤
常見包括
```
<br>換行 <hr> <img>圖片 <input>輸入 <link> <meta>
```
- HTML 標籤中還有屬性 (Attribute)，來提供該標籤的額外資訊

##### 區塊元素 
- display預設為block，區塊元素排列都會另起一行，除非被改變
- 可設置寬高 width hight
- 默認情况下，其寬度自動填满其父元素寬度，即寬度100%
- 高度，行高以及頂和底邊距都可控制；

```
常見包括 div、p、h1~h6、
ul、ol、li、
dl、dt、dd、
form、table、hr、
blockquote 、
address、menu、pre.....等等
```
##### 行內元素
- display預設inline，除非被改變
- 設置寬高無效，只能由内容撑起来
- 行内元素会排列在同一行，直到一行排不下，才會換行，其寬度隨元素的内容而變化。
- 設置上下margin、padding无效，左右padding 、margin有效
```
常見包括
span、em、i、b、strong、
a、img、input、br、select、textarea、q、bdo、
sub、sup...等等
```
- 行內不能包含區塊元素
*可變元素 依上下文決定

Ref:https://www.jianshu.com/p/9fa96ece88f1
#### 撰寫規則
- 屬性值用單引號雙引號都可以
- 標籤與屬性大小寫都可以，常見且建議是固定使用小寫 (lowercase)。
- 雙引號間的屬性值不能空白
什麼是HTML 標籤Tag - HTML 語法教學Tutorial - Fooish 程式技術
https://www.fooish.com/html/tag.html


#### 語意標籤
HTML5中新增了語意化標籤(Semantic Elements)，目的是為了讓標籤(Tag)更具意義，以加強文件的結構化，讓搜尋引擎更清楚了解
```
Header 可於body內或是article或是section代表頁首或是首要區塊
Nav 導覽區塊
Main 主要區塊，整頁只有一個
Article 包覆文章
Section 區塊
Div 無意義為包裹區塊排版用
Aside 用來代表主內容的附加內容，未必是側邊欄，廣告等等都可以用
Footer 頁尾
Time 時間
Mark 似螢光筆重點
details 文章的細節
Figure /figcaption區塊 引用與標題
<hgroup> 當內容有主標題及次標題等多個標題的狀況下使用。
<cite> 引用其他文獻或作品(例如書籍、歌曲、電影、繪畫、雕塑等）的標題

<String>  粗體相對於<b></b>更有強烈意思
<i></i>italic(斜體)的字首。em 的完整名稱則是 emphasized(強調/注重)
s 原文是 strikethrough(刪除線)，del 這個標籤一看就會明白：delete(刪除)。
```
好文參考：
- [快速了解HTML語意化標籤](https://medium.com/@changru.studio/%E5%BF%AB%E9%80%9F%E4%BA%86%E8%A7%A3html%E8%AA%9E%E6%84%8F%E5%8C%96%E6%A8%99%E7%B1%A4-33dd8247d779)

- [[HTML5]b,i,s 跟 strong,em,del 這些看起來一樣，但意義不同的標籤們](
https://km.nicetypo.com/doc/ead903b94bb8bf01974d3ccdb91a117b)



### CSS

#### 區塊計算 Box Model
- Box Model 預設 box-sizing: content-box
  - content 內容 
  ```
  width: 寬度值;height: 高度值;
  ```
  - padding 內距
  ```
  padding:上 右 下 左;　padding:上下 左右;　
  padding:上 左右 下;　padding:四邊同値;
  ```
  - border 邊框
  ```
  border: 邊框粗細 邊框顏色 邊框樣式 ;
  ```
  - margin 物件與物件間距離
  ```
   margin:上 右 下 左;margin:上下 左右;
   margin:上 左右 下;margin:四邊同値;
  ```
- 該物件整體的大小會是content+padding+border，不要以為真的是width; height大小
- 然後margin是占空間但不可視的地方。


<img src="/images/post/content-box.png" width="500px" />

- 可以改變屬性 box-sizing: border-box;
- 就會幫你把整體物件大小設定為width+height
- 但這樣表示content內容只有width/height-padding-border(看左右/上下設定多少)
- 然後margin還是占空間但不可視的地方。

<img src="/images/post/border-box.png" width="500px" />



範例：可以用開發模式查看它的設定
<iframe src="https://codesandbox.io/embed/box-concept-f37fr-f37fr?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="Box concept-f37fr"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>


#### css reset
撰寫時會發現元素與視窗有空隙，css reset可以清楚，還有其他一些效果

- React + @emotion/css 套用範例
```
import reset from 'react-style-reset';
import { injectGlobal } from '@emotion/css';
injectGlobal(reset, {
});
```


#### 排版

##### 隱藏元素
 [w3schools Hide an Element](https://www.w3schools.com/css/css_display_visibility.asp)
```
 display: none; //空間消失
 visibility:hidden //空間仍存在

```

##### float


##### Flex
- 父層設定可以控制子層的排列方式
<iframe src="https://codesandbox.io/embed/flex-base1-xhwn8?fontsize=14&hidenavigation=1&theme=dark&view=preview"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="flex-base1"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

ＴＢＤ
1.align-content
2.延伸設定
3. default: align-items: stretch; 上下高度自動滿版時有出現空白問題

### 範例 layout
####  互動式視窗 Modal window 
  [How TO - CSS/JS Modal](https://www.w3schools.com/howto/howto_css_modals.asp)

- margin: 15% auto; / 15% from the top and centered /

#### input 欄位
- 一般的輸入數字框，可以看到預設會有上下箭頭出現
```
<input type="number" value="5">
```
<input type="number" value="5">

  - 如果要隱藏上下箭頭可以這樣寫：[howto_css_hide_arrow_number](https://www.w3schools.com/howto/howto_css_hide_arrow_number.asp)
  - css-in-js 版- [Hiding input spinner using styled-component](https://stackoverflow.com/questions/56352294/hiding-input-spinner-using-styled-component)
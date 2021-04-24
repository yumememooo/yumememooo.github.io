---
title: "網路文章學習筆記 react "
tags:
  - react
  - hook
categories:
  - Tech.
  - Web
  - front-end
date: 2021-03-28 09:33:18
---

{% note info %} 本文依照網路文章學習並標注內文重點，個人筆記，不公開至blog． {% endnote %}



{% note info %} 本文依照網路文章學習並整理為個人筆記，如有錯誤，歡迎寄信糾正，會再修正更新．
學習路上感謝網路大神們，如果你發現了我，可以查看以下參考文章了解更多概念👇👇👇</div>{% endnote %}

<!--more-->

### 1.react hooks 筆記
pjchender-[從 Hooks 開始，讓你的網頁 React 起來](https://ithelp.ithome.com.tw/users/20103315/ironman/2668)  
- 超級推薦購書 [天瓏](https://www.tenlong.com.tw/products/9789864345083)

紀錄：
- day6 useState的出現
一般加法可以在console看到變化，但是畫面還是不會變，透過 useState 讓 React 知道有東西變了．
  - useState 其實是React 物件中的一個方法，用法的兩個參數其實是解構賦植的用法
```
const [count, setCount] = useState(<資料預設值>);
```
文章中有細節流程：
https://ithelp.ithome.com.tw/articles/10219287


- 判斷隱藏元素的寫法- ＪＳ的邏輯運算子
  - css 隱藏時有display:none （空間會消失）or visibility:hidden（空間會存在）
  - 有兩種兩種 用css隱藏或是把ＤＯＭ整個都隱藏，後者的好處是不能讓使用者自行修改ＣＳＳ
>如果你需要比較嚴格的去控制使用者的行為，不想要使用者透過 CSS 就能簡單修改的話，那麼就把 DOM 整個移除；但如果這個功能被使用者手動打開也不會有太大影響的話，那就使用 CSS 樣式來控制畫面就好，如此會有比較好的效能和體驗(不會讓畫面排版有抖動的情況)。
[[Day 07 - 計數器] 幫計數器設個最大最小值吧 - JSX 中條件渲染的使用](https://ithelp.ithome.com.tw/articles/10219716)

----
- day 8 [[Day 08 - 計數器] 一個不夠，給我一次來十個 - JSX 中迴圈的使用](https://ithelp.ithome.com.tw/articles/10220209)
- 程式碼簡潔onclick & onclick奇怪的地方，()->參數用法的問題可以改成用箭頭函式解決
  - 將onclick中的函數抽出來，並去除掉（）=>，直接撰寫函數，不會執行而會設定
  [練習](https://github.com/yumememooo/counter-water/commit/a084004203346ad204d5d53ff7fe4868a7d452c6)
  - 如果該函式有參數，不能直接撰寫要加上（）＝>，不能會被當做要馬上執行而壞掉進入無限迴圈（函式後加上小括號會直接呼叫該函式）
  [練習](https://github.com/yumememooo/counter-water/commit/71b627e3eefdf7b7aa97b35f44588cb6437a6135)
    - 還有兩種更精簡的寫法，不需加（）＝> （需拿掉 不然會沒反應）
    - 要return function(){}中 [範例](https://github.com/yumememooo/counter-water/commit/c1fd638c3238a484f8f4fc723a1c7e8f4289231b)
    - 箭頭函式更精簡 ，最外圈{}拿掉，後面加上（）=> [範例](https://github.com/yumememooo/counter-water/commit/1ebfae46ef066765ba7145e57dd22b79a0f53cac)

- 重複渲染物件Render 多個 Component
  - 可以參考react的array Map用法說明 [列表與 Key](https://zh-hant.reactjs.org/docs/lists-and-keys.html) ->[練習](https://github.com/yumememooo/counter-water/commit/90adbbdec4100f4f49010bce5305446e1780b3e6)

-----
- day 9 <React.Fragment>竟然還可以縮寫成 <>

- 拆分組建
https://ithelp.ithome.com.tw/articles/10221113

部落格docusaurus
https://pjchender.dev/blog/tags/docusaurus/

- 父組件傳給子組件-透過解構賦值把 props 內需要用到的變數取出
- 須注意hook不能放進條件式中
https://ithelp.ithome.com.tw/articles/10221577


- props 就是指由外部傳入該組件內的資料，以上圖為例，就是因為在使用該組件時是透過 <Counter maxNumber="30" minNumber="21" startingValue="25" /> 這種方式把資料帶入該組件內的。

>hooks 裡面的 State 表示的是該組件自身內部的資料，也就是使用 useState 產生的資料。
不論是 props 或 state 的值都可以直接在 React 開發者工具內進行修改，這在檢查程式邏輯的時候非常方便，例如我們可以直接透過修改 state 或 maxNumber 等欄位看看畫面是不是如我們預期的，在特定條件下「向上／下箭頭」就會消失：

- React 開發者工具
TBD 碼表...效能檢視 Profilers
https://ithelp.ithome.com.tw/articles/10222217

- 及時天氣的API註冊
https://ithelp.ithome.com.tw/articles/10222662

NPM 趨勢比較圖
https://www.npmtrends.com/


- 可以將SVG當作組件傳入
- motion的區塊用法
#theme組件props傳入區塊用法
https://ithelp.ithome.com.tw/articles/10223594

#API與陣列操作
- setState的相關包覆寫法，要把相關的一些欄位都放進status裡，另外set時不能只寫出要修改或添加的物件屬性
https://reactjs.org/docs/hooks-faq.html#should-i-use-one-or-many-state-variables
```
https://ithelp.ithome.com.tw/articles/10224031
const weatherElements = locationData.weatherElement.reduce(
  (neededElements, item) => {
    if (['WDSD', 'TEMP', 'HUMD'].includes(item.elementName)) {
      neededElements[item.elementName] = item.elementValue;
    }
    return neededElements;
  },
  {}
);


```
https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce

arr.reduce(callback[accumulator, currentValue, currentIndex, array], initialValue)
陣列.reduce(回調函數[累積,目前值,目前陣列,陣列],初始值)
這個陣列可以再指派出去。

- 無窮迴圈的發生(待看TBD) useEffect與setState的順序練習
- 組件渲染完後，如果 dependencies 有改變，才會呼叫 useEffect 內的 function
- useEffect意思與可以在裡面做手動更改 DOM 畫面，而不是透過讓React 組件內 state 改變而更新畫面呈現的方式
https://ithelp.ithome.com.tw/articles/10224270

- 請求多個API時要更正的setState,prestate
https://ithelp.ithome.com.tw/articles/10224650


#優化UX 請求多個API造成畫面兩次渲染。
改成當API資訊都完成後再更新畫面，ES6 後更多人使用的則是 Promise 和 async/awit function。
位置寫錯的錯誤思考?如果將useEffort內的function寫在外面會發生什麼事?React Hooks ESLint Plugin 顯示錯誤提示??只是寫法風格問題
看體驗，當然有時候可以分兩次渲染
https://ithelp.ithome.com.tw/articles/10225102

- 新增onclick重新整理，套用useEffort裡的function
為了建立可共用function->Hooks ESLint Plugin 顯示錯誤提示
#把 fetchData 放到 dependencies 中(原來函示可以放在這邊@@?)，因為 fetchData 是一個函式，而在 JavaScript 中函式本質上就是物件的一種，物件在 JavaScript 中直接用 === 判斷並不是直接看屬性名稱和屬性值相不相同來決定的。-->避免 useEffect 內的函式不斷執行 - useCallback 的使用

https://ithelp.ithome.com.tw/articles/10225504

- 陣列判斷
Object的處理
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/entries
- useMemo 的使用:複雜的運算，因此除非有特定資料改變，否則不希望每次畫面重新渲染時都要在重新計算一次
https://ithelp.ithome.com.tw/articles/10225927

#載入中的旋轉動畫控制 css-in-js 判斷
#解構賦值的優化使用解說
https://ithelp.ithome.com.tw/articles/10226579

- 主題套用ThemeProvider
直接在 DevTools 中將 light 改成 dark 試試看
https://ithelp.ithome.com.tw/articles/10226957

- 整體組件成不同檔案與用prop傳值
- 自己做Custom Hook(後端理解為function具有回傳值，就是在做function而已)
https://ithelp.ithome.com.tw/articles/10227282

#讓子層組件可以修改父層組件的資料狀態 作法是一樣的
https://ithelp.ithome.com.tw/articles/10227537
#Controlled vs Uncontrolled Components 的寫法比較
##在 React 中表單元素的處理主要可以分成兩種 Controlled 和 Uncontrolled 這兩種
##像是 <input /> 這類的表單元素本身就可以保有自己的資料狀態，可以直接透過 JavaScript 再取出該元素的值，因為使用者輸入的內容可以直接保存在 <input /> 元素內。
##針對表單元素， React 會建議我們使用 Controlled Components，基本上使用 Controlled Components 和 Uncontrolled Components 都能達到一樣或類似的效果
##提醒：多數的表單元素都可以交給 React 處理，除了上傳檔案用的 <input type="file" /> 例外，因為該元素有安全性的疑慮，JavaScript 只能取值而不能改值，只能透過 Uncontrolled Components 的方式處理。
#- Uncontrolled Components - useRef 的使用但要特別留意的是：「當 input 欄位內的資料有變動時，並不像 Controlled Component 一樣會促發畫面重新渲染」，因此，若有重新渲染畫面的需求，建議還是使用 Controlled Component 來處理

##有些時候想要看某個組件被重新渲染了幾次，就可以類似這樣寫
https://ithelp.ithome.com.tw/articles/10227866


##將使用者設定地區保存下來：useEffect 搭配 localStorage
https://ithelp.ithome.com.tw/articles/10228132

#發布Github Pages 使用 CSS Reset & 搬移專案
https://ithelp.ithome.com.tw/articles/10228423

##PWA概念，把網站漸進成APP serviceWorker
https://ithelp.ithome.com.tw/articles/10228556

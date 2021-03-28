---
title: learn_hook
tags:
  - react
  - hook
categories:
  - Tech.
  - Web
  - front-end
date: 2021-03-28 09:33:18
---

{% note info %} 本文依照網路文章學習並標注內文重點，個人筆記，不公開． {% endnote %}



<!--more-->


#利用不能判斷隱藏元素的寫法
https://ithelp.ithome.com.tw/articles/10219716

#1 程式碼簡潔與onclick奇怪的地方，()->參數用法的問題可以改成用箭頭函式解決
#2 重複渲染物件的寫法
https://ithelp.ithome.com.tw/articles/10220209

#<React.Fragment>竟然還可以縮寫成 <>
https://ithelp.ithome.com.tw/articles/10220688

#1 拆分組建
https://ithelp.ithome.com.tw/articles/10221113

部落格docusaurus
https://pjchender.dev/blog/tags/docusaurus/

#父組件傳給子組件-透過解構賦值把 props 內需要用到的變數取出
#須注意hook不能放進條件式中
https://ithelp.ithome.com.tw/articles/10221577


#props 就是指由外部傳入該組件內的資料，以上圖為例，就是因為在使用該組件時是透過 <Counter maxNumber="30" minNumber="21" startingValue="25" /> 這種方式把資料帶入該組件內的。

hooks 裡面的 State 表示的是該組件自身內部的資料，也就是使用 useState 產生的資料。
不論是 props 或 state 的值都可以直接在 React 開發者工具內進行修改，這在檢查程式邏輯的時候非常方便，例如我們可以直接透過修改 state 或 maxNumber 等欄位看看畫面是不是如我們預期的，在特定條件下「向上／下箭頭」就會消失：

#React 開發者工具
TBD 碼表...效能檢視 Profilers
https://ithelp.ithome.com.tw/articles/10222217

#及時天氣的API註冊
https://ithelp.ithome.com.tw/articles/10222662

NPM 趨勢比較圖
https://www.npmtrends.com/


#可以將SVG當作組件傳入
#Emotion的區塊用法
#theme組件props傳入區塊用法
https://ithelp.ithome.com.tw/articles/10223594

#API與陣列操作
#setState的相關包覆寫法，要把相關的一些欄位都放進status裡，另外set時不能只寫出要修改或添加的物件屬性
https://reactjs.org/docs/hooks-faq.html#should-i-use-one-or-many-state-variables

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



https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce

arr.reduce(callback[accumulator, currentValue, currentIndex, array], initialValue)
陣列.reduce(回調函數[累積,目前值,目前陣列,陣列],初始值)
這個陣列可以再指派出去。

#無窮迴圈的發生(待看TBD) useEffect與setState的順序練習
#組件渲染完後，如果 dependencies 有改變，才會呼叫 useEffect 內的 function
#useEffect意思與可以在裡面做手動更改 DOM 畫面，而不是透過讓React 組件內 state 改變而更新畫面呈現的方式
https://ithelp.ithome.com.tw/articles/10224270

#請求多個API時要更正的setState,prestate
https://ithelp.ithome.com.tw/articles/10224650


#優化UX 請求多個API造成畫面兩次渲染。
改成當API資訊都完成後再更新畫面，ES6 後更多人使用的則是 Promise 和 async/awit function。
位置寫錯的錯誤思考?如果將useEffort內的function寫在外面會發生什麼事?React Hooks ESLint Plugin 顯示錯誤提示??只是寫法風格問題
看體驗，當然有時候可以分兩次渲染
https://ithelp.ithome.com.tw/articles/10225102

#新增onclick重新整理，套用useEffort裡的function
為了建立可共用function->Hooks ESLint Plugin 顯示錯誤提示
#把 fetchData 放到 dependencies 中(原來函示可以放在這邊@@?)，因為 fetchData 是一個函式，而在 JavaScript 中函式本質上就是物件的一種，物件在 JavaScript 中直接用 === 判斷並不是直接看屬性名稱和屬性值相不相同來決定的。-->避免 useEffect 內的函式不斷執行 - useCallback 的使用

https://ithelp.ithome.com.tw/articles/10225504
#發布Github Pages
https://ithelp.ithome.com.tw/articles/10228423
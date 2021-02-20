---
title: "[JS] javascript 新手上路與概念筆記"
tags:
  - javascript
categories:
  - Tech.
  - Web
  - front-end
  - js
date: 2021-02-20 11:33:18
---

{% note info %} javascript的學習整理 {% endnote %}

<!--more-->

## 開始學習

本章由[ＭＤＮ-JavaScript](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript)開始著手練習 

## 個人筆記整理


### 變數

#### 命名規則
- 小寫駱駝
- 大小寫相異(敏感)
- 有意義的名字

ref:[关于变量命名的规则](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Variables#%E5%85%B3%E4%BA%8E%E5%8F%98%E9%87%8F%E5%91%BD%E5%90%8D%E7%9A%84%E8%A7%84%E5%88%99)

#### 宣告
- let是區域的，更改內容只會影響到內部，外面的不會。
- var是全域的，更改內容只會影響到外面的。
- 宣告變數但不賦值=undefined
- null常見於宣告後面定義成沒有值或找不到
- 全域屬性 NaN 表示「非數值」（Not-A-Number）的數值
  - NaN 不等於（==、!=、===、!==）任何值，包括 NaN 本身。請使用 Number.isNaN() 或 isNaN() 來確認某個數值是否為 NaN。
ref:
- [var 与 let 的区别](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Variables#var_%E4%B8%8E_let_%E7%9A%84%E5%8C%BA%E5%88%AB)

- [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [NaN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/NaN)


#### JavaScript Hoisting (提升)顶置
- 變數(var hoisting)與函數都可以先使用再宣告
- 但提升操作不再适用于 let 并引起一个错误(Uncaught ReferenceError)
 ref:
 [JavaScript Hoisting (提升)](https://shubo.io/javascript-hoisting/#javascript-hoisting-%E6%8F%90%E5%8D%87)


#### 字符操作
- 一個字符串和一個数字可以直接相加變成字串
- 把字串當作對象，或許長度或大小寫轉換去處理字符串
```
<script>
    let s = 19 + '67';
    console.log("s:"+s+" type:"+typeof s);
    //鍵入s.可以找到很多以字符為對象的操作
</script>
s:1967 type:string
```


##### Number()
对象将把传递给它的任何东西转换成一个数字
```
let myString = '123';
let myNum = Number(myString);
typeof myNum;
```
##### toString()
每个数字都有一个名为 toString() 的方法，它将把它转换成等价的字符串。

ref:[JavaScript中的字符串](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Strings)

### 事件(Event)
- 好得寫法是找到(select)button並添加事件，避免汙染HTML。
- 關於button.onclick vs addEventListener
  - on會覆蓋上一个事件
  - addEventListener事件，可以多次绑定同一个事件并且不会覆盖上一个事件

ref:[JS裡addEventListener和on的區別](https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/42343/)

### Lint
在電腦科學中，lint是一種工具程式的名稱，它用來標記原始碼中，某些可疑的、不具結構性（可能造成bug）的段落。它是一種靜態程式分析工具

#### JSLint
JSLint 幫你檢查未定義的變數、函數、陳述式結尾有沒有加分號(;)、變數使用之前要先用 var 宣告、使用非數字的變數要用 === 或 !== 讓比對的時候不要自動進行轉型(Casting)、盡量不要使用 eval 函數、... 好多好多

#### ESLint
包括格式檢驗及質量效驗（未使用變量、三等號、全局變量聲明等問题）
自由選擇要使用哪些規則，對 ES6 還有 JSX 的支援度跟其他 linter 相較之下也是最高的

註： prettier 只是格式的檢驗（空格 格式化），不会對代码质量进行校验。但有些檢驗，ESLint沒有，所以可以ESLint＋prettier一起使用，也可以視使用情況不使用 Prettier。
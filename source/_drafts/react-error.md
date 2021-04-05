---
title: react-error
tags:
  - error
categories:
  - Tech.
  - Web
  - front-end
  - react
date: 2021-04-01 20:19:29
---


{% note info %} 紀錄前端開發時會遇到的錯誤狀況 {% endnote %}


<!--more-->


在開發環境執行程式時，點擊某一些動作會跳一些錯誤畫面，Runtime Error就是運行時錯誤
### Babel
Babel 是 JavaScript 的編譯器用來把 ES6 的程式碼轉化為瀏覽器或者其它環境支援的程式碼。

- 參考文 babel的細節解說：[前端科普系列（4）：Babel —— 把 ES6 送上天的通天塔](https://www.mdeditor.tw/pl/pNFj/zh-tw)

1. 錯誤修改const
{% note danger %}
const count = 0;
  return (
      <ActionBlock onClick={() => {
        count = count + 1;
        ....
 {% endnote %}

- _readOnlyError
node_modules/babel-preset-react-app/node_modules/@babel/runtime/helpers/esm/readOnlyError.js

👇👇👇未完待續 您可以拉到底部先看參考文章👇👇👇

# 網路參考文章
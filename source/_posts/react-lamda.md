---
title: '[✍練習][🚧進行中][react] 使用ramda整理資料'
tags:
  - react
  - ing
categories:
  - Tech.
  - Web
  - front-end
  - react
date: 2020-10-01 16:20:06
---

> ramda 一款實用的 JavaScript 函數编程库

<!--more-->

## 安裝 ramda

\$ npm install ramda

## 使用

import \* as R from "ramda";

### 過濾資料

```
const datas = [
  {
    name: "Cupcake",
    pri: 1,
    status: "OPEN",
    type: "blog",
    protein: 4.3
  },
  {
    name: "Donut",
    pri: 2,
    status: "OPEN",
    type: "go",
    protein: 4.9
  },]

找出所有datas.name="Cupcake"的資料
let f = R.filter(R.propEq("name", "Cupcake"), datas);


```

👇👇👇未完待續 您可以拉到底部先看參考文章👇👇👇

---

### 練習區 ✍

- 持續練習並更新

<iframe src="https://codesandbox.io/embed/reactramda-opulw?fontsize=14&hidenavigation=1&theme=dark"
     style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
     title="react_ramda"
     allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
     sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
   ></iframe>

{% note class_name %} ## 網路參考文章 {% endnote %}

[官方文檔](https://ramdajs.com/)
[中文官方文黨](https://ramda.cn/)
[Display JSON Data in React JS](https://www.golangprograms.com/display-json-data-in-reactjs.html)
[Ramda,从开始到重构](http://quanweili.com/2016/12/18/ramda-beginning-to-refactor.html)

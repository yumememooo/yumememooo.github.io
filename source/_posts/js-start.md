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

### JS歷史
ECMAScript是一種由國際標準，ES6為ECMAScript2015，是大幅度的更新，討論度較高，


## 個人筆記整理


### 宣告

#### 命名規則
- 小寫駱駝
- 大小寫相異(敏感)
- 有意義的名字

ref:[关于变量命名的规则](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Variables#%E5%85%B3%E4%BA%8E%E5%8F%98%E9%87%8F%E5%91%BD%E5%90%8D%E7%9A%84%E8%A7%84%E5%88%99)

#### 變數
- var是全域的，更改內容會影響到外面的。
- let是區域的，更改內容只會影響到內部，外面的不會。（ES6)
- const 宣告後不改值。（ES6)
- 宣告變數但不賦值=undefined
- null常見於宣告後面定義成沒有值或找不到
- 全域屬性 NaN 表示「非數值」（Not-A-Number）的數值
  - NaN 不等於（==、!=、===、!==）任何值，包括 NaN 本身。請使用 Number.isNaN() 或 isNaN() 來確認某個數值是否為 NaN。

ref:
[var 与 let 的区别](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Variables#var_%E4%B8%8E_let_%E7%9A%84%E5%8C%BA%E5%88%AB)
[let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
[NaN](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/NaN)

#### 比對
ＴＢＤ

##### 字符操作
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


###### Number()
对象将把传递给它的任何东西转换成一个数字
```
let myString = '123';
let myNum = Number(myString);
typeof myNum;
```
###### toString()
每个数字都有一个名为 toString() 的方法，它将把它转换成等价的字符串。

ref:[JavaScript中的字符串](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Strings)


#### 函式宣告
  - 可用函式宣告（Function Declaration）（ES5）
  - 函式運算式（Function Expressions）（ES5）
  - 箭頭函式運算式（arrow function expression）（ES5）


##### 宣告練習
使用及細節可以看下方：(js_func.html)
```
    <script>
        // ES5 函式宣告（Function Declaration）
        //function 函式名稱(參數) {
        function Add(A, B) {
            return A + B;
        }
        /* 或 */
        // ES5  函式運算式（Function Expressions）
        // var 函式名稱 = function (參數) {
        var Add2 = function (A, B) {//匿名函式
            return A + B;
        }
        var Add3 = function add3(A, B) {//#1 非匿名函式
            console.log(typeof add3);//#1 但只在自身有效
            return A + B;
        }
        console.log(Add(1, 2))//3
        console.log(Add2(1, 2))//3
        console.log(Add3(1, 2))//3
        //console.log(add3(1, 2))//#1 ReferenceError: add3 is not defined


        //ES6 宣告型態 函式名稱 = (參數) => {
        var Add4 = (A, B) => {
            return A + B;
        }
        //縮寫 如果只有return 可以去掉{}與return
        var Add5 = (A, B) => A + B;

         //縮寫 如果只有一個參數 可以去掉（）
        var AddS1 = (A) => A;
        var AddS2 = A => A;

        console.log("ES6:" + Add4(1, 2))//3
        console.log("ES6:" + Add5(1, 2))//3
    </script>
```
##### this的問題與箭頭函數的出現



#### JS的 Hoisting (提升)顶置特性
- 變數(var hoisting)與函數都可以先使用再宣告
- 但提升操作不再适用于 let 并引起一个错误(Uncaught ReferenceError)
 ref:
 [JavaScript Hoisting (提升)](https://shubo.io/javascript-hoisting/#javascript-hoisting-%E6%8F%90%E5%8D%87)



### 事件(Event)
- 好得寫法是找到(select)button並添加事件，避免汙染HTML。
- 關於button.onclick vs addEventListener
  - on會覆蓋上一个事件
  - addEventListener事件，可以多次绑定同一个事件并且不会覆盖上一个事件

ref:[JS裡addEventListener和on的區別](https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/42343/)

### Lint 工具
在電腦科學中，lint是一種工具程式的名稱，它用來標記原始碼中，某些可疑的、不具結構性（可能造成bug）的段落。它是一種靜態程式分析工具

#### JSLint
JSLint 幫你檢查未定義的變數、函數、陳述式結尾有沒有加分號(;)、變數使用之前要先用 var 宣告、使用非數字的變數要用 === 或 !== 讓比對的時候不要自動進行轉型(Casting)、盡量不要使用 eval 函數、... 好多好多

#### ESLint
包括格式檢驗及質量效驗（未使用變量、三等號、全局變量聲明等問题）
自由選擇要使用哪些規則，對 ES6 還有 JSX 的支援度跟其他 linter 相較之下也是最高的

註： prettier 只是格式的檢驗（空格 格式化），不会對代码质量进行校验。但有些檢驗，ESLint沒有，所以可以ESLint＋prettier一起使用，也可以視使用情況不使用 Prettier。

### JavaScript OOP
OOP （(Object-oriented programming）物件導向/對象編程，在 JavaScript 中，大多数事物都是对象, 从作为核心功能的字符串和数组。你甚至可以自己创建对象，在调用函数前加一个 new ，它就会返回一个这个函数的实例化对象，. 然后，就可以在这个对象上面添加一些属性．[JavaScript 对象入门](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects)

舉例：
- 用new func()來建構新的物件，func內部this可以指項新屬性
- 透過建構子（constructor）所建立出來的物件，我們稱為實例（instance）
- 如果忘記打new，變數會出現undifined
```
//this 指向了代码所在的对象(其实代码运行时所在的对象)。
function Pet(first,last, age) {
  this.name= {
    'first': first,
    'last': last
  };
  this.interests = ['food', 'sleep'],
  this.age = age;
  this.walk = function () {
    console.log(this.name.first + " walk...");
  } //這樣寫會佔用不同的對象空間
}

//函数的实例化对象
var cat1 = new Pet('dotdot','wu', 11);
var dog1 = new Pet('lucky','wu', 9);

//通过简单的语法访问他们
console.log(cat1.name.first)//点表示法访问
console.log(cat1['name']['first']) //括号表示法
console.log(cat1.interests[1])//数组属性的一个子元素
console.log(cat1.walk())//对象的方法调用

```

ref:[[筆記] 談談 JavaScript 中的 function constructor 和關鍵字 new](https://pjchender.blogspot.com/2016/06/javascriptfunction-constructornew.html)

#### Prototype 原型鏈的原理
上述的寫法，cat1.walk()與dog1.walk()是兩個不同對象的方法，為解決這問題．
- walk指定在 Pet.prototype 上面，所有 Pet 的 instance 都可以共享這個方法
```
Pet.prototype.walk = function() {
  console.log(this.name.first + " walk...");
}
```

- 因為 cat1 這個 instance 本身並沒有 walk 這個 function， 找不到，它會試著從Pet.prototype去找，一直往上找，直到找到Object，如果還是沒有，就會回傳undefined
- 而這個連接的方式，就是__proto__。
- 同时也有一些其他成员—— watch、valueOf 等等——这些成员定义在 Person() 构造器的原型对象、即 Object 。


ref:[該來理解 JavaScript 的原型鍊了](https://blog.techbridge.cc/2017/04/22/javascript-prototype/)
<br>[ __proto__ 和 prototype 到底有什麼區別](https://kknews.cc/code/6agvk2v.html)


#### JavaScript 中的繼承 (prototypal inheritance)

- call()函数。基本上，这个函数允许您调用一个在这个文件里别处定义的函数。
- 设置 Teacher() 的原型和构造器引用
  - create()这意味着Teacher.prototype现在会继承Person.prototype的所有属性和方法
  - prototype的constructor属性指向的是Person(),要改指向 Teacher
- 可重寫Teacher的greeting
```
//定义 Teacher() 构造器函数
  function Teacher(first, last, age, gender, interests, subject) {
    Person.call(this, first, last, age, gender, interests);

    this.subject = subject;
  }
  //这意味着Teacher.prototype现在会继承Person.prototype的所有属性和方法
  Teacher.prototype = Object.create(Person.prototype);
  Teacher.prototype.constructor = Teacher;//原本的是指向Ｐerson
  Teacher.prototype.greeting = function () {//重開改寫
    var prefix;

    if (this.gender === 'male' || this.gender === 'Male' || this.gender === 'm' || this.gender === 'M') {
      prefix = 'Mr.';
    } else if (this.gender === 'female' || this.gender === 'Female' || this.gender === 'f' || this.gender === 'F') {
      prefix = 'Mrs.';
    } else {
      prefix = 'Mx.';
    }

    alert('Hello. My name is ' + prefix + ' ' + this.name.last + ', and I teach ' + this.subject + '.');
  };
  var teacher1 = new Teacher('Dave', 'Griffiths', 31, 'male', ['football', 'cookery'], 'mathematics');

  teacher1.greeting()

```

ref:[JavaScript 中的继承](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/Inheritance) 探討何時使用與參考網站練習


TBD:
https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

#### 使用JSON
- JSON要求在字符串和属性用雙引號， 但引號無效。
- 我们使用 . 或 [] 訪問对象内的数据
- JSON.parse
用於將文字轉成json object
```
request.responseType = 'text';
var superHeroes = JSON.parse(superHeroesText); 
```
- JSON.stringify
用於將json object轉成json string
```
var myJSON = { "name": "Chris", "age": "38" }; console.log(myJSON)
var myString = JSON.stringify(myJSON);
console.log(myString)//string:{"name":"Chris","age":"38"}
```

### 其他練習

#### JS 與 canvas 元素

1. canvas
- 元素需要有闭合标签
- 基本上現今所有主流的瀏覽器都有支援

- 所有元素定位皆相對於此左上角原點

  <img src="https://mdn.mozillademos.org/files/224/Canvas_default_grid.png">
<br>

HTML
```
<canvas id="canvas" width="300" height="300">
</canvas>

```
ＪＳ
- 圓形ctx.arc(x, y, 半徑, 開始弧度, 結束弧度 )
0~2 pi =360°
更多弧度示意圖：[弧度](https://zh.wikipedia.org/wiki/%E5%BC%A7%E5%BA%A6)

```
var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');
ctx.fillStyle = 'green';
ctx.fillRect(10, 10, 100, 100);//畫矩形 x start,y start,width,height
```
利用漸變色及貝斯曲線或是填入圖案，繪製文字，可做出很多豐富的圖案，還有動畫行星/時鐘，滑鼠動畫，像素控制等，詳請見下方文件

ref:[Canvas 教學文件](https://developer.mozilla.org/zh-TW/docs/Web/API/Canvas_API/Tutorial)
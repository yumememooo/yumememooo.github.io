---
title: "[Note][React] function comp.中的ref屬性改寫"
tags:
  - react
categories:
  - Tech.
  - Web
  - front-end
  - react
date: 2020-09-14 20:57:34
---

function component中的ref屬性改寫．

<!--more-->



> 這天把class component中有input ref的範例改成function component
出現錯誤Error: Function components cannot have string refs. We recommend using useRef() instead.

- 原因
[Ref 和 DOM](https://zh-hant.reactjs.org/docs/refs-and-the-dom.html "Ref 和 DOM")@ React 裡有說你不能在 function component 上使用 ref，因為他們沒有 instance。

- 解法
	1.如果沒有用到把ref拿掉即正常
	2.改用useRef 是一個可以讓我們抓取到 DOM 節點的 hooks。(參考改法:[【Day 24】 useRef](https://ithelp.ithome.com.tw/articles/10221937?sc=rss.iron "【Day 24】 useRef") @IT邦幫忙)



- 改寫比較

<table><tr><td valign="top" width="30%" height="100%">
#### class component

```javascript
import React from 'react';

class Suggest extends React.Component{
  
    getValue(){
      return this.refs.lowlevelinput.valaue;
    }
    render(){
      const randomid=Math.random().toString(16).substring(2);
      return (
       <div>
         <input 
           list={randomid}
           defaultValue={this.props.defaultValue}
           ref='lowlevelinput'
           id={this.props.id}
           />  
          <datalist id={randomid} >
          {this.props.options.map((item,idx)=>
             <option value={item} key={idx}/>
           )}</datalist>
       </div>
      );
    }
  }
  export default Suggest;
  // ReactDOM.render(
  //   <div>
  //     <Suggest options={['esd','feff','fsf','fdsg','ghg']}/>
  //   </div>,
  //   document.getElementById('app')
  // );
```

<!-- recent_releases starts -->
</td><td valign="top" width="30%">
#### function component

```javascript
import React , { useRef }from 'react';

//class Suggest extends React.Component{
  const SuggestOpt=(props)=>{
     // const handleClick = () => {
  const handleChangeValue = (event) => {
    console.log(inputRef.current.value);
  };
   // render(){
    const handleClick = () => {
      inputRef.current.focus(); //滑鼠會跳到input的欄位
    }
    const inputRef = useRef(null);
      const randomid=Math.random().toString(16).substring(2);
      return (
       <div>
         <input 
           list={randomid}
           defaultValue={props.defaultValue}
           ref={inputRef}
           id={props.id}
            onChange={handleChangeValue}
           />  
          <datalist id={randomid} >
          {props.options.map((item,idx)=>
             <option value={item} key={idx}/>
           )}</datalist>
           <button onClick={handleClick}>click me</button>
       </div>
      );
  //  }
  }
  
export default SuggestOpt;
//1.class Suggest extends React.Component{
//改成const SuggestOpt=(props)=>{
//2.拿掉render(){}
//3.改寫ref
```

</td></tr></table>


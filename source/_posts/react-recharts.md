---
title: react-recharts
tags:
  - react
  - recharts
categories:
  - Tech.
  - Web
  - front-end
  - react
date: 2020-11-14 22:17:59
---

{% cq %} 
# 前文 ：引言
 {% endcq %}
 <blockquote class="blockquote-center">
 內文</blockquote>



<!--more-->



### Reactc畫圖套件recharts


#### 導入
```
 $ npm install recharts
```
#### 使用
```
import { LineChart, Line, XAxis, YAxis, Tooltip } from 'recharts';
function RenderLineChart() {
  const data = [
    { name: 'Page A', uv: 400, pv: 2400, amt: 2400 },
    { name: 'Page B', uv: 800, pv: 1200, amt: 2400 },
    { name: 'Page C', uv: 900, pv: 3000, amt: 2400 },
  ];
  return (
    <LineChart width={400} height={250} data={data}>
      <XAxis dataKey="name" />
      <YAxis />
      <Tooltip />
      <Line type="monotone" dataKey="uv" stroke="#8884d8" />
      <Line type="monotone" dataKey="pv" stroke="#3f51b5" />
      <Line type="monotone" dataKey="amt" stroke="#666666" />
    </LineChart>
  );
}

//在對應要放入的位置放入
<RenderLineChart />
```


{% note class_name %} ## 網路參考文章 {% endnote %}

[recharts](https://recharts.org/en-US)
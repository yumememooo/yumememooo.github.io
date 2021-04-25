---
title: "[web] 跨域請求 CORS"
tags:
  - http
  - cors
  - browser 
categories:
  - Tech.
  - web
  - browser

date: 2021-04-20 18:24:51
---

{% note info %} 筆記關於跨域請求 CORS {% endnote %}


<!--more-->

#### 跨來源資源共用
- 同源策略指的是，瀏覽器中某些行為，必須與來源頁面的「協定」、「網域」、「連接埠」都相同，才能進行。

- 跨來源資源共用（Cross-Origin Resource Sharing (CORS)）是一種使用額外 HTTP 標頭令目前瀏覽網站的使用者代理取得存取其他來源（網域）伺服器特定資源權限的機制

#### 跨域請求
而針對跨域請求，瀏覽器規範了伺服端可控制的項目，允許的來源、請求方法、可否發送Cookie、可取得的回應標頭，回應有效期限等。

CORS將跨域請求分為:
- 簡單(simple)的跨來源請求，不觸發預檢的請求，只使用 GET、HEAD、POST，且不添加額外的 Header


- 帶預檢(Preflight )的請求
使用了PUT、DELETE、CONNECT、OPTIONS、TRACE、PATCH方法(其實非簡單請求以外就會觸發預檢)，瀏覽器會先使用OPTIONS來試探伺服器Access-Control-Allow-Methods 及 Access-Control-Allow-Headers header。Preflight Request 沒過的話，真的 Request 也就不會發送了，


#### 建議延伸閱讀
- [ithome深入認識跨域請求](https://www.ithome.com.tw/voice/129558)
  1. 解說同源，前端請求歷史方法(XMLHttpRequest，JSONP)及請求方法。
  2. 非必要的話，就別將Access-Control-Allow-Credentials設為true。

- 詳細的規範可以看[MDN-CORS](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/CORS#%E7%B0%A1%E5%96%AE%E8%AB%8B%E6%B1%82)


- [CORS 简单请求+预检请求（彻底理解跨域](https://github.com/amandakelake/blog/issues/62)
整理過後的分類

- [[Day 27] Cross-Origin Resource Sharing (CORS)](https://ithelp.ithome.com.tw/articles/10205069)
  1. 有詳細的預檢請求request/response 內容
  2. Access-Contorl-Max-Age 則是告訴瀏覽器幾秒內不用再次預檢， 
86400 就是完成一次預檢後有一天的效力。
  3. Credentials 前端 Fetch 請求


- [|D10| Web Server - 跨域請求](https://ithelp.ithome.com.tw/articles/10205069)
  1. 可以看到API request送了兩次，第一次為OPTIONS
  2. 不同源(port/協議/domain)的比較

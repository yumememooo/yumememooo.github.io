---
title: "java spring 非同步事件"
tags:
  - java
  - spring
categories:
  - Tech.
  - back-end
  - java
date: 2021-01-30 18:00:42
---

{% cq %} 
# 前文 ：引言
 {% endcq %}

>spring加上Fire and forget，非同步處理，發出處理後就不用等待回復繼續做其他事情。

1.找到@Configuration的地方加上@EnableAsync
```
@Configuration
@EnableAsync
public class XxxConfig {
}
```
2.找到想要執行非同步的方法上方加上 @Async
```
@Component
public class MyComponent {
    @Async
    void doSomething() {
        // this will be executed asynchronously
    }
}
```
如果想要拿到回傳的地方可以在Future<XXX>拿到結果。
```
@Component
public class MyComponent {
    @Async
    Future<String> doSomething(String s, int i, long l, Object o) {
        // this will be executed asynchronously
        return new AsyncResult<>("result");
    }
}
```
3.異常處理 TBD
這塊自己是用restTamplate發出訊息，但無奈可以catch到錯誤，卻無法做錯誤輸出整理。
留下文章待做研究。





<!--more-->


{% note class_name %} ## 網路參考文章 {% endnote %}
- [spring-background-fire-and-forget-processing](https://stackoverflow.com/questions/33243255/spring-background-fire-and-forget-processing)
- [Spring Boot(5) @Async非同步執行緒池詳解](https://www.mdeditor.tw/pl/pIYL/zh-tw)
- Spring中@Async用法與異常處理
[Spring中@Async用法](https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/312303/)
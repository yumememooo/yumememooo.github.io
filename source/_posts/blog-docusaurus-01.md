---
title: "[BLOG] 五分鐘教你使用 docusaurus 建立筆記部落格"
tags:
  - blog
  - docusaurus
categories:
  - Tech.
  - Web
  - blog
date: 2021-05-21 18:39:33
---


{% note info %} 雖然說現在用的hexo技術建立的部落格就是為了寫筆記，但有時候只是為了真的純快速紀錄，之後待查或待看，但要整理成新的文章往往要一段時間，且很多不同的速記比較很難一下找出來，這時看到有另一種風格的部落格蠻適合當這樣的記錄的，適合作文檔的站點． {% endnote %}
{% note success %} 
1.Docusaurus will help you ship a beautiful documentation site in no time.
2.是由[Faecbook團隊開源專案](https://github.com/facebook/docusaurus)，提供的一款易於維護的靜態網站建立工具，且可以使用react技術編輯．（MIT License）
{% endnote %}

---
個人選擇的優點：
  1. 左側有可以闓盒的側欄，且進入文章後不會不見，可以快速瀏覽，且有搜尋文章的功能．
  2. 作為文檔保存筆記
  3. 玩玩Docusaurus ！！

（第一點雖然hexo我有試圖找過有沒有不同主題可以符合這樣的需求，但就當作為了切開而架架另一種風格的部落格，而且也很快速）

<!--more-->

## 建立Docusaurus
馬上就進入[官網](https://docusaurus.io/docs) 

get started 說明流程只要三個指令：

```javascript
npx @docusaurus/init@latest init my-website classic
cd my-website
npx docusaurus start

```
我的配置流程，我用的命名為my-note：
```javascript

blog npx @docusaurus/init@latest init my-note classic

npx: 40 安裝成功，花費 6.139 秒

Creating new Docusaurus project ...

Success! Created my-note
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm deploy
    Publish website to GitHub pages.

We suggest that you begin by typing:

  cd my-note
  npm start
```
這邊最後一步啟動介紹寫的有點不同，但是都可以啟動

一些基本的畫面就出來了☼☼☼
http://localhost:3000/my-note/

<img src="/images/post/my-note-ui.png" width="500px"/>

接著我先不改內容，先部署到網路上拿到正式網址．

----

## 上傳到github
這邊我用的方式是用gh-pages工具的做法，跟[官網deployment介紹](https://docusaurus.io/docs/deployment)的有點不同，（官網寫的覺得有點難懂，但流程可能比較正式）


個人使用gh-pages工具流程記錄如下．

1. 先到github新增專案名為“”my-note
2. 先把剛剛的專案上傳到GIT
```Bash 基本上照gutbuh建立完的提示輸入就好
git remote add origin XXX
git push -u origin master
```
3.安裝gh-pages工具
```
npm install --save gh-pages
```
3. 在專案的 package.json 中加入 homepage與scripts
```diff
"name": "my-note",
+ "homepage": "https://yumememooo.github.io/my-note",
scripts": {
+   "predeploy": "npm run build",
+    "deploy": "gh-pages -d build",
     "docusaurus": "docusaurus",
    "start": "docusaurus start",
    "build": "docusaurus build",
    "swizzle": "docusaurus swizzle",
-    "deploy": "docusaurus deploy",
```
4.接著gh-page 就可以用下列指令上傳啦
```shell console
npm run deploy

略
Success! Generated static files in build.

Use `npm run serve` to test your build locally.
> my-note@0.0.0 deploy /xxxx
> gh-pages -d build

Published
```
5. 成功部署到 Github 上後，會發現多了一個名為 gh-pages 的分支，教學文中說設定頁->GitHub Pages->Source要把頁面指到 gh-pages 這個分支（但我查看預設就是了）

6. 接著打開頁面，結果發現馬上跳錯誤畫面，但有指示要更改docusaurus.config.js檔案內的
```
baseUrl: '/my-note/',
```

7. 再開一次頁面會成功了！！
https://yumememooo.github.io/my-note/


## 開始編輯網站
這邊基本畫面上就有教學了，而且覺得比官網上的分類說明還要清楚，可以直接查看就好，這邊就簡單紀錄使用用法．

### 更改設定檔 docusaurus.config.js
這邊可以更改網站標題與logo


### 編輯的文件檔案規格
這邊可以選擇自己用react->js或是Markdown撰寫，前面需要學過react，一般可以用Markdown就好（不知道什麼是Markdown的可以先去玩玩線上編輯工具）

#### 新增頁面 page
可以新增一個頁面，然後對應的網址就會出現對應內容了，這通常是獨立頁面，需要另外用超連結指到這個位置．
- 須注意對應的網址會在 baseUrl底下喔
```
ex:
/src/pages/foo/index.js → <baseUrl>/foo/
看看效果：
my-note/src/pages/markdown-page.md
 →https://yumememooo.github.io/my-note/markdown-page/
```


#### 建立文件 Document
可以直接把文章放到docs/hello.md，並編輯位置與標題就會出現在側邊欄了．

```markdown /docs/intro.md
+ ---
+ sidebar_label: "Hi!"  
+ sidebar_position: 3
+ ---

[相關的markdown前言](https://docusaurus.io/zh-CN/docs/api/plugins/@docusaurus/plugin-content-docs#markdown-frontmatter)

# Hello 這邊就是文章內容

This is my **first Docusaurus document**!
```

### 建立blog
這邊一樣方法，只是會建立在blog分頁


## 新增插件
[插件列表](https://docusaurus.io/zh-CN/docs/api/plugins)

### plugin-content-docs
如果是有裝classic主題，就可以不用另外安裝，[plugin-content-docs](https://docusaurus.io/zh-CN/docs/api/plugins/@docusaurus/plugin-content-docs)裡的內容可以像下面修改：
```diff /docusaurus.config.js
presets: [
    [
      '@docusaurus/preset-classic',
      {
        docs: {
+          showLastUpdateTime: true,
        }

      },
    ],
  ],
```
-----



## 網路參考文章
{% note warning %} <span style="font-size: 9px;">
學習路上感謝網路大神們，如果你發現了我，可以查看以下參考文章了解更多概念👇👇👇</span>{% endnote %}
- [docusaurus 中文指南](https://www.docusaurus.cn/docs/configuration)
- [[Day 29 - 即時天氣] 寫網頁就是要炫耀啊，不然要幹麻？發布上 Github Pages 吧！](https://ithelp.ithome.com.tw/articles/10228423)
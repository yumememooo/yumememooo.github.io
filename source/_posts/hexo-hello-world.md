---
title: 使用Ｈexo 撰寫部落格
tags:
  - hexo
  - blog
categories:
  - Tech.
  - Web
  - blog
---
{% cq %} 
# hexo是什麼？
 {% endcq %}
 <blockquote class="blockquote-center">
 
Hexo 是一個快速、簡單且強大的網誌框架。Hexo 使用 Markdown 標記語言解析您的文章，並在幾秒鐘內，透過漂亮的主題產生靜態檔案。（來自 https://hexo.io/zh-tw/docs/ 說明）</blockquote>



# 本文將會知道
  1. 如何使用 Hexo 產生部落格 （超快速，只要看到這邊就建好囉！）
  2. 如何使用 markdown 撰寫文章 
  3. 如何部署到 github 個人網頁 
  4. 如何更改主題與內文風格 

<!--more-->
---


## 安裝hexo與初始化部落格


### 產生基本部落格結構

```
安裝工具 （使用npm安裝 可先安裝Node：https://nodejs.org/en/）
$ npm install -g hexo-cli
初始資料夾
$ hexo init <folder>
進入資料夾及安裝相依
$ cd <folder>
$ npm install
這邊就已經做好初始化了
```
###  啟動部落格 Run server

``` bash
$ hexo server
開啟瀏覽器 http://localhost:4000 就可以看到部落格了💕💕💕
```
More info: [Server](https://hexo.io/docs/server.html)

### （紀錄）顯示版本資訊 
（有需要的話，可以查詢對應安裝版本）知道自己安裝的版本，對於之後查詢問題是很有幫助的喔！
``` bash
$ hexo version
(node:5190) ExperimentalWarning: The fs.promises API is experimental
INFO  Validating config
hexo: 5.1.1
hexo-cli: 4.2.0
os: Darwin 19.0.0 darwin x64
http_parser: 2.8.0
node: 10.16.3
v8: 6.8.275.32-node.54
uv: 1.28.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.15.0
modules: 64
nghttp2: 1.39.2
napi: 4
openssl: 1.1.1c
icu: 64.2
unicode: 12.1
cldr: 35.1
tz: 2019a
```
---

## 開始撰寫文章

### 新增文章

``` bash
$ hexo new "My New Post"
會在source/posts 底下新增一個 .md 檔案
```
More info: [Writing](https://hexo.io/docs/writing.html)

### 撰寫文章

在剛剛新增的檔案開始採用 markdown語法開始撰寫文章．
- 可以找線上編輯器工具幫助撰寫及預覽，「自己習慣用這一個https://markdown-editor.github.io/」 ，編輯完再貼過來內文．
- 如對語法有一點熟悉，就直接用vscode打開檔案開始撰寫內文，並可以安裝vscode markdown preview 插件，邊改邊預覽．

- 編寫完再啟動部落格並在瀏覽器查看效果．

----

## 部署網站

### 建立與設定 Git 空間

- 先在github上新增一個專案叫與帳號一樣命名叫做“[yourname].github.io”
- 配置 _config.yml
```
deploy:
  type: git
  repo: https://github.com/yourname/yourname.github.io
  branch: master
```

### 產生靜態文件 Generate static files

``` bash
$ hexo generate 或是hexo g
會在public資料夾產生網站靜態檔案
這是用來部署到網站的檔案，記得每次部署前都要更新喔
```
More info: [Generating](https://hexo.io/docs/generating.html)

### 一鍵部署

``` bash
$ hexo deploy
（略）
Branch 'master' set up to track remote branch 'master' from 'https://github.com/nagimemooo/nagimemooo.github.io'.
INFO  Deploy done: git  
```

其他空間部署說明(ex:heroku) More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)

### 個人網站網址

https://yourname.github.io/

這樣就大功告成啦！🎉🎉🎉（註：有時要稍等一下才會看到更新）

### 清理靜態文件 Clean static files

``` bash
$ hexo clean
清除快取檔案 (db.json) 和已產生的靜態檔案 (public)
```



## 更換主題及個人化設定

### 更換主網站設定檔
主網站設定檔位置：/your folder/_config.yml，可以在此編輯基本網站說明．
```
title: Nagi's 程式筆記
subtitle: '小小工程師 Ｍemo '
description: ''
keywords:
author: Ｎagi
language: zh-TW
語言可以改為繁體中文，但對應顯示語言可以在以下位置修改：
/your folder/themes/next-reloaded/languages/zh-TW.yml
```

#### 更換主題
- Hexo 預設主題是landscape

- 想要更換主題依下列步驟即可：
1. 在 hexo 網站上挑選主題：https://hexo.io/themes/
2. 然後依照教學 clone對方的主題到自己的 theme 資料夾(通常都有git指令，在自己資料夾照下即可)
3. 修改主網站設定_config.yml來更換



---
- 本部落格採用Next，它是一個相當熱門的主題,且有很多中文文檔說明，我也是看了範例網站，真的太喜歡才決定架hexo的，紀錄操作步驟如下．
  - (初次遇到錯誤，可跳置下方) 試著更換主題 
  1. git clone https://github.com/iissnan/hexo-theme-next themes/next:

  2. config.yml 換成 theme：next，但是啟動hexo s後，開啟的網站卻是亂碼參數頁面＠＠
啟動畫面也出現以下訊息：
```
WARN  ========================= ATTENTION! ==========================
  ===============================================================
WARN   NexT repository is moving here: https://github.com/theme-next
  ===============================================================
WARN   It's rebase to v6.0.0 and future maintenance will resume there
 ===============================================================
```
原因應該是找到的文章教學，clone來源太舊了？改參考官方更新步驟[从 NexT v5.1.x 更新](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/UPDATE-FROM-5.1.X.md "从 NexT v5.1.x 更新")

  - （再來一次）試著更換主題
  1. Clone v7.8.0 最新的倉庫（如放在 next-reloaded）：
$ git clone https://github.com/theme-next/hexo-theme-next themes/next-reloaded
（v.5.1.4）
  2. 在 Hexo 的主配置文件中设置主题：
theme: next-reloaded
  3. 重新開啟就正常了
- 之後想更換別的主題也是這樣喔

### 主題設定
主題設定位置：/hexo-web/themes/next-reloaded/_config.yml

#### 更換NexT版面
```
NextT 提供不同風格可以更換
#scheme: Muse 選單在上方
#scheme: Mist 選單在上方
scheme: Pisces 選單在側邊
```

#### 新增文章標籤與分類
1. 新增標籤與分類頁面
```
hexo new page tags
hexo new page categories
```

2. 為文章加上Tag與categories
在_posts/xxx.md 文章上方新增，差別在於標籤是並行的標示，而分類會有階層式關係．
```
---
title: 使用Ｈexo 撰寫部落格
tags:
  - Testing
  - Another Tag

比較特別以下這種寫法代表階層關係Web->blog
categories:
  - Web
  - blog

或是多分類表示法：代表Diary->Food...
categories:
- [Diary, Food] 
- [Diary, Games]
- [Life]
---
```

3. 開啟頁面
```
_config.yml
# Usage: `Key: /link/ || icon`
# icon 也可以自由置換 https://fontawesome.com/v4.7.0/icons/
menu:
  home: / || fa fa-home
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  tags: /tags/ || fa fa-tags
  about: /about/ || fa fa-user
```

#### 新增個人頁面
1. 新增關於我頁面
```
hexo new page about
```

2. 編輯頁面內容
[your folder]/source/about/index.md
```
---
title: About Me
date: 2020-09-06 13:53:06
---
bla bla bla bla...
```

3. 開啟頁面
```
_config.yml
# Usage: `Key: /link/ || icon`
# icon 也可以自由置換 https://fontawesome.com/v4.7.0/icons/
menu:
  home: / || fa fa-home
  categories: /categories/ || fa fa-th
  archives: /archives/ || fa fa-archive
  tags: /tags/ || fa fa-tags
  about: /about/ || fa fa-user
```

#### 文章中顯示引言
```
有分號的上下引言，兩種皆可
<!-- 标签 方式，要求版本在0.4.5或以上 -->
{% centerquote %}blah blah blah{% endcenterquote %}
<!-- 标签别名 -->
{% cq %} blah blah blah {% endcq %}

單純的置中引言
<!-- HTML方式: 直接在 Markdown 文件中编写 HTML 来调用 -->
<!-- 其中 class="blockquote-center" 是必须的 -->
<blockquote class="blockquote-center">blah blah blah</blockquote>

顯示效果在本文開頭喔

```

#### 文章開頭標記
```
{% note class_name %} Content (md partial supported) {% endnote %}
其中class_name可不設或是改成下方關鍵字
```
{% note class_name %} Content (不設定) {% endnote %}

{% note default %} default {% endnote %}

{% note primary %} primary {% endnote %}

{% note success %} success {% endnote %}

{% note info %} info {% endnote %}

{% note warning %} warning {% endnote %}

{% note danger %} danger {% endnote %}

#### 文章中貼上圖片
```

放置圖片在/your folder/themes/next-reloaded/source/images
貼上相對路徑
![my](/images/avatar_memo.png) 
或是用html寫法，可以控制大小
<img src="/images/avatar_memo.png" width="150px" />

```

#### 開啟文章與網站訪問數字
```
主題內建不蒜子計數器
_config.yml
busuanzi_count:
  enable: true
  total_visitors: true
  total_visitors_icon: fa fa-user
  total_views: true
  total_views_icon: fa fa-eye
  post_views: true
  post_views_icon: fa fa-eye

本地預覽時底部訪問人數與總訪問的數字會異常大，這是正常现象
只需要部署至雲端即可恢復正常
```


#### 在標頭放上可愛的git連結
```
_config.yml
github_banner:
  enable: true
（本部落格右上角範例）
```

#### 顯示部落格作者照片
```
_config.yml
avatar：圖片網址
```

#### 放上個人社群連結
```
social
可自由新增
```

#### 顯示閱讀進度百分比
```
back2top:
  enable: true
  # Back to top in sidebar.
  sidebar: false 顯示在右下角 true代表顯示在側邊欄
  # Scroll percent label in b2t button.
  scrollpercent: true 顯示百分比
```

### 外部資源設定

#### 標籤雲

1.安裝插件
```
npm i hexo-tag-cloud --save
```
2.配置主網站_config.yml
要注意不要改錯檔案，不然可以看到標籤雲卻改不了樣式
```
# hexo-tag-cloud 標籤雲：see https://github.com/MikeCoder/hexo-tag-cloud
tag_cloud:
  textFont: Trebuchet MS, Helvetica # 字体
  textColor: '#869ABF' # 字體颜色
  textHeight: 12 # 字體高度
  outlineColor: '#FFCFAB' # 字體背景色
  maxSpeed: 0.5 # 標籤雲最大移動速度
  pauseOnSelected: true # true 選中時停止移動
```

3. 修改主題側邊欄的語言內容
以 NexT 主题為例修改layout/_macro/sidevar.swig 文件中在sidebar-inner新增
```
{% if site.tags.length > 1 %}
<script type="text/javascript" charset="utf-8" src="{{ url_for('/js/tagcloud.js') }}"></script>
<script type="text/javascript" charset="utf-8" src="{{ url_for('/js/tagcanvas.js') }}"></script>
<div class="widget-wrap">
    <div id="myCanvasContainer" class="widget tagcloud">
    <canvas width="220" height="250" id="resCanvas" style="width=100%">
        {{ list_tags() }}
    </canvas>
    </div>
</div>
{% endif %}

```

4. 作者git上的Readme說明 [by version 2.1.2]
建議可以關注 https://github.com/MikeCoder/ 說明動作操作
```
完成安装和显示，可以通过 hexo clean && hexo g && hexo s 来进行本地预览, hexo clean 为必须选项。
**PS:不要使用 hexo g -d 或者 hexo d -g 这类组合命令。**详情见: Issue 7
```


### 個人化設定

#### 預設新增文章模板

修改 /scaffolds/post.md 新增自己預設內容
```
---
title: {{ title }}
date: {{ date }}
tags:
categories:
---
blabla.....
<!--more-->
```
意外發現的方法，藉由這樣修改hexo new post時就可以把基本的設定加好了

------------

{% note class_name %} # 參考文章 {% endnote %}

- Quick Start
Welcome to [Hexo](https://hexo.io/)!  Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues)

- [HEXO 指令](https://hexo.io/zh-tw/docs/commands.html)
- [NextT開始使用](https://theme-next.iissnan.com/getting-started.html)
- [NextT 主题配置](https://theme-next.iissnan.com/theme-settings.html)
- [NextT 內置標籤](https://theme-next.iissnan.com/tag-plugins.html)
- [Hexo个人博客NexT主题设置Scheme外观](https://blog.csdn.net/mqdxiaoxiao/article/details/92843057?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param)
- [hexo页脚添加访客人数和总访问量](https://chrischen0405.github.io/2018/09/11/post20180911/)
- [Hexo 添加标签云](https://www.jianshu.com/p/2bb36378045d)
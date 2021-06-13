---
title:  HEXO BLOG


這是一個使用 HEXO 主題架設的部落格，方便快速建立文章及部屬在 github 上。

- github repo:
  https://github.com/yumememooo/yumememooo.github.io

- blog web IRL:
  https://yumememooo.github.io/

## Quick Start

### Create a new post

```bash
$ hexo new "My New Post"
```

### Run server

```bash
$ hexo server
```

### Generate static files

```bash
$ hexo generate
```

### Deploy to remote sites

```bash
$ hexo deploy
```

## upload

branch - src (have all files)
themes/next-reloaded will not upload
themes-bk/_config.yml will backup to upload
branch - master (only web files)


## post
```
{% note class_name %} Content (不設定) 淡灰色 {% endnote %}
{% note default %} 灰色 default {% endnote %}
{% note primary %} 紫色 primary {% endnote %}
{% note success %} 綠色 success {% endnote %}
{% note info %} 藍色 info {% endnote %}
{% note warning %} 黃色 warning {% endnote %}
{% note danger %} 紅色 danger {% endnote %}
```
## 重點標籤
```
{% label default@標示灰色底色 %}
{% label primary@標示紫色底色 %}
{% label success@標示綠色底色 %}
{% label info@標示藍色底色 %}
{% label warning@標示黃色底色 %}
{% label danger@標示danger底色 %}
```

{% label info@ES6%}
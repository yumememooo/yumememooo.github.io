---
title: "[command]使用內建指令快速產生大黨"
tags:
  - CLI
  - file
categories:
  - [Tech., Mac]
  - [Tech., Windows]
date: 2021-04-20 18:33:30
---


{% note info %} 開發時有時會需要測試大檔案的上傳，因此需要先準備大檔案，而系統內建就有一些指令可以快速產生虛胖的檔案． {% endnote %}


<!--more-->

### windows環境

>Fsutil 是用於執行與檔案配置表 (FAT) 和 NTFS 檔案系統相關的工作，例如管理重新剖析點、管理稀疏檔案或卸載磁片區。必須以系統管理員身分執行，才能使用 fsutil。

更多功能請見[microsoft fsutil](https://docs.microsoft.com/zh-tw/windows-server/administration/windows-commands/fsutil)

#### fsutil file createnew 用法
- fsutil file createnew 位置 <FileName.txt> <FileSize(size in bytes)>
```
C:\WINDOWS\system32> fsutil file createnew /?
使用方法 : fsutil file createNew <filename> <length>
   例如 : fsutil file createNew C:\testfile.txt 1000
C:\WINDOWS\system32>fsutil file createnew C:\testfile.txt 1000
檔案 C:\testfile.txt 已經建立
```
- 自行計算一下產生不同大小的檔案
```
fsutil file createnew C:\1kb.txt 1000 //產生1kb檔案至指定位置
fsutil file createnew large_10m.txt 10485760   //10*1024*1024
fsutil file createnew large_500m.txt 524288000   //500*1024*1024
fsutil file createnew large_1g.txt 1073741824  //1*1024*1024*1024
```

---

### Mac 環境
在Ｍac環境使用更方便，不需計算大小，使用內建的 mkfile 指令就可以輕鬆建立了：
- mkfile -n size[b|k|m|g] filename
```
mkfile -n 20m 20mb.txt
```

---

## 網路參考文章
{% note warning %} <span style="font-size: 9px;">
學習路上感謝網路大神們，如果你發現了我，可以查看參考文章了解更多概念👇👇👇
</span>{% endnote %}
[Quickly Generate Large Test Files in Windows](https://tweaks.com/windows/62755/quickly-generate-large-test-files-in-windows/)
[[Mac] 使用 mkfile 指令，快速建立測試用的大檔](https://ephrain.net/mac-%E4%BD%BF%E7%94%A8-mkfile-%E6%8C%87%E4%BB%A4%EF%BC%8C%E5%BF%AB%E9%80%9F%E5%BB%BA%E7%AB%8B%E6%B8%AC%E8%A9%A6%E7%94%A8%E7%9A%84%E5%A4%A7%E6%AA%94/)

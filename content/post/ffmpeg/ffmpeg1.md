---
title: "万能的多媒体转换器——FFmpeg"
description: 
date: 2023-11-03T09:59:29Z
image: 
math: 
license: 
hidden: false
comments: true
categories:
    - random
tags:
    - ffmpeg

---

{{< quote author="" source="百度百科" url="https://baike.baidu.com/item/ffmpeg/2665727">}}
FFmpeg是一套可以用来记录、转换数字音频、视频，并能将其转化为流的开源计算机程序。采用LGPL或GPL许可证。它提供了录制、转换以及流化音视频的完整解决方案。
{{< /quote >}}

## 基本使用

参考：[简单的终端操作 - Windows篇](../简单的终端操作-windows篇/)

最简单的使用方式如下：

`ffmpeg -i 输入文件 输出文件`

> 注：如果想直接使用ffmpeg，而不是定位到ffmpeg所在文件夹再使用，可以将`ffmpeg.exe`放在`C:\Windows\System32`下，也可以通过编辑环境变量来解决（[了解环境变量](../了解环境变量/)）\
> 利用ffmpeg也可以快速地将视频转换成音频（示例如下第二条）

例：

```shell
ffmpeg -i input.flv output.mp4
ffmpeg -i input.mp4 output.mp3
```

（文章仍在编辑中，未完待续……）

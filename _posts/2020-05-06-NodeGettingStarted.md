---
layout: post
title: Node.js 入門
date: 2020-05-05 21:30:15 +0800
autor: Michael Tseng
comments: true
categories: articles
tags: [Node.js]
---

Node.js是Open Source跨平台的Runtime environment，可以在上面執行JavaScript程式，使用Google V8引擎。JavaScript運行在瀏覽器中，而Node.js運行在後端(脫離瀏覽器)，常用於後端服務(Application Programming Interface)。

## Node架構
綠色部分是JavaScript，中間是Google V8引擎，可以將JavaScript轉換成機器語言，以便在機器上運行，是使用C++撰寫。所以Node.js並非程式語言，而是一個Runtime environment可以在後端去執行JavaScript程式
![Node Architecture](https://imgur.com/x5Z7k6A)

## Node運作
* Event-driven
* Non-blocking
* Asynchronous
![Node Work](https://imgur.com/Xfl8yXy)
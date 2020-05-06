---
layout: post
title: Node.js入門學習記錄
date: 2020-05-06 21:30:15 +0800
autor: Michael Tseng
comments: true
categories: articles
tags: [Node.js]
---

Node.js是Open Source跨平台的Runtime environment，使用Google V8引擎，可以在上面執行JavaScript程式。JavaScript運行在瀏覽器中，而Node.js運行在後端(脫離瀏覽器)，常用於後端服務(Application Programming Interface)。

## 架構
綠色部分是JavaScript，中間是Google V8引擎，可以將JavaScript轉換成機器語言，以便在機器上運行，是使用C++撰寫。所以Node.js並非程式語言，而是一個Runtime environment可以在後端去執行JavaScript程式

![Node Architecture](https://i.imgur.com/x5Z7k6A.png)

## 運作
* Event-driven
* Non-blocking
* Asynchronous

![Node Work](https://i.imgur.com/Xfl8yXy.png)

### 實作
* Blocking

```javascript
// Blocking
// 先等待三秒後執行console.log("BlockingTest Complete!");
// 再執行console.log("Node.js");
function BlockingTest(){
    var start = new Date().getTime();
    while(new Date().getTime() < start + 3000);
}
BlockingTest();
console.log("BlockingTest Complete!");
console.log("Node.js");

// 執行結果
// BlockingTest Complete!
// Node.js
```

* Non-blocking

```javascript
// Non-Blocking
// done為Callback函數，done => function()
// 會先執行console.log("Node.js");
// 等待三秒在回去呼叫function()中的console.log("Non-BlockingTest Complete!");

function NonBlockingTest(done){
    setTimeout(() => {
        done();
    }, 3000);
}

NonBlockingTest(function(){
    console.log("Non-BlockingTest Complete!");
})
console.log("Node.js");

// 執行結果
// Node.js
// BlockingTest Complete!
```

## 安裝
* [Node.js](https://nodejs.org/en/)
* [Visual Studio Code](https://code.visualstudio.com/)

## 參考
* [Node.js Tutorial for Beginners: Learn Node in 1 Hour](https://youtu.be/TlB_eWDSMt4)
* [Node.js入门](https://www.youtube.com/playlist?list=PLliocbKHJNwvbitOJ73M04PUoJae79kEg)
* [Node.js 是什麼？跟 JavaScript 有什麼關係](https://tw.alphacamp.co/blog/node-js-and-javascript)
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

## Global Objects
Global Objects的意思是指全域物件，也就是開發者在任何地方都可以存取Global Objects，在node宣告變數或函數，是無法透過global物件存取，只有node預設變數或函數是依附在gobal物件上，其他自行宣告的變數或函數，存取範圍僅限制它們存在的檔案裡。[Node Global Objects](https://nodejs.org/dist/latest-v12.x/docs/api/)

```javascript
var message = '';
console.log(global.message);

// 執行結果
// undefined
```

## Modules
我們可以將重複的功能定義成一個模組裡面可以包含變數和方法，如果主程式需要就可以引入使用自定義模組，所以會介紹模組的輸入與輸出。

`
資料夾結構
.
+-- First-app
    +-- app.js
    +-- logger.js
`

```javascript
// logger.js
// 建立變數url與方法log
var url = 'http://mylogger.io/log';

function log(message){
    console.log(message);
}

// module.exports.自訂想輸出名稱 = 此檔案變數、函數
module.exports.log = log;
module.exports.endPoint = url;
```

```javascript
// app.js
// 引入logger輸出模組
const logger = require('./logger');

console.log(module);
console.log(logger);
logger.log('message');

// 執行結果
// Module {
//   id: '.',
//   path: 'C:\\Users\\USER\\Desktop\\HTML\\first-app',
//   exports: {},
//   parent: null,
//   filename: 'C:\\Users\\USER\\Desktop\\HTML\\first-app\\app.js',
//   loaded: false,
//   children: [
//     Module {
//       id: 'C:\\Users\\USER\\Desktop\\HTML\\first-app\\logger.js',
//       path: 'C:\\Users\\USER\\Desktop\\HTML\\first-app',
//       exports: [Object],
//       parent: [Circular],
//       filename: 'C:\\Users\\USER\\Desktop\\HTML\\first-app\\logger.js',
//       loaded: true,
//       children: [],
//       paths: [Array]
//     }
//   ],
//   paths: [
//     'C:\\Users\\USER\\Desktop\\HTML\\first-app\\node_modules',
//     'C:\\Users\\USER\\Desktop\\HTML\\node_modules',
//     'C:\\Users\\USER\\Desktop\\node_modules',
//     'C:\\Users\\USER\\node_modules',
//     'C:\\Users\\node_modules',
//     'C:\\node_modules'
//   ]
// }
// { log: [Function: log], endPoint: 'http://mylogger.io/log' }
// message
```

## 參考
* [Node.js入门](https://www.youtube.com/playlist?list=PLliocbKHJNwvbitOJ73M04PUoJae79kEg)
* [[Note] 什麼是 NodeJS](https://pjchender.github.io/2018/12/07/node-%E4%BB%80%E9%BA%BC%E6%98%AF-nodejs/)
* [Node.js 是什麼？跟 JavaScript 有什麼關係](https://tw.alphacamp.co/blog/node-js-and-javascript)
* [Node.js Tutorial for Beginners: Learn Node in 1 Hour](https://youtu.be/TlB_eWDSMt4)
* [Node.js 新手入門1：Node Module System 模組化系統](https://medium.com/@brianwu291/learn-basic-node-part1-module-system-e9ee1724656b)
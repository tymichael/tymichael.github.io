---
layout: post
title: Javascript學習記錄
date: 2020-04-02 00:22:15 +0800
autor: Michael Tseng
comments: true
categories: articles
tags: [sample]
---

Javascript是一種網頁設計的語言，用來呈現網頁動態效果，例如:跑馬燈。Javascript與Java是完全不同的語言，Javascript是由Netscape 工程師Brendan Eich所發明的。

## 開發工具
* Visual Studio Code
* Google Chrome 開發者工具，開啟Google Chrome後，點"右鍵"選擇"檢查"，會跳出開發者視窗，在選擇"Console"，就可以在上面寫Javascript程式，實作如下圖
![Console](https://i.imgur.com/LHARnDp.png)

## Todolist專案實作
User Story，定義需求規格，再來實作
### User Story
* App 要有變數儲存待辦事項
* App 要有方法去顯示待辦事項
* App 要有方法去增加待辦事項
* App 要有方法去更新待辦事項
* App 要有方法去刪除待辦事項

### 實作
```javascript
// todolist V1
// User story 1: 變數儲存待辦事項
var todos = ["todos1", "todos2"];
// User story 2: 顯示待辦事項
console.log(todos);
// User story 3: 新增待辦事項
todos.push("new todos");
console.log(todos);
// User story 4: 更新待辦事項
todos[0] = "update todos";
console.log(todos);
// User story 5: 刪除待辦事項
todos.splice(0, 1);
console.log(todos);
```
![執行結果](https://i.imgur.com/NRN1b9B.png)
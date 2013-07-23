---
layout: post
title: "duff's device in javascript"
date: 2013-07-23 16:59
comments: true
categories: 
---

```js
var iterations = 9999;
var testVal = 0;
var n = iterations / 8;
var caseTest = iterations % 8;

do {
    switch (caseTest) {
        case 0:
        testVal++;
        case 7:
        testVal++;
        case 6:
        testVal++;
        case 5:
        testVal++;
        case 4:
        testVal++;
        case 3:
        testVal++;
        case 2:
        testVal++;
        case 1:
        testVal++;
    }
    caseTest = 0;
}
while( --n > 0);
```

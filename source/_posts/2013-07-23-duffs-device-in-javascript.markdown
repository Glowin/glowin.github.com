---
layout: post
title: "duff's device in javascript"
date: 2013-07-23 16:59
comments: true
categories: 
---

```js
/**
 * Duff's Device 
 * http://home.earthlink.net/~kendrasg/info/js_opt/jsOptMain.html#duffsdevice
 */
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

另外的一个 Jeff 的版本

```js
/**
 * Fast Duff's Device
 * @author Jeff Greenberg
 * http://home.earthlink.net/~kendrasg/info/js_opt/jsOptMain.html#fastDuffsdevice
 */
var testVal = 0;
var n = iterations % 8;
while (n--) {
 testVal++;
}

n = parseInt(iterations / 8);
while (n--) {
 testVal++;
 testVal++;
 testVal++;
 testVal++;
 testVal++;
 testVal++;
 testVal++;
 testVal++;
}
```

这儿有一些相关的链接:
http://jsperf.com/duffs-device


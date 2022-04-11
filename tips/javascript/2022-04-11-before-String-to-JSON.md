---
title: 如何正确的判断一个字符串是否为JSON字符串
tip-number: 72
tip-username: LiuH
tip-tldr: 很多时候我们需要在将一个字符串转为JSON时先判断该字符串是否为一个JSON字符串，如果是则转为JSON，否则直接返回默认值。
---


很多时候我们需要在将一个字符串转为JSON时先判断该字符串是否为一个JSON字符串，如果是则转为JSON，否则直接返回默认值：

``` javascript
function isJson(str) {
    try {
        if (typeof JSON.parse(str) === 'object') {
            return true;
        }
        return false;
    } catch {
        return false;
    }
}

isJson(''); // false
isJson('{}'); // true
isJson('[]'); // true
isJson('123456'); // false
```
需要注意的是，如果 `str` 是一个纯数字的字符串，比如：`'123456'`，使用 `JSON.parse` 可以正常转换，结果为 `123456`。

# WxMock
微信小程序 - 模拟数据工具
##### 使用方法

### 使用代码片段分享 
[wechatide://minicode/wCHxXXmf6OYz](wechatide://minicode/wCHxXXmf6OYz)


* 1. copy文件dist/mock.js dist/WxMock.js 到小程序工程根目录的 utils目录下
* 2. 在app.js 引入 WxMock 代码 
```javascript 
var Mock = require("./utils/WxMock.js"); 
```
* 3. 在app.js中书写需要模拟的接口及返回结构
```javascript
 Mock.mock('https://xxx.com/users',{
        "success": true,
        "data|1-20": [
            {
                "name":function() {
                  return Mock.Random.cname()
                },
                "lastLogin":function() {
                  return Mock.Random.datetime()
                }
            }
        ]
 })
  Mock.mock('https://xxx.com/user/delete',{
         "success": true,
         "message": "删除成功"
  })
```
* 4. 只要在 wx.request 中使用url为 mock对应的地址 就会返回响应mock数据
```javascript
wx.request({
  url: 'https://xxx.com/users',
  success: function(res){
    console.log('https://xxx.com/users',res);
  }
})
```

Mock.js 使用方式见 http://mockjs.com/examples.html

# Mock.js
<!-- 模拟请求 & 模拟数据 -->
[![Build Status](https://travis-ci.org/nuysoft/Mock.svg?branch=refactoring)](https://travis-ci.org/nuysoft/Mock)

<!-- [![Coverage Status](https://coveralls.io/repos/nuysoft/Mock/badge.png?branch=refactoring)](https://coveralls.io/r/nuysoft/Mock?branch=refactoring)
[![NPM version](https://badge.fury.io/js/mockjs.svg)](http://badge.fury.io/js/mockjs)
[![Bower version](https://badge.fury.io/bo/mockjs.svg)](http://badge.fury.io/bo/mockjs)
[![Dependency Status](https://gemnasium.com/nuysoft/Mock.svg)](https://gemnasium.com/nuysoft/Mock)
[![spm package](http://spmjs.io/badge/mockjs)](http://spmjs.io/package/mockjs) -->

Mock.js is a simulation data generator to help the front-end to develop and prototype separate from the back-end progress and reduce some monotony particularly while writing automated tests.

The official site: <http://mockjs.com>

## Features

* Generate simulated data according to the data template
* Provide request/response mocking for ajax requests
* ~~Generate simulated data according to HTML-based templates~~

This library is loosely inspired by Elijah Manor's post [Mocking
Introduction](http://www.elijahmanor.com/2013/04/angry-birds-of-javascript-green-bird.html), [mennovanslooten/mockJSON](https://github.com/mennovanslooten/mockJSON), [appendto/jquery-mockjax](https://github.com/appendto/jquery-mockjax) and [victorquinn/chancejs](https://github.com/victorquinn/chancejs/).

## Questions?
If you have any questions, please feel free to ask through [New Issue](https://github.com/nuysoft/Mock/issues/new).

## Reporting an Issue
Make sure the problem you're addressing is reproducible. Use <http://jsbin.com/> or <http://jsfiddle.net/> to provide a test page. Indicate what browsers the issue can be reproduced in. What version of Mock.js is the issue reproducible in. Is it reproducible after updating to the latest version?

## License
Mock.js is available under the terms of the [MIT License](./LICENSE).

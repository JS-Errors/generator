# js-errors [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Dependency Status][daviddm-image]][daviddm-url] [![Coverage percentage][coveralls-image]][coveralls-url]

[English README](./README.en.md)

> 通用错误处理与生成方案

具备如下功能的javascript错误处理方案
1. 域(Domain)
   类似于前缀(Prefix)，方便错误的识别
2. 预定义错误(即标准错误)   
   预定义库会随着时间不断的累积，方便使用
3. 国际化
   错误的消息值可以随着不同的区域发生变化
4. 定制化  
   通过指定错误文件夹定制错误信息
5. 一致性
   对于相同的名字的错误，不同的项目可以通用。因为名字与ID在同名错误之间不可变。方便了项目的沟通过

## 安装

```sh
$ npm install --save js-errors
```

## 使用

```js
//获取错误接口
var BaseError = require('js-errors').error;

//获取错误消息或者Code信息数据
var i18n = require('js-errors').i18n;
var errorMessages = i18n.get(pathOfErrorMessagesOrCodesDefined);
```

### 定义新错误

```js
var error = new BaseError({
      errors: ['user', 'not', 'found'],    //Sequential Error Description
      prefix: 'java:',                     //Prefix for Messages
      code: 404,                           //Numeric value for this error
      message: 'User is not found!',       //Customized Error Messsage
      locale: 'en-US',                     //Locale for errors
      i18n: i18n.get(dir)                  //Customized error definition directory
    });
//error.name => "UserNotFound"
//error.code => 404
//error.message => "java:User is not found!"
//error.restify() => { code: 404, message: "js:hello", name: 'UserNotFound'}
```

### 抛出错误
```js
throw error;
```

### 错误消息(message)、错误代码(code)和错误名称(name)

* 错误消息可以添加前缀，可以根据地区变换
* 错误代码可以自定义，也可以预定义
* 错误名称在所有的项目中不会发生变化，可以唯一标识


## License

MIT © [calidion](blog.3gcnbeta.com)


[npm-image]: https://badge.fury.io/js/js-errors.svg
[npm-url]: https://npmjs.org/package/js-errors
[travis-image]: https://travis-ci.org/js-errors/js-errors.svg?branch=master
[travis-url]: https://travis-ci.org/js-errors/js-errors
[daviddm-image]: https://david-dm.org/js-errors/js-errors.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/js-errors/js-errors
[coveralls-image]: https://coveralls.io/repos/js-errors/js-errors/badge.svg
[coveralls-url]: https://coveralls.io/r/js-errors/js-errors

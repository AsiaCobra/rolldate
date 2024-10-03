# rolldate [![npm](https://img.shields.io/npm/v/rolldate.svg)](https://www.npmjs.com/package/rolldate) [![npm](https://img.shields.io/npm/dm/rolldate.svg)](https://www.npmjs.com/package/rolldate)

This plugin is a new version of [jquery-date](https://github.com/weijhfly/jqueryDatePlugin "jquery-date"), primarily designed to address issues such as unreasonable parameter design, low scrolling efficiency, dependency on jQuery, lack of optional theme styles, etc. It also introduces callback functions for greater flexibility.

## Version 3.0 Update (2019/05/24)

The previous version was 2.1.5. Changes in the new version (starting from 3.0.0):

1. The usage changed from `new rolldate.Date` to `new Rolldate`.
2. Callback functions were adjusted: `tapBefore` renamed to `init`, `confirmBefore` renamed to `confirm`, `confirmEnd` removed, and `cancel` added.
3. The date format (format) is now unrestricted and can be freely combined according to rules.

## Important Version Update (2019/02/03)

The previous version was 1.5.1. The new version (starting from 2.0.0) differs from earlier versions in the following ways:

1. Replaced the scrolling plugin from iscroll to better-scroll, improving compatibility.
2. Changed the interface style for easier operation.
3. Removed the `rolldate.css` file; only the JS file needs to be included.
4. Removed theme styles and sliding time settings for date initialization.

**Note**: Versions prior to 2.0.0 will no longer be maintained. For previous versions, please visit: [Old rolldate](https://weijhfly.github.io/rolldate-index2.html "rolldate")

## Demo

Experience the [rolldate](https://weijhfly.github.io/rolldate-index.html "rolldate") (scan the QR code below for a direct experience):

![rolldate](https://weijhfly.github.io/images/rolldate-demo.jpg)

## Usage

### ES6
```js
import Rolldate from 'rolldate';
new Rolldate({
  el: '#date'
});


## 使用方式
### es6
```js
import Rolldate from 'rolldate'
new Rolldate({
  el:'#date'
})
```
### commonJS
```js
var Rolldate = require('rolldate');
new Rolldate({
  el:'#date'
})
```
### amd
```js
require(['rolldate'],function(Rolldate){
  new Rolldate({
    el:'#date'
  })
})
```
### cmd
```js
seajs.use('rolldate',function(undefined){
    //插件没有遵循cmd规范，这里的Rolldate是全局的
    new Rolldate({
      el:'#date'
    })
});
```
## 参数、方法说明
名称|必填|默认值|说明
---|:-:|:-:|---
el|否|无|绑定插件的dom元素，插件内部使用document.querySelector，<br>也可以直接传递dom元素对象，只支持单个
format|否|'YYYY-MM-DD'|日期格式，无限制。规则：年-YYYY 月-MM 日-DD 时-hh 分-mm 秒-ss 使用/、-、空格、:之一分隔，可随意组合
beginYear|否|2000|日期开始年份
endYear|否|2100|日期结束年份
value|否|无|日期初始化的默认值，列如'2018-03-18'
lang|否|年、月、日...|配置插件语言，默认：title:'选择日期',cancel:'取消',confirm:'确认',<br>year:'年',month:'月',day:'日',hour:'时',min:'分',sec:'秒'
minStep|否|1|分钟按指定数分隔
init|否|null|插件触发前的回调函数，return false可阻止插件执行
moveEnd|否|null|插件滚动后的回调函数，函数返回一个参数(better-scroll实例)
confirm|否|null|确认按钮触发前的回调函数，return false可阻止插件执行，<br>return其他值可修改日期，函数返回一个参数(选中的日期)
cancel|否|null|插件取消时触发的回调函数
trigger|否|'tap'|默认使用tap解决移动端click事件300ms延迟，可选click替换tap。注意使用tap会阻止其他绑定的click事件的触发
show|否|无|主动触发插件，当trigger为tap时，主动触发插件应该使用此方法
hide|否|无|主动隐藏插件  

```js
//完整参数、方法示例
var rd = new Rolldate({
    el: '#date',
    format: 'YYYY-MM-DD',
    beginYear: 2000,
    endYear: 2100,
    minStep:1,
    lang:{title:'自定义标题'},
    trigger:'tap',
    init: function() {
      console.log('插件开始触发');
    },
    moveEnd: function(scroll) {
      console.log('滚动结束');
    },
    confirm: function(date) {
      console.log('确定按钮触发');
    },
    cancel: function() {
      console.log('插件运行取消');
    }
})
rd.show();
rd.hide();

```

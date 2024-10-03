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
Name|Required|Default|Description
---|:-:|:-:|---
el|No|None|The DOM element to which the plugin is bound. The plugin uses `document.querySelector` internally. <br>You can also directly pass a DOM element object, only supports a single element.
format|No|'YYYY-MM-DD'|Date format, no restrictions. Rules: Year-YYYY Month-MM Day-DD Hour-hh Minute-mm Second-ss AM/PM-A Use one of /, -, space, : as separators, can be freely combined.
beginYear|No|2000|Start year of the date
endYear|No|2100|End year of the date
value|No|None|Default value for date initialization, e.g., '2018-03-18'
lang|No|Year, Month, Day...|Configure the plugin language, default: title:'Select Date', cancel:'Cancel', confirm:'Confirm',<br>year:'Year', month:'Month', day:'Day', hour:'Hour', min:'Minute', sec:'Second'
minStep|No|1|Minutes are divided by the specified number
init|No|null|Callback function before the plugin is triggered, return false to prevent the plugin from executing
moveEnd|No|null|Callback function after the plugin scrolls, the function returns one parameter (better-scroll instance)
confirm|No|null|Callback function before the confirm button is triggered, return false to prevent the plugin from executing, <br>return other values to modify the date, the function returns one parameter (selected date)
cancel|No|null|Callback function triggered when the plugin is canceled
trigger|No|'tap'|Default is to use tap to solve the 300ms delay of the click event on mobile devices, you can choose click to replace tap. Note that using tap will prevent other bound click events from being triggered
show|No|None|Actively trigger the plugin, when trigger is tap, actively trigger the plugin should use this method
hide|No|None|Actively hide the plugin  

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

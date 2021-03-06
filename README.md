# JavaScript Type Determination Methods Cheat Sheet

## Background
`typeof`, `Object.prototype.toString()`, `.constructor.toString()` and `.contstruct.name` property are three common ways in determining a variable type. This document summarizes the behaviours of these tools when given different variable types in different browsers.

## Quick Navigation
* [`Object.prototype.toString`](#objectprototypetostring)
* [`typeof`](#typeof)
* [`.constructor.toString()`](#constructortostring)
* [`.constructor.name`](#constructorname-property)
  
## `Object.prototype.toString()`
| argument | IE8 | IE9 | IE10 | IE11 | Edge | Chrome | Firefox | Safari |
| -------- | --- | --- | ---- | ---- | ---- | ------ | ------- | ------ |
| null |**_[object Object]_** | [object Null] | [object Null] | [object Null] | [object Null] | [object Null] | [object Null] | [object Null] | 
| undefined | **_[object Object]_** | [object Undefined] | [object Undefined] | [object Undefined] | [object Undefined] | [object Undefined] | [object Undefined] | [object Undefined] | 
| [] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | 
| new Array() | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | [object Array] | 
| {} | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | 
| new Object() | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | 
| "Hello World" | [object String] | [object String] | [object String] | [object String] | [object String] | [object String] | [object String] | [object String] | 
| 1 | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | 
| 1.1 | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | 
| NaN | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | [object Number] | 
| true | [object Boolean] | [object Boolean] | [object Boolean] | [object Boolean] | [object Boolean] | [object Boolean] | [object Boolean] | [object Boolean] | 
| function(){} | [object Function] | [object Function] | [object Function] | [object Function] | [object Function] | [object Function] | [object Function] | [object Function] | 
| /[a-z]/ | [object RegExp] | [object RegExp] | [object RegExp] | [object RegExp] | [object RegExp] | [object RegExp] | [object RegExp] | [object RegExp] | 
| new Date() | [object Date] | [object Date] | [object Date] | [object Date] | [object Date] | [object Date] | [object Date] | [object Date] | 
| document.getElementById('result') | **_[object Object]_** | [object HTMLDivElement] | [object HTMLDivElement] | [object HTMLDivElement] | [object HTMLDivElement] | [object HTMLDivElement] | [object HTMLDivElement] | [object HTMLDivElement] | 
| document.getElementsByTagName('div') | **_[object Object]_** | [object HTMLCollection] | [object HTMLCollection] | [object HTMLCollection] | [object HTMLCollection] | [object HTMLCollection] | [object HTMLCollection] | [object HTMLCollection] | 
| arguments | **_[object Object]_** | [object Arguments] | [object Arguments] | [object Arguments] | [object Arguments] | [object Arguments] | [object Arguments] | [object Arguments] | 
| new (Test = function() {}) | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | 
| new (function Test() {}) | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] | [object Object] |  [object Object] |
  
## `typeof`
| argument | IE8 | IE9 | IE10 | IE11 | Edge | Chrome | Firefox | Safari |
| -------- | --- | --- | ---- | ---- | ---- | ------ | ------- | ------ |
| null | object | object | object | object | object | object | object |object |
| undefined | undefined | undefined | undefined | undefined | undefined | undefined | undefined |undefined |
| [] | object | object | object | object | object | object | object |object |
| new Array() | object | object | object | object | object | object | object |object |
| {} | object | object | object | object | object | object | object |object |
| new Object() | object | object | object | object | object | object | object |object |
| "Hello World" | string | string | string | string | string | string | string |string |
| 1 | number | number | number | number | number | number | number |number |
| 1.1 | number | number | number | number | number | number | number |number |
| NaN | number | number | number | number | number | number | number |number |
| true | boolean | boolean | boolean | boolean | boolean | boolean | boolean |boolean |
| function(){} | function | function | function | function | function | function | function |function |
| /[a-z]/ | object | object | object | object | object | object | object |object |
| new Date() | object | object | object | object | object | object | object |object |
| document.getElementById('result') | object | object | object | object | object | object | object |object |
| document.getElementsByTagName('div') | object | object | object | object | object | object | object |object |
| arguments | object | object | object | object | object | object | object |object |
| new (Test = function() {}) | object | object | object | object | object | object | object |object |
| new (function Test() {}) | object | object | object | object | object | object | object | object |
  
## `.constructor.toString()`
| argument | IE8 | IE9 | IE10 | IE11 | Edge | Chrome | Firefox | Safari |
| -------- | --- | --- | ---- | ---- | ---- | ------ | ------- | ------ |
| []                                    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }            | function Array() { [native code] }            | function Array() { [native code] } | 
| new Array()                           | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }    | function Array() { [native code] }            | function Array() { [native code] }            | function Array() { [native code] }            | 
| {}                                    | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }           | function Object() { [native code] }           | function Object() { [native code] }           | 
| new Object()                          | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }           | function Object() { [native code] }           | function Object() { [native code] }           | 
| "Hello World"                         | function String() { [native code] }   | function String() { [native code] }   | function String() { [native code] }   | function String() { [native code] }   | function String() { [native code] }   | function String() { [native code] }           | function String() { [native code] }           | function String() { [native code] }           | 
| 1                                     | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }           | function Number() { [native code] }           | function Number() { [native code] }           | 
| 1.1                                   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }           | function Number() { [native code] }           | function Number() { [native code] }           | 
| NaN                                   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }   | function Number() { [native code] }           | function Number() { [native code] }           | function Number() { [native code] }           | 
| true                                  | function Boolean() { [native code] }  | function Boolean() { [native code] }  | function Boolean() { [native code] }  | function Boolean() { [native code] }  | function Boolean() { [native code] }  | function Boolean() { [native code] }          | function Boolean() { [native code] }          | function Boolean() { [native code] }          | 
| undefined                             | function Function() { [native code] } | function Function() { [native code] } | function Function() { [native code] } | function Function() { [native code] } | function Function() { [native code] } | function Function() { [native code] }         | function Function() { [native code] }         | function Function() { [native code] }         | 
| /[a-z]/                               | function RegExp() { [native code] }   | function RegExp() { [native code] }   | function RegExp() { [native code] }   | function RegExp() { [native code] }   | function RegExp() { [native code] }   | function RegExp() { [native code] }           | function RegExp() { [native code] }           | function RegExp() { [native code] }           | 
| new Date()                            | function Date() { [native code] }     | function Date() { [native code] }     | function Date() { [native code] }     | function Date() { [native code] }     | function Date() { [native code] }     | function Date() { [native code] }             | function Date() { [native code] }             | function Date() { [native code] }             | 
| document.getElementById('result')     | **_undefined_**                       | **_undefined_**                       | **_[object HTMLDivElement]_**         | **_[object HTMLDivElement]_**         | **_[object HTMLDivElement]_**         | function HTMLDivElement() { [native code] }   | function HTMLDivElement() { [native code] }   | function HTMLDivElement() { [native code] }   | 
| document.getElementsByTagName('div')  | **_undefined_**                       | **_undefined_**                       | **_[object HTMLCollection]_**         | **_[object HTMLCollection]_**         | **_[object HTMLCollection]_**         | function HTMLCollection() { [native code] }   | function HTMLCollection() { [native code] }   | function HTMLCollection() { [native code] }   | 
| arguments                             | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }   | function Object() { [native code] }           | function Object() { [native code] }           | function Object() { [native code] }           | 
| new Test()                            | function() {}                         | function() {}                         | function() {}                         | function() {}                         | function() {}                         | function () {}                                | function () {}                                | function () {}                                | 
| new Test()                            | function Test() {}                    | function Test() {}                    | function Test() {}                    | function Test() {}                    | function Test() {}                    | function Test() {}                            | function Test() {}                            | function Test() {}                            | 
  
## `.constructor.name` property
| argument | IE8 | IE9 | IE10 | IE11 | Edge | Chrome | Firefox | Safari |
| -------- | --- | --- | ---- | ---- | ---- | ------ | ------- | ------ |
| [] | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Array | Array | Array | Array | 
| new Array() | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Array | Array | Array | Array | 
| {} | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Object | Object | Object | Object | 
| new Object() | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Object | Object | Object | Object | 
| "Hello World" | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | String | String | String | String | 
| 1 | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Number | Number | Number | Number | 
| 1.1 | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Number | Number | Number | Number | 
| NaN | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Number | Number | Number | Number | 
| true | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Boolean | Boolean | Boolean | Boolean | 
| undefined | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Function | Function | Function | Function | 
| /[a-z]/ | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | RegExp | RegExp | RegExp | RegExp | 
| new Date() | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Date | Date | Date | Date | 
| document.getElementById('result') | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | HTMLDivElement | HTMLDivElement | HTMLDivElement | HTMLDivElement | 
| document.getElementsByTagName('div') | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | HTMLCollection | HTMLCollection | HTMLCollection | HTMLCollection | 
| arguments | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Object | Object | Object | Object | 
| new (Test = function() {}) | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | | **_Test_** | | **_Test_** | 
| new (function Test() {}) | **_undefined_** | **_undefined_** | **_undefined_** | **_undefined_** | Test | Test | Test | Test | 
  
## Remarks:
* IE8: Tested on Internet Explorer Version 8.0.7601.17514 running on Windows 7
* IE9: Tested on Internet Explorer Version 9.0.8112.16421 running on Windows 7
* IE10: Tested on Internet Explorer Version 10.0.9200.17148 running on Windows 7
* IE11: Tested on Internet Explorer Version 11.321.14393.0 running on Windows 10
* Edge: Tested on Microsoft Edge 38.14393.0.0 running on Windows 10
* Chrome: Tested on Chrome Version 53.0.2785.143 m (64-bit) running on Windows 10
* Firefox: Tested on Firefox Version 48.0.2 running on Windows 7
* Safari: Tested on Safari Version 10.0 (11602.1.50.0.10) running on Mac OS X El Capitan

## Found a mistake?
If you found a mistake in the documentation, please feel free to address it in the Issues section.

## Disclaimer
This documentation is written in the hope that it can give a quick overview of the behaviours, but there is no gurantee that this documentation is free of mistakes. If you are using its result in your production project, make sure you test your project well.

## License
Copyright (c) Yu H.  
Published under The MIT License (MIT)

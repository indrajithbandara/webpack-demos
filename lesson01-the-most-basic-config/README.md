# 基础配置

## 源码文件：`main.js`

```javascript
function say () {
  return "Hello World!";
}
module.exports = say
```
### 说明

- 通过 `module.exports = say` 导出模块，也可为 `exports = say`


## webpack 配置文件：`webpack.config.js`

```javascript
module.exports = {
  entry: './main.js',
  output: {
    filename: './dist/bundle.js',
  }
};
```

### 说明

- 最基础配置需要配 `entry`及 `output` 字段，即为 **输入** 和 **输出**，其中 `output` 最少需要一个 `filename` 字段，如果含有路径名称，本地没有会自动创建文件夹


## 打包生成的文件：`bundle.js`

```javascript
/******/ (function(modules) { // webpackBootstrap
/******/ 	// The module cache
/******/ 	var installedModules = {};
/******/
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/
/******/ 		// Check if module is in cache
/******/ 		if(installedModules[moduleId]) {
/******/ 			return installedModules[moduleId].exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = installedModules[moduleId] = {
/******/ 			i: moduleId,
/******/ 			l: false,
/******/ 			exports: {}
/******/ 		};
/******/
/******/ 		// Execute the module function
/******/ 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
/******/
/******/ 		// Flag the module as loaded
/******/ 		module.l = true;
/******/
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/
/******/
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = modules;
/******/
/******/ 	// expose the module cache
/******/ 	__webpack_require__.c = installedModules;
/******/
/******/ 	// define getter function for harmony exports
/******/ 	__webpack_require__.d = function(exports, name, getter) {
/******/ 		if(!__webpack_require__.o(exports, name)) {
/******/ 			Object.defineProperty(exports, name, {
/******/ 				configurable: false,
/******/ 				enumerable: true,
/******/ 				get: getter
/******/ 			});
/******/ 		}
/******/ 	};
/******/
/******/ 	// getDefaultExport function for compatibility with non-harmony modules
/******/ 	__webpack_require__.n = function(module) {
/******/ 		var getter = module && module.__esModule ?
/******/ 			function getDefault() { return module['default']; } :
/******/ 			function getModuleExports() { return module; };
/******/ 		__webpack_require__.d(getter, 'a', getter);
/******/ 		return getter;
/******/ 	};
/******/
/******/ 	// Object.prototype.hasOwnProperty.call
/******/ 	__webpack_require__.o = function(object, property) { return Object.prototype.hasOwnProperty.call(object, property); };
/******/
/******/ 	// __webpack_public_path__
/******/ 	__webpack_require__.p = "";
/******/
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(__webpack_require__.s = 0);
/******/ })
/************************************************************************/
/******/ ([
/* 0 */
/***/ (function(module, exports) {

function say () {
  return "Hello World!";
}
module.exports = say

/***/ })
/******/ ]);
```

### 说明

- 整体结构大致为这样

```javascript
(function (modules) {
  function __webpack_require__ () {
    // ...
  }
  __webpack_require__.m = []
  __webpack_require__.c = {}
  __webpack_require__.d = function(exports, name, getter) {}
  __webpack_require__.n = function(module) {}
  __webpack_require__.o = function(object, property) {}
  // p 属性为 output字段的 publicPath 属性
  __webpack_require__.p = ''
  // webpack 起始入口文件
  __webpack_require__.s = 
  return __webpack_require__(__webpack_require__.s)
})([function (module, exports) {}, ...])
```

## 命令行输出信息

```java
$ npm start                                                                                               system

> lesson1@0.1.0 start /Users/tt/Documents/webpack-demos/lesson01-the-most-basic-config
> webpack

Hash: 9faf9379e0b3892dc402
Version: webpack 3.10.0
Time: 74ms
           Asset     Size  Chunks             Chunk Names
./dist/bundle.js  2.54 kB       0  [emitted]  main
   [0] ./main.js 65 bytes {0} [built]
```

### 说明

- 

#Node的简介和主要内容

#### 简介

* 什么是Node.js
  * 不是语言，也不是框架，是Js运行时的平台
  * 简单来说Node.js就是JavaScript运行在服务端的一个平台

#### 主要内容


* Node.js中的javascript
  * 没有BOM、DOM
  * 只有Ecmascript基本的语法和浏览器上的Js相同
  * Node为javascript提供了一些服务器级别的API，这些API绝大多数都封装到一个具名的模块中了，就是核心模块:  例如fs、http模块
    * 文件操作的能力（fs模块）
    * http服务的能力（http模块）


- 模块系统

  - Node中有核心模块、第三方模块、用户自定义的模块

    - 核心模块是封装在Node中的，直接用**`requre`**引入
    - 第三方模块需要先使用把管理器安装后再引入
    - 用户自定义的模块即用户自己写的文件
  - 在Node中，没有全局作用域的概念，是一个模块就是一个独立的作用域
  - Node中可以通过 `require` 加载多个`javascript`脚本文件（文件即模块）
  - 有模块作用域，模块是完全封闭的，可以避免多个文件出现污染问题(例如a.js中定义的变量，不会被b.js锁污染)
  - 但有时模块之间也是需要通信的， 可以通过 `exports` 导出对象（空对象，每个模块中都有），  require  接受加载该文件模块，并拿到导出的对象接口


* ip地址和端口号
  * ip地址是用来定位计算机（服务器）的
  * 端口号是用来定位具体的应用程序

* http响应数据（http-fs.js）
  * 像输入www.baidu.com，百度会返回给你的响应数据是一个页面：百度首页
  * 这样响应页面的方式不是用res.write()进行字符串拼接,而是通过http的文件操作
  * 当然服务器响应的不会是文件，其实是文件的内容；浏览器会根据对应的Content-Type进行解析
  * Content-Type: 服务器每次响应数据最好告诉浏览器是什么数据，什么编码
  * 不同的资源对应的Content-Type不同，对照 http://tool.oschina.net/commons
  * 文本类型的数据要加编码格式，图片不用加

+ 代码风格
  + 推荐风格
    * [Javascript standard style](https://standardjs.com/index.html)
    * Airbnb Javsscript style
  + 当使用无分号的风格时，需注意：
    * [  (  ` 前面需要加分号(或者 ！ ~ &)  注： ``反引号是ES6中新增的一种用于包裹字符串的方式 叫做模板字符串  支持换行(相当与pre标签)和方便的拼接字符串
    * 例如匿名函数： `(function(){})`  需要这样写： `;(function(){})`
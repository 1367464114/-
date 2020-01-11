

## ES6

#### 为什么要学习ES6

 + 首先要了解ECMScript与JavaScript的关系
   	- 早在1996年，JavaScript的创造者把它交给了ECMA标准化组织，初衷是让JavaScript成为国际标准
   	   	- 第二年，ECMA 就发布 262 号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，这就是 ECMAScript 1.0 版
   	- 总结一下就是ECMAScript是JavaScript的规格，JavaScript是ECMAScript的一种实现

#### ES6 按正常理解应该是ECMAScript的6.0版本，但由于一些特定的历史原因，让它变得没那么简单

 + 首先要明确ES6和ECMAScript2015（es2015）的关系
   	+ 其实在一开始要更新ES5.1版本时，ES6就是ECMAScript的6.0版本
   	   	+ 因为这个版本引入的语法功能太多，而且制定过程当中，还有很多组织和个人不断提交新功能，无法用一次更新囊括所有的内容
   	   	+ 标准的制造者想让升级成为常规流程，于是决定标准在每年的 6 月份正式发布一次，作为当年的正式版本，而2015年6月发布的是ES6的第一个版本，也就是ES2015
   	+ 其实ES6应该算是个历史名词，而真正的版本时ES2015、ES2016、ES2017，到现在的ES2019

#### ES2015

###### ES2015标注提供了许多新的语法和编程特性以提高ECMAScript的开发效率并优化ECMAScript的开发体验

+ UNICODE编码的扩展

  + ES6解决了原来大于0xFFFF无法正确处理的问题

    + 如果直接在**\u** 后面跟上超过**0xFFFF**的数值(比如**\u20BB7**),**JavaScript**会理解成**\u20BB+7**。由于**\u20BB**是一个不可打印字符，所以只会显示₻7

    + ES6对这一点做出了改进，只要将码点放入大括号，就能正确解读该字符

    ```html
    	var unicode = "\u20BB7"; 
        var unicode2 = "\u{20BB7}";
        console.log(unicode);	//打印₻7	
        console.log(unicode2);	//打印𠮷
    ```
  
  + codePointAt()
  
    + JavaScript内部，字符以UTF-16的格式存储，每个字符固定为2个字节。
    + 而那些Unicode码点大于0xFFFF的字符需要4个字节储存的字符，JavaScript会认为它们是两个字符
  
    ```html
    	var s = '𠮷';
        console.log(s.length);	//打印的值是2
    ```
  
     + 而且charAt 方法无法读取整个字符，charCodeAt 方法只能分别返回前两个字节和后两个字节的值
  
    ```html
    	var s = '𠮷';
        console.log(s.charAt(0))	//打印的值是�
        console.log(s.charAt(1))	//打印的值是�
        console.log(s.charCodeAt(0))	//打印的值是55362
        console.log(s.charCodeAt(1))	//打印的值是57271
    ```
  
    + 所以，ES6提供了codePointAt方法，能够正确处理4个字节储存的字符，返回一个字符的码点
  
    ```html
    	var s = '𠮷a';
        console.log(s.codePointAt(0))	//打印的值是134071
        console.log(s.codePointAt(1))	//打印的值是57271
        console.log(s.codePointAt(2))	//打印的值是97
    ```
  
    + codePointAt方法是测试一个字符由两个字节还是由四个字节组成的最简单方法
  
    ```
    function is32Bit(c) {
      return c.codePointAt(0) > 0xFFFF;
    }
    
    is32Bit("𠮷") // true
    is32Bit("a") // false
    ```

+ let、const和块级作用域
  + let是用来定义变量的
  + const是用来定义常量的
  + 块级作用域实际上是let 带来的
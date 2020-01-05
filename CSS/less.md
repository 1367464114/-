## less

#### 和sass类似，也是一个CSS的预处理器



#### 安装

##### 在浏览器端

+ 去 [中文网](http://lesscss.cn/#download-options)下载最新的less,或者引入有效的CDN也可以

 + 在 .html 文件中引入 less.min.js 或 less.js
   	+ 引入 less.min.js 或 less.js 的目的是编译 less代码，所以最好将引入 less部分写在 less代码的后面

+ 将 style 标签中的类型改为 text/less
  + 要让浏览器知道它所识别的是 less 代码 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>less</title>
    <style type="text/less">
        .header{
            height: 60px;
            background-color: #ccc;
            .left{
                color: green;
            }
            .right{
                color: red;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <span class="left">111111</span>
        <span class="right">222222</span>
    </div>
</body>
<script src="less/less.min.js" ></script>
</html>
```

##### 如果想用链入式，怎么做？

​		刚开始我想，不就是链入式，我在外面写一个less文件引进来，把文件类型改了不就行了，可惜我失败了！

 + 想用链入式，我们只能引入css文件
   	- 本地引入.less文件会产生跨域问题，浏览器端使用时是使用ajax来拉取.less文件，因此直接在本机文件系统打开（即file://开头）或者是有跨域的情况下会拉取不到.less文件，导致样式无法生效。除非是在服务器端
 + 那么问题又来了，本地只能引入.css文件，那我还学less干什么
   	+ 这就用到一个工具[考拉](http://www.koala-app.com/)
   	+ 我们还是可以直接写.less文件的，写完将.less文件所在的目录直接拖入考拉中，就会自动帮我们在相应的文件夹里生成.css文件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>less</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <div class="header">
        <span class="left">111111</span>
        <span class="right">222222</span>
    </div>
</body>
<script src="less/less.js" ></script>
</html>
```

![image-20200105205438302](C:\Users\黄金文\AppData\Roaming\Typora\typora-user-images\image-20200105205438302.png)

##### 注释

 		less中有两种注释  //  或 /**/

​		不同点在于在 .less文件被编译成 .css文件后是否会保留到  .css文件中

​		// 是不会保留的

​		/**/是会保留的

##### 在服务器端

[点击查看](http://lesscss.cn/#using-less)



#### 和sass的区别

##### 运行环境

+ sass需要安装Ruby环境
+ less是基于JavaScript的，引入less.js文件就可以编译

##### 循环

+ sass可以循环遍历任何类型的数据
+ less只能循环数值

##### 变量

 + sass使用$定义
 + less则使用@



#### 特性

##### 嵌套规则








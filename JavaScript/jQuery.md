# jQuery

### 简介

- 定义
	+ jQuery其实就是JavaScript的一个函数库，还有一些比较优质的JavaScript库，类似 Prototype
	+ 其实就是辅助JavaScript开发的一个库
	+ 口号"写的少，做的多"

- 优点（其实就是让JS的开发过程变的更简单） 
    + 让操作HTML元素和事件更加方便
    + 比较成熟，文档很详细，还有一些成熟的插件
    + 制作一些特效和[动画]( https://www.w3cschool.cn/jquery/jquery-hide-show.html )
    + 目前最流行的JS框架，很多大公司在用 Google、微软
    + 兼容了所有的主流浏览器

- 下载
    + [jQuery下载地址](https://jquery.com/download/)


### 主要内容

- 语法
    + JavaScriptQuery就是JS查询的意思，查询HTML元素然后对其操作   $(selector).action()  例如： $("p").hide()
    + 基本格式  `$(document).ready(function(){代码})` 简写  `$(function(){代码})`

- 选择器
    + 基于XPath和CSS选择器，所以有许多和CSS选择器相似的地方
    + `$('p')` `$('#read')` `$('.read')`

- 筛选和查找元素
    + 其实就是根据元素之间的相对关系 向上、向下、水平地查找元素
    + 主要就是一些遍历函数 [查看网址](https://www.w3cschool.cn/jquery/jquery-traversing.html)

- 对HTML元素的操作
    + 对元素内容的操作
        * html()
            ```html
            <!-- 设置 -->
            $(document).ready(function(){
                $('.btn').click(function(){
                    $('p').html('你好，jQuery!')
                })
            })
            <!-- 返回 -->
            $(document).ready(function(){
                $('.btn').click(function(){
                    alert($('p').html())
                })
            })
            ```
        * text()
            ```html
            <!-- 设置 -->
            $(document).ready(function(){
                $('.btn').click(function(){
                    $('p').text('你好，jQuery!')
                })
            })
            <!-- 返回 -->
            $(document).ready(function(){
                $('.btn').click(function(){
                    alert($('p').text())
                })
            })
            ```
            * 和html()的区别： text()返回的是纯文本内容
        * val()
            * 可以设置或返回input标签中value的属性值
            ```html
            <!-- 设置 -->
            $(document).ready(function(){
                $('.btn').click(function(){
                    $(':text').val('你好，jQuery!') 
                })
            })
            <!-- 返回 -->
            $(document).ready(function(){
                $('.btn').click(function(){

                    alert($(':text').val())
                })
            })
            ```
    + 对元素属性的操作
        * 设置元素属性
            * attr()
                * 设置一个元素属性
                    ```html
                    $(function(){
                        $('img').attr('width', '200')
                    })
                    ```
                * 设置多个元素属性
                     ```html
                    $(function(){
                        $('img').attr({'width':'200', 'src':'images/2.png'})
                    })
                    ```
        * 删除元素属性
            * removeAttr()
                ```html
                $(function(){
                    $('img').attr('width')
                })
                ```

- 对样式的操作
    + 对样式类的操作
        * 添加样式类
            * addClass()可以添加一个或多个类  多个类时类名用空格分隔
            ```html
            $(function(){
                $('div').addClass('img color')
            })
            ```
        * 删除样式类
            * removeClass()
            ```html
            $(function(){
                $('h1,div').removeClass('color')
            })
            ```
        * 交替样式类
            
            * toggleClass() 可以设置或删除样式类
            
            ```html
            $(function(){
                $('btn').click(function(){
                    $('h1').toggleClass('color')
                })
            })
            ```
    + 对样式属性的操作
        * css()
            ```html
            <!-- 读取样式属性 -->
            $(function(){
                alert($('p').css('color'))
            })
            ```
            ```html
            <!-- 设置样式属性 -->
            $(function(){
                alert($('p').css('color', 'red'))
            })
            ```
        * offset()
            ```html
            <!-- 设置元素偏移量 -->
            $(function(){
                $('p').offset({top: 100,left: 200})
            })
            ```
            ```html
            <!-- 返回元素偏移量 -->
            $(function(){
                $('p').offset().top
            })
            ```
    
- jQuery中的DOM操作(其实就是一些DOM级别的操作)
    + 创建元素
        * $()
        ```html
        <!-- 直接创建一个节点  要注意格式 -->
        const $li = $('<li></li>')

        <!-- 创建文本节点 -->
        const $li = $('<li>jQuery</li>')

        <!-- 创建属性节点 -->
        const $li = $('<li title='jQuery'></li>')
        ```
    + 插入元素
        * 父子关系
            * append()可以在所选元素结尾插入一个或多个节点  多个节点用逗号分隔
            * prepend()所选元素开头
        * 兄弟关系
            * before()所选元素之前
            * after()所选元素之后
    + 复制元素
        
        * clone() 生成被选元素的副本  包括子节点、文本和属性
    + 替换元素
        * replaceWith()
        * replaceAll()
    + 包裹元素
        
        * wrap()
    + 删除元素
        
        * remove() 删除被选元素 包括文本、子节点、绑定的事件、附加的数据
    * empty()  删除被选元素 包括文本、子节点
        * detach()  只是从被选元素中移除所有内容
    
- jQuery的事件处理
    +  `$(document).ready(function(){})`
    + [参考链接](https://www.w3cschool.cn/jquery/jquery-ref-events.html)
    + 事件冒泡

- jQuery对象
    + 区分jQuery对象和DOM对象
    + jQuery对象中无法使用DOM对象中的方法，同理DOM对象也无法使用jQuery对象中的方法
    + 转化
        * jQuery对象转DOM对象
            * [index]  `const $foo = $('#foo'); const foo = $foo[0]; `
            * get(index)  `const $foo = $('#foo');  const foo = $foo.get(0)`
        * DOM对象转jQuery对象
            * 只需用`$()`把DOM对象包裹起来  例如： `const foo = document.getElementById('foo');  const $foo = $(foo)`

- jQuery与Ajax
    + load()
    + $.get()  $.post()
    + $.getJSON()
    + $.ajax()

- jQuery插件
    
    + [下载地址](https://plugins.jquery.com/)
    
- jQueryUI
    + [下载地址](https://jqueryui.com/)
    

### 了解

- jQuery Mobile

- Qunit
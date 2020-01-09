## Sass

#### 是一种层叠样式语言，是一个Css的预处理器，是Css的扩展语言



#### 用途

 + 当Css样式越写越多的时候，我们会发现它的复用性太差了，它的语法太简单了（选择器+声明）

 + Sass的出现就是为了帮助我们减少 CSS 重复的代码，节省开发时间

   

#### 特性

##### Sass通过增加规则、变量、混入、选择器、继承、内置函数等特性拓展了Css

 + 变量

   - 变量用于存储信息，可以重复使用

   - 一般可以存储颜色值、字符串、数字、布尔值等

   - 例如颜色值，通过引用变量的方式引入颜色值

   ```html
   $navColor: #06c1ae;
   
   .green {
   			border-right-color: $navColor;
   			top: -10px;
   			left: -8px;
   		}
   ```

    - Sass中的变量是有作用域的，上面的$navColor就只能在.green中起作用

    - 对应的会有全局作用域，利用 !global关键字来设置

      

#### 嵌套规则

##### 子元素的样式可以嵌套到父元素的样式里

```html
.go-back {
		position: relative;
		.arrow {
			@include arrow(10px, #fff, right);
			position: absolute;
			top: 22px;
			left: 10px;
			.green {
				border-right-color: $navColor;
				top: -10px;
				left: -8px;
			}
		}
	}
```

##### 开头相同的属性可以写在一起

```html
font: {
  family: Helvetica, sans-serif;
  size: 18px;
  weight: bold;
}

text: {
  align: center;
  transform: lowercase;
  overflow: hidden;
}
```



#### 混入

##### @mixin指令定义一个混入   @include指令引入到具体使用的文档中

+ 语法结构

  @mixin name { property: value; property: value; ... }

  ```html
  <!--定义了一个混入-->
  @mixin arrow($w: 10px, $c: #000, $dir: top) {
  	font-size: 0;
  	width: 0;
  	border: $w solid transparent;
  	border-#{$dir}-color: $c;
  }
  <!--引入混入-->
  .arrow {
      @include arrow(10px, #fff, right);
      position: absolute;
      top: 22px;
      left: 10px;
      .green {
      border-right-color: $navColor;
      top: -10px;
      left: -8px;
      }
  }
  ```

  命名时需要注意的是 - 和 _ 是一样的，例如 my_file 和 my-file 是一个混入

##### 混入是可以接受参数的，可以通过@include调用混入并传参

​		@include arrow(10px, #fff, right)

​		可以参考上面给的例子
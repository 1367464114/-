## BFC机制

 block formatting context：块级格式化上下文

#### 什么是 BFC

​	 bfc是一个独立的渲染区域，只有block-level box参与，它规定了内部的block-level box如何布局，并且与这个区域外部毫不相干。

#### 相关概念

 1、formatting context 直译过来就是 格式化上下文 的意思

 2、它其实是一个容器，一个决定文档如何渲染的容器

 3、常见的有：块级格式化上下文（BFC）和内联格式化上下文（inline formatting context简称IFC）

#### 触发 BFC 的情况

+ overflow 的属性值不是 visible

 + 应用实例
   	+ 当父容器中的子元素全都浮动时，会出现**高度塌陷**，原因是父容器没有 height ，靠子元素支撑，浮动后子元素脱离文档流不再占据父元素的空间。给父容器设置 oerflow: hidden;  
## BFC机制

+ BFC直译过来就是：block formatting context（块级格式化上下文）

  

#### 什么是 BFC

+ BFC是一个独立的渲染区域，只有block-level box参与，它规定了内部的block-level box如何布局，并且与这个区域外部毫不相干。

  

#### 相关概念

 1、首先要理解FC的概念

 + formatting context 直译过来就是 格式化上下文 的意思；它其实是一个容器，一个决定子元素如何渲染的容器

 2、常见的FC有：块级格式化上下文（BFC）和内联格式化上下文（inline formatting context简称IFC）

 3、Css3还有：网格布局格式化上下文（gridlayout formatting context 简称GFC==>display: grid）和 自适应格式化上下文(flex formatting context 简称 FFC==>display: flex)



#### 触发 BFC 的情况

- float 的属性值不是 none (left、right、inherit)

- overflow 的属性值不是 visible （auto、scroll、hidden）

- position 的属性值是 absolution 或 fixed

- display 的属性值是inline-block、table-cell、flex、table-caption或者inline-flex

  

#### 应用实例

- 当父容器中的子元素全都浮动时，会出现高度塌陷，原因是父容器没有 height ，靠子元素支撑，浮动后子元素脱离文档流不再占据父元素的空间。给父容器设置 oerflow: hidden;  就会解决这一问题。

- 解决外边距重合的问题

  ```javascript
  <style>
      .warp{
          width: 50px;
          height: 50px;
          background-color: bisque;
          margin: 100px;
      }
  </style>
  <body>
      <div class="warp"></div>
      <div class="warp"></div>
  </body>
  ```

  - 上面的代码中我给两个 div 分别设置 margin: 100px; 按道理说两个元素之间应该有200px的距离，但是真实情况如下图：
    <img src="https://upload-images.jianshu.io/upload_images/24278224-bb89905498159390.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" alt="图片3.png" style="zoom:50%;" />

  - 解决办法就是将两个存在外边距的元素分别放到一个BFC中，BFC中的元素不会受到外部的影响。

    

    + 代码：

    ```javascript
    <style>
        .warp{
            overflow: hidden;
        }
        .warp p{
            width: 50px;
            height: 50px;
            background-color: bisque;
            margin: 100px;
        }
    </style>
    <body>
        <div class="warp">
            <p></p>
        </div>
        <div class="warp">
            <p></p>
        </div>
    </body>
    ```

    

    - 实现的效果图：

    <img src="../../../%25E5%25AD%25A6%25E4%25B9%25A0%25E8%25AE%25B0%25E5%25BD%2595/study/imgs/%25E5%259B%25BE%25E7%2589%25872.png" style="zoom:50%;" />

- 生成两栏的布局，右边自适应

  - 效果图：

    <img src="../../../%25E5%25AD%25A6%25E4%25B9%25A0%25E8%25AE%25B0%25E5%25BD%2595/study/imgs/%25E5%259B%25BE%25E7%2589%25874.png" style="zoom:50%;" />

  - 代码：

  ```javascript
   <style>
          *{margin: 0;padding: 0;list-style: none;}
          .left{
              width: 100px;
              height: 200px;
              background-color: #ccc;
              float: left;
          }
          .right{
              overflow: hidden;
              height: 200px;
              background-color: blanchedalmond;
              border: 1px solid #000;
          }
      </style>
  </head>
  <body>
      <div class="left">left</div>
      <div class="right">right</div>
  </body>
  ```

  



注意： 当BFC内部有浮动时，为了不影响外部元素的布局，BFC计算高度时会包括浮动的高度
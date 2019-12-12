## HTML5拖放

### 实现步骤

+ 首先把要拖放的元素设置为可拖放

  ```html
    <h2 draggable="true">要拖放的文本</h2>
  
    <!-- 将draggable属性设置为true -->
  ```

  + 图片和链接默认是可托放的，所以不需要设置 draggable 属性

+ 然后就是规定要拖动什么

  + 利用 ondragstart 事件规定要拖动的数据

  * 具体就是使用 dataTransfer.setData()方法 规定数据的类型和值
  * 值也就是你要拖动数据或元素的标志 如id,类名，一般通过事件的 target 属性获取

+ 接下来就是放置元素

  - 先规定放置的地点

    	* 不能托放的原因是默认不能将数据或元素放到其他的元素中
    	* 最开始的想法就是给放置地点阻止默认设置

    - 利用 ondropover 事件
      - 当某被拖动的对象在另一对象容器范围内拖动时触发此事件

    * 在 ondropover 事件中设置  preventDefault()  方法

          
          <!-- 这是我定义的放置元素的地点 -->
          <div ondragover="drago(event)" ondrop='drop(event)'></div>
          
          <!-- 这是阻止默认设置 -->
          function drago(aa){
          	aa.preventDefault();
          }
          

  - 进行放置

    * 其实就是把拖动的元素插入到放置地点里

    * 利用 ondrop 事件进行具体的放置

      ```html
      <div ondragover="drago(event)" ondrop='dro(event)'></div>
          
                  function dro(aa){
                      aa.preventDefault();
                      <!-- 阻止默认事件 -->
                      let data = aa.dataTransfer.getData('Text');
                      <!-- 获取到被拖元素的id 通过刚才设置的值直接获取 -->
                      aa.target.appendChild(document.getElementById(data))
                      <!-- 将元素插入到放置的地点 -->
                  }
      ```

      

 + 实例

   ```javascript
   <!DOCTYPE html>
           <html lang="en">
           <head>
               <meta charset="UTF-8">
               <title>拖放</title>
               <script type='text/javascript'>
                   function myfun(aa){
                       aa.dataTransfer.setData("Text",aa.target.id);
                   }
                   function drago(aa){
                       aa.preventDefault();
                   }
                   function dro(aa){
                       aa.preventDefault();
                       let data = aa.dataTransfer.getData('Text');
                       aa.target.appendChild(document.getElementById(data))
                   }
               </script>
           </head>
           <body>
               <div ondragover="drago(event)" ondrop='dro(event)' id="345" style="width: 200px;height: 200px;border: 1px solid #000;"></div>
               <h2 draggable="true" ondragstart="myfun(event)" id="123">nmcjsdkfdksbfsklbjs</h2>
           </body>
           </html>
   ```

   
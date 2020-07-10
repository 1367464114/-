## JS基础面试题

#### 1、考察点：作用域、变量提升

```javascript
var a = 1;
console.log(a);
function f1(){
    console.log(a); //找a 先块级作用域 再全局作用域
    var a = 2;	//换成 let a = 2; 呢？？
}
console.log(a);
f1();
console.log(a);

打印结果：1 1 undefined 1
换成 let 之后：1 1 报错：ReferenceError 初始化之前无法访问到 a
```





#### 2、考察点：数据类型的存储、运算符的优先级

+ 题目

```javascript
var a = {n:1};
var b = a;
a.x = a = {n:2};
console.log(a.n,b.n);
console.log(a.x,b.x);

//输出  2  1
    undefined {n:2}
```

+ 解析

```javascript
var a = {n:1};
// 在栈中存放 a 和值（引用类型为地址，指向堆中的值）
// 堆中存放 {n: 1}
var b = a;
// 在栈中存放 b 和地址(例如 0b111) 指向堆中的值
// 堆中存放 {n: 1}
a.x = a = {n:2};
// . 优先级高于 =
// 先执行 a.x 通过a的地址访问到 {n: 1} 发现没有x,会帮x先声明 即为undefined
// 后执行 =  改变 a地址的指向 指向{n: 2},b的地址指向并没变
// 执行 a.x={n: 2}  0a111地址的指向数值为{n: 1,x:{n: 2}}  
// console.log(a.f)
console.log(a.n,b.n);
console.log(a.x,b.x);
```

+ 图解

![](../../../../Git/%E5%AD%A6%E4%B9%A0%E8%AE%B0%E5%BD%95/study/imgs/%E5%AF%B9%E8%B1%A1%E8%B5%8B%E5%80%BC.png)

+ 重点总结
  + JS数据类型的存储
    + 基本类型 ：变量名和值直接存放到栈中，赋值可以直接改变值
       + 引用类型 ：栈中存放的是变量名和地址  地址指向堆中存储的数值
  + .  的优先级高于 =
  + 启动画图工具：在搜索框中输入 mspaint





#### 3、考察点：变量提升的优先级、覆盖问题

+ 题目和打印结果

```javascript
console.log(c)
var c;	//如果换成  var c = 1; 打印结果？？
function c(a) {
    console.log(a);
    var a = 3;
    function a() {

    }
}
c(2);

打印结果：function c(a) {
            console.log(a);
            var a = 3;
            function a() {

            }
        }

		function a() {

    	}
```

+ 题目解析
  + 变量提升的优先级：函数声明>arguments>变量声明，也就是说先声明函数再声明变量
  + 那么当函数名和变量名相同时呢？会覆盖吗
    + 答案是：变量声明不会覆盖函数声明（也就解释了题目中打印函数声明的原因），换句话说就是函数声明把变量声明给覆盖了，严格来说不能叫覆盖，因为函数声明本来就在变量声明之前
  + 那语句换成  **var a = 1**  之后呢
    + 第一个打印结果不变
    + 第二个会报错：c 不是一个函数
    + 因为虽然变量声明不会覆盖函数声明，但是变量的赋值会覆盖函数的声明
    + 也就是说 执行 var a = 1  语句之后，函数声明被覆盖了，那么后面执行  c(2) 语句时肯定会报错啊，c 现在是变量了，不是函数了
# js基础

- 数据类型
- 常见流程控制语句
- 运算符

## 1.1使用方式：

内嵌式：将js代码写到 html文件中 

外联式：通过创建一个独立的js文件，将js文件引入html中

```html
<script src='js文件.js'></script>
```



## 1.2let  const var 定义变量的区别：

（1）使用var进行定义变量会进行变量提升（var所定义的变量会提升到前面)

（2）const用于定义常量，采用大驼峰命名（先定义 后使用）

（3）let用于定义变量，采用小驼峰命名（先定义 后使用）

变量命名规则：  由 字母，数字，`_`,$ 组成      由 字母,`_`,$  开头

## 1.3变量提升

1)**变量提升**： 会被提升到其所在作用域的顶部，但赋值操作不会被提升。因此，在声明之前访问该变量，会得到 `undefined`。

```html
//eg
console.log(myVar); // 输出: undefined
var myVar = 10;
console.log(myVar); // 输出: 10
//eg
var myVar; // 变量提升
console.log(myVar); // 输出: undefined
myVar = 10; // 赋值
console.log(myVar); // 输出: 10
```

2)函数提升

**函数声明：** 会被完全提升到其所在作用域的顶部，包括函数体。因此，可以在声明之前调用函数。

```js
myFunction(); // 输出: "Hello"
function myFunction() {
    console.log("Hello");
}
```

**函数表达式（Function Expression）：** 只会提升变量声明，而不会提升函数体。如果使用 `var` 声明函数表达式，则在声明之前访问该变量会得到 `undefined`；如果使用 `let` 或 `const` 声明，则会抛出 `ReferenceError`

```js
myExpression(); // 抛出 TypeError: myExpression is not a function
var myExpression = function() {
    console.log("World");
};
//相当于
var myExpression; // 变量提升
myExpression(); // 抛出 TypeError: myExpression is not a function
myExpression = function() {
    console.log("World");
};

```



## 1.4.常见数据类型：五基一引

- 基本数据类型 

> number   数字   0 111 
>
> string  字符串  ` ''   ""`
>
> Boolean  布尔   `true  false`
>
> null  空   `null`
>
> undefined  未定义类型  `undefined  `
>
> long  长整数

- 引用数据类型

> Object    对象  
>
> ​		--  object   `{key:value,key1:value1}`
>
> ​        -- array 数组  `[元素1,元素2]`
>
> ​        --Function 函数 `function 函数名(){函数体}`
>
> ​        --RegExp  正则  （校验某个字符串是否满足我的规则）   `/^1[3-9][0-9]{9}/`
>
> ​        --Date 日期类型 （格林威治日期格式）`Tue Feb 18 2025 10:49:22 GMT+0800 (中国标准时间)`

- 引用数据类型2.0

> 实例化定义      `new Object()`   `new Array()`   `new Funtion()`  `new RegExp()`  `new Date()`
>
> 字面量定义   `{}` `[]` `function(){}`  `/规则/`   `new Date()`

## 2.1对象操作

> 对象： 一个具象事物 
>
> 类： 具有相同属性的整体 抽象群体概念     

> 对象特征：  
>
> 头发，四肢 脸  肤色 姓名 学号    所有信息===对象的属性
>
> 吃饭  睡觉  爱好  学习 所有的行为动作===对象的方法(属性名===方法名) 方法值都是函数
>
> ```html
>  let user = {
>  name:'陈佳',
>  color:'黄色',
>  sno:'22000001',
>  hair:'黑头发',
>  eat:function(){ return '正在吃饭' },
>  study:function(){ return '正在学习...'}
> };
> console.log(user);
> //通过  对象.属性名  进行取值
> console.log(user.name) //陈佳
> // 我的名字是：xxx 我的肤色是xxxx,我的学号xxx,我早上九点xxxx,早上10点xxxx
> console.log('我的名字是：'+user.name+'我的肤色是'+user.color+',我早上九点'+user.eat()+',早上10点'+user.study()+'。');
> console.log(user.eat());
> console.log('我的名字是： '+user.name+'我的肤色是'+user.color+',我的学号'+user.sno+',我早上九点'+user.eat()+',早上10点'+user.study());
> // 短字符标签 模版字符串  `字符串直接写${变量}字符串`
> console.log(`我的名字是：${user.name} 我的肤色是${user.color},我的学号${user.sno},我早上九点${user.eat()},早上10点${user.study()}`);
> ```

### 2.2模版字符串

短字符标签 模版字符串  `字符串直接写${变量}字符串`

作用：

- 简化字符串插值

  ```js
  const name = "Alice";
  const age = 30;
  const message = `My name is ${name} and I am ${age} years old.`;
  ```

- 方便创建多行字符串

- ```js
  const html = `
    <div>
      <h1>Welcome</h1>
      <p>This is a multiline string.</p>
    </div>
  `;
  ```

- 支持标签模板，实现高级字符串处理

  ```js
  function highlight(strings, ...values) {
    let result = "";
    for (let i = 0; i < strings.length; i++) {
      result += strings[i];
      if (i < values.length) {
        result += `<span class="highlight">${values[i]}</span>`;
      }
    }
    return result;
  }
  const name = "Bob";
  const age = 25;
  const highlightedText = highlight`My name is ${name} and I am ${age} years old.`;
  console.log(highlightedText);
  // 输出: My name is <span class="highlight">Bob</span> and I am <span class="highlight">25</span> years old.
  
  ```

  

- 允许在字符串中嵌入任意 JavaScript 表达式

  ```js
  const x = 10;
  const y = 20;
  const sum = `The sum of ${x} and ${y} is ${x + y}.`;
  console.log(sum); // 输出: The sum of 10 and 20 is 30.
  ```

## 3.数组操作（重点）

### 3.1数组的基本使用

- 数组的定义 

```js
let arr = new Array(1,5,56,59,9,59,2,26)    //[1,5,56,59,9,59,2,26]
let arr = [1,5,56,59,9,59,2,26]     //[1,5,56,59,9,59,2,26]
let arr1 = ['1111','你好啊',1000,null]
let arr2 = [[123,456],[789,1]]   //二维数组
let arr3 = [{name:'陈冬雪'},{name:'陈瑶'}]  //数组
```

- 数组的使用 

通过数组[下标]来进行使用

- 数组属性  获取数组的长度

  ```js
  数组名.length  
  最大下标 = 数组名.length-1
  ```

### 3.2数组方法

#### 1）sort 排序 

会修改原数组的值

使用方法：

```js
//a:前一个元素 小的元素    b:后一个元素 大的元素
arr.sort(function(a,b){
    return a - b;   //a--->b
})
//其中注意：数字排序 必须传入function    字母排序必须只是sort()
    let arr1 = ['a','A','B','AA','b','0'];   //'0'==48  A==65  AA  B  a==97 b
    arr1.sort() 
    console.log(arr1);
 //对象数组排序 通过 a.属性 进行排序
 let arr5 = [{price:100},{price:200},{price:5}]
    arr5.sort(function(a,b){
            return a.price - b.price;
    })
    console.log(arr5)
```

#### 2)数组的增删改

> 修改原数组的值

- push   末尾添加元素

```js
arr.push(新增的元素)
```

- pop     末尾删除元素

```js
arr.pop()   
```

- unshift   头部添加一个元素

```js
arr.unshift(新增的元素)
```

- shift       头部删除一个元素

```js
arr.shift()
```

- splice    任意位置的增 删 替换	

```js
arr.splice(起始索引,需要删除几个元素，新增的元素1,新增元素2，新增....)
```

```js
//只新增元素，起始索引为新增之后的新增元素的索引
arr.splice(起始索引,需要删除几个元素，新增的元素1,新增元素2，新增....)
```

## 4.常见运算符

①　算术运算符： +   -   *   /  %   ++   -- 
②　比较运算符：==   !=    >   >=   <   <=   ===(全等于)   !==(不全等于)
③　条件运算符：(expr1) ? (expr2) : (expr3)
④　逻辑运算符：&&（与）    ||（或）    ! (非)
⑤　字符串运算符：+
⑥　赋值运算符： =   +=   -=   *=    /=    %=

## 5.数学内置方法

- toFixed(3)     保留小数位数 四舍五入

```js
3.55666.toFixed(3)    //3.557
```

- parseInt(‘3.55’)     转换为数字并保留整数    截取整数部分    3 
- parseFloat(‘3.55’)        转换为数字并保留整数+小数   3.55
- Number('3.55')     转换为数字   3.55

## 6.数学方法  Math

- floor(数字)    向下取整

```js
Math.floor(3.55)     //3
```

- ceil(数字)   向上取整

```js
Math.ceil(3.001)   //4
```

- PI     获取圆周率

```js
Math.PI    //3.141592653589793
```


# css基础

层叠样式表 (Cascading Style Sheets，缩写为 CSS），是一种 **样式表** 语言，用来**描述 HTML 文档的呈现**（**美化内容**）。

### 01-css引入方式

- 行内样式：CSS 写在标签的 style 属性值里

```html
<div style="color: red; font-size:20px;">这是 div 标签</div>
```

- 内部样式表：CSS 代码写在 style 标签里面

- 外部样式表：在 HTML 使用 link 标签引入css文件

  ```html
  <link rel='stylesheet' herf='./style.css'>
  ```

### 02-选择器

- **标签选择器：**使用**标签名**作为选择器 → 选中**同名标签设置相同的样式**。

​	例如：p, h1, div, a, img......

- **类选择器 ：**查找标签，**差异化**设置标签的显示效果。

  ```html
  <style>
    /* 定义类选择器 */
    .red {
      color: red;
    }
  </style>
  <!-- 使用类选择器 -->
  <div class="red">这是 div 标签</div>
  ```

  注意：

  * 类名**自定义**，不要用纯数字或中文，尽量用英文命名
  * 一个类选择器**可以供多个标签使用**
  * **一个标签可以使用多个类名**，类名之间用**空格**隔开

  > 开发习惯：类名见名知意，多个单词h可以用 - 连接，例如：news-hd。

  - **id选择器**

    id 选择器一般**配合 JavaScript** 使用，很少用来设置 CSS 样式

    ```html
    <style>  /* 定义 id 选择器 */  
        #red {    color: red;  }
    </style>
    <!-- 使用 id 选择器 -->
    <div id="red">这是 div 标签</div>
    ```

    

  - **通配符选择器**

​		作用：查找页面**所有**标签，设置相同样式。

​		通配符选择器： ***，不需要调用**，浏览器自动查找页面所有标签，设置相同的样式

> ​	通常用于清除默认样式

### 03-文字控制属性

1. 字体大小 font-size:  px;

2. 行高 line-height  属性值：num+px  如果只是num则表示标签font-size属性值的倍数

3. 字体样式（倾斜）font-style  倾斜：**italic**  不倾斜：**normal** 

4. 单行文字垂直居中：**行高属性值等于盒子高度属性值**

5. 字体类型：font-family

6. 文本缩进：text-indent  属性值：数字 + px  或者 **数字 + em**（推荐：**1em = 当前标签的字号大小**）

7. **文本对齐方式** ：text-align：left左对齐 right右对齐 center居中

8. 文本修饰线  **text-decoration**  属性值： none无  **underline** 下划线

   **line-through 删除线**  overline 上划线

9. color 文字颜色

### 04-复合选择器 

定义：由两个或多个基础选择器，通过不同的方式组合而成。

作用：更准确、更高效的选择目标元素（标签）。

#### 4-1后代选择器

通过在父选择器后面添加子选择器 { CSS 属性}，父子选择器之间用**空格**隔开。

作用：父元素里面的子元素添加样式 不影响父元素外的元素

```html
<style>
    后代选择器
  div span {
    color: red;
  }
</style>
<span> span 标签</span>
<div>
  <span>这是 div 的儿子 span</span >
</div>
```

#### 4-2子代选择器

选中某元素的子代元素（**最近的子级**）。父选择器 > 子选择器 { CSS 属性}，父子选择器之间用 **>** 隔开。

```html
<style>
  div > span {
    color: red;
  }
</style>

<div>
  <span>这是 div 里面的 span</span>变红
  <p>
    <span>这是 div 里面的 p 里面的 span</span>不变红
  </p>
</div>
```

#### 4-3并集选择器

选中**多组标签**设置**相同**的样式。

选择器写法：选择器1, 选择器2, …, 选择器N { CSS 属性}，选择器之间用 **,** 隔开。

```html
<style>
  div,
  p,
  span {
    color: red;
  }
</style>

<div> div 标签</div>
<p>p 标签</p>
<span>span 标签</span>
```

#### 4-4交集选择器 

选中**同时满足多个条件**的元素。

选择器写法：选择器1选择器2 { CSS 属性}，选择器之间连写 

```html
<style>
  p.box {
  color: red;
}
</style>

<p class="box">p 标签，使用了类选择器 box</p>
<p>p 标签</p>
<div class="box">div 标签，使用了类选择器 box</div>
```

> 注意：如果交集选择器中有标签选择器，标签选择器必须书写在最前面。

#### 4-5伪类选择器 

伪类选择器：伪类表示元素**状态**，选中元素的某个状态设置样式。

:hover 悬停时   :link访问时  :visited访问后  :active点击时

```html
<style>
  a:hover {
    color: red;
  }
  .box:hover {
    color: green;
  }
</style>

<a href="#">a 标签</a>
<div class="box">div 标签</div>
```

### 05-css特性

* 继承性：继承性：子级默认继承父级的**文字控制属性**。（如果标签有默认文字样式会继承失败）

* 层叠性：相同的属性会覆盖：**后面的 CSS 属性覆盖前面的 CSS 属性**；不同的属性会叠加：**不同的 CSS 属性都生效**

* 优先级:权重，当一个标签**使用了多种选择器时**，基于不同种类的选择器的**匹配规则**。

* **基础选择器**

  规则：选择器**优先级高的样式生效**。

  公式：**通配符选择器 < 标签选择器 < 类选择器 < id选择器 < 行内样式 < !important**

  ​           **（选中标签的范围越大，优先级越低)!important 权重最大

### 06-背景属性

1. 背景图 background-image: url(./images/1.png);

2. **平铺方式  background-repeat** ： no-repeat不平铺 repeat平铺  repeat-x repeat-y平铺方向

3. 背景图位置background-position：left bottom right top （也可以用数值px）

4.  背景图缩放background-size

   属性值：

   关键字

   *  cover：等比例缩放背景图片以完全覆盖背景区，可能背景图片部分看不见
   *  contain：等比例缩放背景图片以完全装入背景区，可能背景区部分空白

   百分比：根据盒子尺寸计算图片大小

   数字 + 单位（例如：px）

5. 背景图固定 作用：背景不会随着元素的内容滚动。background-attachment：fixed

### 07-元素级别（显示模式) 重点

#### 7-1块级元素

特点：

* 独占一行；宽度默认是父级的100%；添加宽高属性生效

#### 7-2行内元素

特点：

* 一行可以显示多个；设置宽高属性不生效；宽高尺寸由内容撑开

#### 7-3行内块元素

* 一行可以显示多个；设置宽高属性生效；宽高尺寸也可以由内容撑开

#### 7-4 元素转换

属性：**display**  属性值block 块级 inline行内 inline-block行内块
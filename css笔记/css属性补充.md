# css样式补充

1. #### 添加边框时：向内添加边框  

   box-sizing: border-box

2. #### css隐藏效果

   占据空间 visibility: hidden; hidden隐藏 visible显示

   不占据空间 dispaly: none 隐藏 block 显示

3. #### 光标移入显示手手

    cursor: pointer;

4. #### 在样式中计算属性：

   calc()     eg  width: calc(100% / 5)

   

5. #### 宽高比一比一（正方形）

   在只知道一边高宽的情况下aspect-ratio: 1 / 1;

   如果同时指定了`width`和`height`，`aspect-ratio`会被忽略。

   ```css
   .element {
       width: 200px;
       height: 300px; /* 高度固定为300px */
       aspect-ratio: 1 / 1; /* 被忽略 */
   }
   
   ```


# 2.**获取距离属性**：

## 2.1鼠标事件相关的坐标属性：

1. **`offsetX`**: 鼠标事件中，鼠标相对于目标元素的水平坐标。

   - 示例代码：

     ```javascript
     element.addEventListener('click', function(event) { 
         console.log(event.offsetX); 
     });
     ```

2. **`offsetY`**: 鼠标事件中，鼠标相对于目标元素的垂直坐标。

   - 示例代码：

     ```javascript
     element.addEventListener('click', function(event) { 
         console.log(event.offsetY); 
     });
     ```

3. **`pageX`**: 鼠标事件中，鼠标相对于页面的水平坐标（包含滚动偏移）。

   - 示例代码：

     ```javascript
     document.addEventListener('click', function(event) { 
         console.log(event.pageX); 
     });
     ```

4. **`pageY`**: 鼠标事件中，鼠标相对于页面的垂直坐标（包含滚动偏移）。

   - 示例代码：

     ```javascript
     document.addEventListener('click', function(event) { 
         console.log(event.pageY); 
     });
     ```

5. **`clientX`**: 鼠标事件中，鼠标相对于视口的水平坐标（不包括滚动条）。

   - 示例代码：

     ```javascript
     document.addEventListener('click', function(event) { 
         console.log(event.clientX); 
     });
     ```

6. **`clientY`**: 鼠标事件中，鼠标相对于视口的垂直坐标（不包括滚动条）。

   - 示例代码：

     ```javascript
     document.addEventListener('click', function(event) { 
         console.log(event.clientY); 
     });
     ```

------

## 2.2元素相关的距离属性：

1. **`offsetTop`**: 元素的顶部边缘相对于其最近已定位的祖先元素的距离。

   - 示例代码：

     ```javascript
     console.log(element.offsetTop);
     ```

2. **`offsetLeft`**: 元素的左边缘相对于其最近已定位的祖先元素的距离。

   - 示例代码：

     ```javascript
     console.log(element.offsetLeft);
     ```

3. **`getBoundingClientRect()`**: 返回元素相对于视口的矩形信息，包含 `top`, `right`, `bottom`, `left`, `width`, `height`。

   - 示例代码：

     ```javascript
     let rect = element.getBoundingClientRect();
     console.log(rect.top, rect.right, rect.bottom, rect.left, rect.width, rect.height);
     ```

------

## 2.3滚动条相关属性：

1. **`scrollTop`**: 获取元素的垂直滚动条位置。

   - 示例代码：

     ```javascript
     console.log(element.scrollTop);
     ```

2. **`scrollLeft`**: 获取元素的水平滚动条位置。

   - 示例代码：

     ```javascript
     console.log(element.scrollLeft);
     ```

------

## 2.4元素可视区域相关属性：

1. **`clientWidth`**: 获取元素的可视区域宽度（包括内边距，不包括滚动条、边框）。

   - 示例代码：

     ```javascript
     console.log(element.clientWidth);
     ```

2. **`clientHeight`**: 获取元素的可视区域高度（包括内边距，不包括滚动条、边框）。

   - 示例代码：

     ```javascript
     console.log(element.clientHeight);
     ```

3. **`offsetWidth`**: 获取元素的宽度（包括内边距、边框，但不包括外边距、滚动条）。

   - 示例代码：

     ```javascript
     console.log(element.offsetWidth);
     ```

4. **`offsetHeight`**: 获取元素的高度（包括内边距、边框，但不包括外边距、滚动条）。

   - 示例代码：

     ```javascript
     console.log(element.offsetHeight);
     ```

------

## 2.5元素滚动区域相关属性：

1. **`scrollWidth`**: 获取元素的滚动区域宽度（包括不可见部分）。

   - 示例代码：

     ```javascript
     console.log(element.scrollWidth);
     ```

2. **`scrollHeight`**: 获取元素的滚动区域高度（包括不可见部分）。

   - 示例代码：

     ```javascript
     console.log(element.scrollHeight);
     ```

------

## 2.6浏览器视口相关属性：

1. **`window.innerWidth`**: 获取浏览器视口的宽度（包括滚动条区域）。

   - 示例代码：

     ```javascript
     console.log(window.innerWidth);
     ```

2. **`window.innerHeight`**: 获取浏览器视口的高度（包括滚动条区域）。

   - 示例代码：

     ```javascript
     console.log(window.innerHeight);
     ```

------

## 2.7文档滚动位置：

1. **`document.documentElement.scrollTop`**: 获取整个文档的垂直滚动位置。

   - 示例代码：

     ```javascript
     console.log(document.documentElement.scrollTop);
     ```

2. **`document.documentElement.scrollLeft`**: 获取整个文档的水平滚动位置。

   - 示例代码：

     ```javascript
     console.log(document.documentElement.scrollLeft);
     ```
### css样式补充

1. #### 添加边框时：向内添加边框  

   box-sizing: border-box

2. #### css隐藏效果

   占据空间 visibility: hidden; hidden隐藏 visible显示

   不占据空间 dispaly: none 隐藏 block 显示

3. #### 光标移入显示手手

    cursor: pointer;

4. #### 在样式中计算属性：

   calc()     eg  width: calc(100% / 5)

   

5. #### 宽高比一比一

    在只知道一边高宽的情况下aspect-ratio: 1 / 1;

   如果同时指定了`width`和`height`，`aspect-ratio`会被忽略。

   ```css
   .element {
       width: 200px;
       height: 300px; /* 高度固定为300px */
       aspect-ratio: 1 / 1; /* 被忽略 */
   }
   
   ```

   
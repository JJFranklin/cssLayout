# CSS-Layout
旨在打造详尽的前端布局代码学习库（自从用了框架开发，CSS生疏了不少，所以开这个库练练手）

## 水平居中

子元素为行内元素还是块状元素，宽度一定还是宽度未定，采取的布局方案不同。

方案选择基本思路：
子元素为

> * 行内元素：对父元素设置`text-align:center`;
> * 定宽块状元素: 设置左右`margin`值为`auto`;
> * 不定宽块状元素: 设置子元素为`display:inline`,然后在父元素上设置`text-align:center`;
> * 通用方案: flex布局，对父元素设置`display:flex;justify-content:center`;

常用方法举例：
> **NOTE**:为了统一展示效果，在以下实例代码中对父子元素设置了固定宽高，实际可以不设置，由子元素内容来控制其宽度

>1. 方法一：[text-align + inline-block](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-水平居中（text-align%20%2B%20inline-block）.html)

**设置**：对父元素设置`text-align:center`(将会对行内元素起作用)，子元素设置`display:inline-block`（兼容IE6、7 时，替换为`display:inline;zoom:1;`）;

**优点**：兼容性良好

**缺点**： 需要额外代码修复因继承父元素的`text-align:center`对子元素内容排列造成的影响，如需要添加`.child{text-align:left}`


>2. 方法二：[table + margiin](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-水平居中（table%20%2B%20margin）.html)

**设置**：对子元素设置`display:table`(此元素会作为块级表格来显示，元素表现类似block，但是宽度跟随内容宽度)（兼容IE6、7 时，替换`div`结构为`table`结构即可）;

**优点**： 只需要对子元素进行设置

**缺点**： 向下兼容IE6、7时，需要更改html结构

>3. 方法三：[absolute + transform](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-水平居中（absolute%20%2B%20transform）.html)

**设置**：对父元素设置`position:realatve`(使其作为参照物)，对子元素设置`position:absolute;left:50%`(绝对定位元素的宽度也随内容而定)，然后对子元素设置`transform:translateX(-50%)`（兼容IE6、7 时，替换`div`结构为`table`结构即可）;

**优点**： 居中元素不会对其他元素造成影响

**缺点**：`transform`不兼容低版本IE

>4. 方法四：[flex + justify-content](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-水平居中（flex%20%2B%20justify-content）.html)

**设置**：对父元素设置`display:flex;justify-content:center`(这样其内部的元素会变为`align-items`)，`align-items`的宽度默认为`auto`，所以跟随内容宽度变化，继而`justify-content:center`属性会使子元素居中

**优点**：只需要对父元素进行设置

**缺点**：`flex`不兼容低版本IE


## 垂直居中

垂直居中对于子元素是单行内联文本、多行内联文本以及块状元素采用的方案是不同的。

> * 父元素一定，子元素为单行内联文本：设置父元素的`height`等于行高`line-height`
> * 父元素一定，子元素为多行内联文本：设置父元素的`display:table-cell`或`inline-block`，再设置`vertical-align:middle`;
> * 块状元素:设置子元素`position:absolute` 并设置`top、bottom`为0，父元素要设置定位为static以外的值，`margin:auto`;
> * 通用方案: flex布局，给父元素设置`{display:flex; align-items:center;}`

## 常用方法举例：

>1. 方法一：[table-cell + vertical-align](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-垂直居中（table-cell%20%2B%20vertical-align）.html)

**设置**：子容器高度不固定，对父元素设置`display:table-cell`(parent变为单元格，)，继续设置`vertical-align:center`（使inline元素垂直居中）;

**优点**：兼容性好（支持 IE 8）


**缺点**：IE 8 以下版本需要调整页面结构至 table

>2. 方法二：[absolute + transform](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-垂直居中（absolute%20%2B%20transform）.html)

**设置**：对父元素设置`position:realatve`(使其作为参照物)，对子元素设置`position:absolute;left:50%`(绝对定位元素的宽度也随内容而定)，然后对子元素设置`transform:translateY(-50%)`（兼容IE6、7 时，替换`div`结构为`table`结构即可）;

**优点**： 居中元素不会对其他元素造成影响

**缺点**：`transform`不兼容低版本IE

>3. 方法三：[flex + align-items](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-垂直居中（flex%20%2B%20align-items）.html)

**设置**：对父元素设置`display:flex`(align-items默认属性为stretch),继而设置`align-items:center`即可;

**优点**： 只需要对父元素进行设置

**缺点**：`flex align-items`不兼容低版本IE

## 水平居中且垂直居中

结合以上介绍到的水平和垂直居中方法进行设置

>1. 方法一：[text-align + inline-block + table-cell + vertical-align](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-完全居中（text-align%20%2B%20inline-block%20%2B%20table-cell%20%2B%20vertical-align）.html)

>2. 方法二：[absolute + transform](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-完全居中（absolute%20%2B%20transform）.html)

>3. 方法三：[flex + justify-content + align-items](https://hellowor1d.github.io/cssLayout/app/居中布局/居中布局-完全居中（flex%20%2B%20justify-content%20%2B%20align-items）.html)

## 多列布局

![效果图](http://7xo9xp.com1.z0.glb.clouddn.com/CSSLayout/float+margin-csslayout.jpg)

###  一列定宽，一列自适应宽度

1.一列定宽，一列自适应宽度（float+margin）

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/一列定宽一列自适应(%20float%20%2B%20margin%20).html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E4%B8%80%E5%88%97%E5%AE%9A%E5%AE%BD%E4%B8%80%E5%88%97%E8%87%AA%E9%80%82%E5%BA%94(%20float%20%2B%20margin%20).html)

2.**一列定宽，一列自适应宽度（float+margin）fix 改良版**

[预览](https://hellowor1d.github.io/cssLayout//app/多列布局/一列定宽一列自适应fix（float%20%2B%20margin%20）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E4%B8%80%E5%88%97%E5%AE%9A%E5%AE%BD%E4%B8%80%E5%88%97%E8%87%AA%E9%80%82%E5%BA%94fix%EF%BC%88float%20%2B%20margin%20%EF%BC%89.html)
>NOTE：此方法不会存在 IE 6 中3像素的 BUG，但 .left 不可选择， 需要设置 .left {position: relative} 来提高层级。 此方法可以适用于多版本浏览器（包括 IE6）。缺点是多余的 HTML 文本结构。

3.一列定宽，一列自适应宽度( float + overflow )

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/一列定宽一列自适应fix（float%20%2B%20margin%20）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E4%B8%80%E5%88%97%E5%AE%9A%E5%AE%BD%E4%B8%80%E5%88%97%E8%87%AA%E9%80%82%E5%BA%94(%20float%20%2B%20overflow%20).html)

4.一列定宽，一列自适应宽度( table + table-cell )

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/一列定宽一列自适应(%20table%20%2B%20table-cell%20).html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E4%B8%80%E5%88%97%E5%AE%9A%E5%AE%BD%E4%B8%80%E5%88%97%E8%87%AA%E9%80%82%E5%BA%94(%20table%20%2B%20table-cell%20).html)

5.一列定宽，一列自适应宽度( flex )

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/一列定宽一列自适应(%20flex%20).html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E4%B8%80%E5%88%97%E5%AE%9A%E5%AE%BD%E4%B8%80%E5%88%97%E8%87%AA%E9%80%82%E5%BA%94(%20flex%20).html)

### 多列定宽，一列自适应宽度

基于上面对于一列定宽一列自适应的需求实现，多列定宽只需要在原有一列定宽的基础上添加新的列即可，最后的列依然会自适应剩余宽度。

以 flex 的实现为基础可以作如下改造：
 ```html
    <div class="parent">
        <div class="left">
            <p>.left</p>
            <p>左侧定宽</p>
        </div>
        <!--添加了一列，CSS与 .left 公用-->
        <div class="center">
            <p>.center</p>
            <p>第二列定宽</p>
        </div>
        
        <div class="content">
            <p>.content</p>
            <p>flex：1 充满剩余空间，形成自适应效果，不设置的话默认为内容宽度</p>
        </div>
    </div>

    <style>
            .parent {
            display: flex;
        }
        
        .left,.center {
            width: 300px;
            height: 500px;
            margin-right:10px;
            background-color: lightblue;
        }
        
        .content {
            flex: 1;
            height: 500px;
            background-color: orange;
        }
    
    </style>
 ```
### 多列不定宽，一列自适应宽度 
基于以上一列定宽一列自适应的实现，进行改造，左侧不定宽区域的宽度任意（也可以由内部的内容来决定宽度就可以实现不定宽且自适应），继续增加一列即可变为多列，都很方便实现

## 多列等分布局

1.多列等分布局（float）

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/多列等分布局（float）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E5%A4%9A%E5%88%97%E7%AD%89%E5%88%86%E5%B8%83%E5%B1%80%EF%BC%88float%EF%BC%89.html)

2.多列等分布局（table）

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/多列等分布局（table）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E5%A4%9A%E5%88%97%E7%AD%89%E5%88%86%E5%B8%83%E5%B1%80%EF%BC%88table%EF%BC%89.html)

3.多列等分布局（flex）

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/多列等分布局（flex）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E5%A4%9A%E5%88%97%E7%AD%89%E5%88%86%E5%B8%83%E5%B1%80%EF%BC%88flex%EF%BC%89.html)

## 多列等高布局

1.多列等高布局（table）

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/多列等高布局（table）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E5%A4%9A%E5%88%97%E7%AD%89%E9%AB%98%E5%B8%83%E5%B1%80%EF%BC%88table%EF%BC%89.html)

2.多列等高布局（flex）

[预览](https://hellowor1d.github.io/cssLayout/app/多列布局/多列等高布局（flex）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%A4%9A%E5%88%97%E5%B8%83%E5%B1%80/%E5%A4%9A%E5%88%97%E7%AD%89%E9%AB%98%E5%B8%83%E5%B1%80%EF%BC%88flex%EF%BC%89.html)

## 全屏布局

1.弹性全屏布局（position）

[预览](https://hellowor1d.github.io/cssLayout/app/全屏布局/弹性全屏布局（position）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%85%A8%E5%B1%8F%E5%B8%83%E5%B1%80/%E5%BC%B9%E6%80%A7%E5%85%A8%E5%B1%8F%E5%B8%83%E5%B1%80%EF%BC%88position%EF%BC%89.html)

2.弹性全屏布局（flex）

[预览](https://hellowor1d.github.io/cssLayout/app/全屏布局/弹性全屏布局（flex）.html)    [源码](https://github.com/Hellowor1d/cssLayout/blob/gh-pages/app/%E5%85%A8%E5%B1%8F%E5%B8%83%E5%B1%80/%E5%BC%B9%E6%80%A7%E5%85%A8%E5%B1%8F%E5%B8%83%E5%B1%80%EF%BC%88flex%EF%BC%89.html)

3.百分比布局，以上宽度设置更改为百分比即可

4.根据内容完全自适应，position有限制无法满足，flex可以做到
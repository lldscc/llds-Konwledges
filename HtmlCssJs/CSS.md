## 引入方式

css写在style标签中，style标签一般写在head标签里面，title标签下面，选择器 {css属性}

CSS常见三种引入方式

+ 内嵌式：style标签中，head标签里，title标签下。作用当前页面，小案例

```css
<style>
    p{
        /* 文字颜色变红色 */
        color: red;
        /* 字变大 px:像素  */
        font-size: 30px;
         /* 背景颜色  */
        background-color: green;
        /* width  height */
        width: 200px;
        height: 200px; 
    }
</style>
```



+ 外联式  ：单独的css文件，作用多个页面；适合项目中

  ```css
  <head>
  		<meta charset="utf-8">
  		<title>myblog</title>
  		<link rel="stylesheet" type="text/css" href="css/css.css"/>
  </head>
  ```

  

+ 行内式 ：在标签的style属性中；作用当前标签；配合js使用

## 选择器

### 基础选择器

+ 标签选择器
+ 类选择器     class="类名"        .类名{}
+  id选择器      id      #类名{}
+ 通配符选择器 

### 进阶选择器

+ 后代选择器      格式：父代选择器  后代选择器 {css}；

+ 子代选择器      格式:   父代选择器 >子代选择器{css};//亲儿子

+ 并集选择器      格式 ：选择器，选择器{css};

+ 交集选择器      格式：选择器.选择器{css};

+ 伪类选择器    伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或选择第1个，第个元素。

  ```css
  a:link{}        /*选择所有未被访问的链接*/
  a:visited{}     /*选择所有己已被访问的链接*/
  a:hover{}       /*选择鼠标指针位于其上的链接*/
  a:active{}      /*选择活动链接（鼠标按下未弹起的链接）*/
  input:focus{}         /*伪类选择器用于选取获得焦点的表单元素。*/
  ```
  
  ```css
  //`:first-child` 和 `:last-child`：选择父元素下的第一个和最后一个子元素。
  
  ul li:first-child {
      font-weight: bold;
  }
  
  ul li:last-child {
      font-weight: normal;
  }
  //:nth-child(n)：选择元素在其父元素中的排位，其中n可以是一个数字、表达式或关键词。用于选择特定位置的元素。
  li:nth-child(odd) {
      background-color: lightgray;
  }
  
  ```
  
  



## 文本文字

+ **color**                            文本颜色   
+ **font-size**                     字体大小      默认16px
+ **font-weight**               字体粗细700
+ **font-style**                   倾斜效果     italic 倾斜；normal 正常
+ **font-family**                 字体
+ **font(复合属性)取值**：font:style weight size family;
  省略要求：只能省略前两个，如果省略了相当于设置了默认值
  注意点：如果需要同时设置单独和连写形式。要么把单独的样式写在连写的下面；要么把单独的样式写在连写的里面
+ **text-align**               对齐方式     左对齐：==left==； 居中对齐：==center== ； 右对齐：==right==
+ **text-indent**            文本缩进       像素px；字长度em
+ **text-decoration**	文本修饰无修饰： ==none==；删除线：==line-through==；下划线：==underline==；（使用 text-decoration：none；清除a标签默认的下划线）
+ **line-height**             行高= 文字加上下间距   像素px或倍数

标签水平居中    margin ：0 auto；

width  height           宽高度px



## 元素显示模式

|  元素模式  | 元素排列                 | 设置样式         | 默认宽度 | 包含           |
| :--------: | ------------------------ | ---------------- | -------- | -------------- |
|  块级元素  | 一行只能放一个块级元素   | 可设置宽高度     | 容器100% | 任何标签       |
|  行内元素  | 一行可以放多个行内元素   | 不可以设置宽高度 | 本身     | 文本或行内标签 |
| 行内块元素 | 一行可以放多个行内块元素 | 可以设置宽高度   | 本身     |                |



### 块元素

常见的块元素有< h1 >~< h6>、< p>、< div>、< u>、< ol>、< i>等，< div>标签是最典型的块元素。块级元素的特点：

+ 比较霸道，自己独占一行。
+  高度，宽度、外边距以及内边距都可以控制。 
+ 宽度默认是容器（父级宽度）的100%。
+ 是一个容器及盒子，里面可以放行内或者块级元素。

### 行内元素

常见的行内元素有< a>、< strong>、< b>、< em>、< i>、< del>、< s>、< ins>、< u>、< span>等，< span>标签是最典型的行内元素。行内元素的特点：

+ 相邻行内元素在一行上，一行可以显示多个。
+ 高、完直接设置是无效的。
+ 默认完度就是它本身内容的完度。
+ 行内元素只能容纳文本或其他行内元素。

### 行内块元素

在行内元素中有几个特殊的标签< img/>、< input/>、< td>,它们同时具有块元素和行内元素的特点。有些资料称它们为行内块元素。行内块元素的特点：

+ 和相邻行内元素（行内块）在一行上，但是他们之间会有空白缝隙。一行可以显示多个（行内元素特点）。
+ 默认完度就是它本身内容的宽度（行内元素特点）。
+ 高度，行高、外边距以及内边距都可以控制（块级元素特点）。

### 模式转换

+ **display：block**；            转换成块元素   
+ **display：inline**；            转换成行内元素
+ **display：inline-block；** 转换成行内块元素



## 背景

### 背景颜色

```css
background--color:颜色值；
```

一般情况下元素背景颜色默认值是transparent(透明)

### 背景色半透明

```
background:rgba (0,0,0,0.3);  /*alpha透明度，取值范围在0~1之间
```



### 背景图片

```css
background-image： none 或 url (url);
```

### 背景平铺

```css
background-repeat: repeat或 no-repeat 或 repeat-x 或  repeat-y;//平铺类型
```

不平铺：no-repeat;      X方向平铺：repeat-x;     Y方向平铺：repeat-y;

### 背景图片位置

```css
background-position:x y；
```

|    参考值    | 说明                                             |
| :----------: | :----------------------------------------------- |
| 像素：px  px | 百分数由浮点数字和单位标识符组成的长度值         |
|   方位名词   | top，center，bottom，left，center，right方位名词 |

### 背景图像固定

```css
background-attachment ： scroll(滚动，默认) / fixed(固定)
```

### 背景复合写法

background:  背景颜色   背景图片地址   背景平铺   背景图像滚动   背景图片位置：









# div+css布局

**页面布局常用属性**

1. 字体属性: font-size
2. 文本属性: text-decoration、text-align
3. 首行缩进: text-indent
4. 行高:line-height
5. 宽高属性: width、height、min-height、max-height
6. 背景属性: background
7. 列表属性:list-style
8. 字体颜色: color
9. 定位属性: position
10. 布局属性: display
11. 浮动属性: float、clear
12. 盒子模型; border、**margin、padding**，圆角边框: border-radius
13. 阴影:text-shadow、box-shadow
14. 移动居中transform：translate（50%，50%）

## 浮动属性 float

- 浮动元素在父元素内部浮动
- 浮动元素不占用空间

- 元素浮动，**display属性**失效，可以设置宽高，不会独占一行

语法：float：none/left/right



## 定位属性

position属性指定一个元素(静态的，相对的，绝对或固定)的定位方法的类型


|    值    |                             描述                             |
| :------: | :----------------------------------------------------------: |
| absolute | 生成**绝对定位**的元素，相对于 static定位以外的第一个父元素进行定位，元素的位置通过“left”  "top”  right”  以及“bottom”属性进行规定，**不占用原来位置**，移动参考点：网页的左上角；如果父元素有定位属性，移动参考点为父元素左上角。子绝父相：子级绝对定位，父级相对定位 |
|  fixed   | 生成**固定定位**的元素，相对于浏览器窗口进行定位元素的位置通过“left”，"top”“right”以及“bottom”属性进行规定 |
| relative | 生成**相对定位**的元素，相对于其正常位置进行定位因此，"left:20”会向元素的 LEFT 位置添加20 像素（相对自己），**会占用原来位置，定位参考点自己左上角**，标签的属性不变。 |
|  static  | 默认值。没有定位，元素出现在正常的流中(忽略 top,bottom,left, right 或者 zindex 声明)。 |

其他：z-index属性设置有定位属性的盒子的Z轴显示，后写的盒子在上，z-index设置1，可以使先定义的盒子优先显示



## display

display常见属性值

- none:隐藏对象不占原来的位置，（visibility：hidden隐藏占用位置，visibility：visible显示）（（透明度opacity：0隐藏占用位置）
- inline:指定对象为内联元素
- block:指定对象为块元素
- inline-block:指定对象为内联块元素，行内块元素
- table-cell:指定对象作为表格单元格
- flex:弹性盒





## 盒子模型

四个区域：

- 内容content
- 边框border
- 内边距padding
- 外边距margin

### 边框border

border：宽度 样式 颜色；

border：1px  solid red；

### 外边距margin

外边距合并：同级以最大值，父子级：子级影响父级，父级加边框不影响

设置值：margin：上  右   左  下 ；margin：上   右左  下；margin：上下 左右；margin：上下左右；（顺时针）

块元素居中：margin：0 auto；

清除默认：padding：0；margin：0；





## flex布局
[Flex文档](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#flexbox-background)


设置方式：父元素添加display：flex，子元素自动挤压或压伸；默认主轴为X

父元素：弹性容器；子元素：弹性盒子

默认：主轴是内容大小，侧轴铺满

### 主轴对齐方式

属性名：**justify-content**

| 属性值              | 效果                                                   |
| ------------------- | ------------------------------------------------------ |
| flex-start;flex-end | 弹性盒子从起点或终点开始排列                           |
| **center**          | 弹性盒子沿主轴居中排列                                 |
| **space-between**   | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子**之间** |
| **space-around**    | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子**两侧** |
| **space-evenly**    | 弹性盒子沿主轴均匀排列，弹性盒子与容器之间间距相等     |

### 侧轴对齐方式

属性名：**align-items**所有弹性盒子（在弹性容器中设置）；

**align-self**某个弹性盒子（在弹性盒子中设置）

| 属性值              | 效果                             |
| ------------------- | -------------------------------- |
| stretch             | 默认：弹性盒子没有高度沿侧轴铺满 |
| center              | 弹性盒子沿侧轴在容器居中排列     |
| flex-start;flex-end | 弹性盒子从起点或终点开始排列     |

### 修改主轴方向

**flex-direction：column** 改成垂直方向

### 弹性伸缩比

控制主轴方向的尺寸，属性值整数，占用父级剩余尺寸发份数

### 换行

属性：**flex-wrap：wrap**

### 行对齐方式

属性名**：align-content**

| 属性值              | 效果                                                   |
| ------------------- | ------------------------------------------------------ |
| flex-start;flex-end | 弹性盒子从起点或终点开始排列                           |
| **center**          | 弹性盒子沿主轴居中排列                                 |
| **space-between**   | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子**之间** |
| **space-around**    | 弹性盒子沿主轴均匀排列，空白间距均分在弹性盒子**两侧** |
| **space-evenly**    | 弹性盒子沿主轴均匀排列，弹性盒子与容器之间间距相等     |











## overflow内容溢出
CSS的`overflow`属性用于控制元素内容溢出时的处理方式。它有以下几个取值：

1. `visible`（默认值）：内容会溢出元素框，不会裁剪或添加滚动条。

2. `hidden`：内容会被裁剪，超出元素框的部分将被隐藏。

3. `scroll`：如果内容溢出元素框，会显示滚动条，即使内容没有溢出也会显示一个隐藏的滚动条。

4. `auto`：如果内容溢出元素框，会显示滚动条，如果内容没有溢出则不显示滚动条。

5. `inherit`：继承父元素的`overflow`属性。

这些取值可以应用于任何具有尺寸限制的元素，如`div`、`span`、`p`等。通过设置`overflow`属性，你可以控制元素在内容溢出时的显示方式。

例如，以下代码将创建一个宽度为200px、高度为150px的`div`元素，并设置其内容溢出时显示滚动条：

```css
div {
  width: 200px;
  height: 150px;
  overflow: auto;
}
```

请注意，`overflow`属性只能在具有尺寸限制的元素上生效，如果元素没有设置宽度或高度，`overflow`属性将不会起作用。

## SVG



```css
<svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor"
                            class="bi bi-person-fill" viewBox="0 0 16 16">
                            <path d="M3 14s-1 0-1-1 1-4 6-4 6 3 6 4-1 1-1 1H3Zm5-6a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z" />
                        </svg>
```

这段代码是通过直接嵌入SVG代码的方式加载SVG图标。在你提供的HTML代码中，SVG图标的内容被包含在`<svg>`元素内，这个`<svg>`元素定义了图标的宽度、高度、颜色等属性，并使用了一个SVG路径（`<path>`）来描述图标的形状。

具体来说：

- `xmlns`属性指定了SVG命名空间。
- `width`和`height`属性定义了SVG图标的宽度和高度。
- `fill`属性用于指定SVG图标的填充颜色。
- `class`属性包含了一个CSS类，这可以用于进一步样式化SVG图标。
- `viewBox`属性定义了SVG坐标系统的坐标范围。

总之，这种方式允许你在HTML中直接嵌入SVG图标，而无需引用外部SVG文件。这对于小型图标或需要通过CSS进行样式化的图标非常有用。SVG的内容直接包含在HTML文件中，这使得图标更容易管理和自定义。























## css布局标签

`<nav>` 是HTML中的一个语义元素，它通常用于定义一个页面上的导航栏（Navigation Bar）。导航栏用于导航到网站的不同部分、页面或链接到其他相关页面。`<nav>` 元素的主要目的是帮助搜索引擎和屏幕阅读器等工具理解页面的结构，并提供更好的可访问性。

通常，`<nav>` 元素包含导航链接，这些链接可以指向网站的主页、不同的部分、产品页面、关于页面、联系方式等。例如：

```html
<nav>
    <ul>
        <li><a href="/">首页</a></li>
        <li><a href="/products">产品</a></li>
        <li><a href="/about">关于我们</a></li>
        <li><a href="/contact">联系我们</a></li>
    </ul>
</nav>
```

在上面的示例中，`<nav>` 元素包含一个无序列表（`<ul>`），其中每个列表项（`<li>`）包含一个导航链接（`<a>`）。这样的结构有助于明确表示这是一个导航栏。

使用语义元素如 `<nav>` 而不是普通的 `<div>` 有助于提高页面的可访问性和可维护性，并使搜索引擎更容易理解页面的内容。当然，如何设计和样式化导航栏取决于具体的网站需求和设计风格。

HTML中有许多其他语义元素，类似于`<nav>`，用于更清晰地定义页面的不同部分和内容。这些元素有助于提高页面的可读性、可维护性和可访问性。以下是一些常见的语义元素：

1. `<header>`：用于标识页面或页面内的头部部分，通常包含站点的标题、标志、导航菜单等。

2. `<footer>`：用于标识页面或页面内的底部部分，通常包含版权信息、联系方式、相关链接等。

3. `<article>`：用于标识页面的独立内容单元，如一篇新闻文章、博客帖子、产品评论等。

4. `<section>`：用于将页面内容划分为逻辑上相关的部分，通常具有自己的标题。

5. `<aside>`：用于标识页面内容之外的附加信息，如侧边栏、广告、相关链接等。

6. `<figure>` 和 `<figcaption>`：`<figure>` 用于包含与文档主要内容相关的媒体，如图片、图表、音频或视频。`<figcaption>` 用于为`<figure>`提供标题。

7. `<main>`：用于标识文档的主要内容，每个页面应该只有一个`<main>` 元素。

8. `<details>` 和 `<summary>`：`<details>` 用于创建一个可展开的详细信息部分，而 `<summary>` 用于提供可点击的摘要或标题。

这些语义元素有助于提高页面的结构化程度，使其更易于理解和维护，同时还能提供更好的可访问性。根据具体的页面内容和需求，你可以选择适当的语义元素来组织和呈现信息。



# iconfont外部资源的使用 

### 图标（线上）

1. 添加到我的项目，生成在线css链接（Font class）

   ```
   //at.alicdn.com/t/c/font_4265869_q83fcnzi9c.css
   ```

2. 在自己的html文件添加css链接

   ```html
   <head>
       <link rel="stylesheet" href="//at.alicdn.com/t/c/font_4265869_q83fcnzi9c.css">
   </head>
   ```

3. 使用：在官网上找到图标的类名并添加

   ```html
   <div class="iconfont icon-guanli"></div>
   <div class="iconfont icon-fenlei"></div>
   ```

### 字体（线上）

1. 官网生成font-face代码

2. 添加到css文件中

   ```css
   @font-face {
       font-family: "阿里妈妈数黑体 Bold";
       font-weight: 700;
       src: url("//at.alicdn.com/wf/webfont/6IP2yTB9h7Wj/4Q3uZQoLB90p.woff2") format("woff2"),
           url("//at.alicdn.com/wf/webfont/6IP2yTB9h7Wj/Sne47RzgjoxA.woff") format("woff");
       font-display: swap;
   }
   ```

3. 用css选择器选择要更换字体样式的标签

```css
.h1 {
     font-family: '阿里妈妈数黑体 Bold';
}
```











## transform变换

复合语法：

```css
transform:translate() rotate() scale()...
```



transform 属性

+ `translate()`：平移元素，可以指定水平和垂直方向的偏移量。

  ```css
  transform:translate(x, y)
  transform:translateX(50px)
  transform:translateY(50px)
  /*百分比根据自身*/
  ```

  

+ `rotate()`：旋转元素，可以指定旋转的角度。

  ```css
  transform: rotate(45deg);
  /*度数单位：deg  可正可负 默认旋转中心点为元素中心*/
  
  transform-origin: x y;
  /*x y 可以是中心点(50% 50%)
  可以是像素或者方位( top bottom left right center)
  */
  ```

  

+ `scale()`：缩放元素，可以指定水平和垂直方向的缩放比例。

  ```css
  transform: scale(x,y);
  /*x y 宽高
  */
  ```

  

+ `skew()`：倾斜元素，可以指定水平和垂直方向的倾斜角度。

+ `matrix()`：通过 2D 矩阵变换来组合多个变换效果。

+ `transform-origin`： 设置变换原点

```css
  transform: rotate(6deg) translate(125%, -23%);
```



## transition过渡

谁变化加给谁

```css
transition:过渡的属性 时间 运动曲线 何时开始
/*
属性写all，全部
多个属性用逗号分隔
*/
```



### 属性

- `transition-property`：指定要过渡的属性名称，可以是单个属性或多个属性的列表。
- `transition-duration`：指定过渡的持续时间，以秒（s）或毫秒（ms）为单位。
- `transition-timing-function`：指定过渡的缓动函数（默认的缓动函数ease），用于控制过渡的速度曲线。
- `transition-delay`：指定过渡的延迟时间，以秒（s）或毫秒（ms）为单位。

简写`transition: property duration timing-function delay`



## animation动画

### 定义动画

```css
@keyframes move{
     0%{
        transform: translate(0,0);
    }
     100%{
          transform: translate(100px,100px);
   }
}
```



### 调用动画

```css
/*复合写法
linear 表示动画的缓动函数为线性，即匀速运动。
infinite 表示动画循环播放无限次。
alternate 表示动画在每次循环结束后反向播放。 */ 
animation: move 2s linear infinite alternate;

/*单个写法 */ 
animation-name:动画名称
animation-duration:持续时间
```

















# 实现

## 子元素在父元素水平垂直居中
要让 `<img>` 元素在 `<div>` 中水平垂直居中，你可以使用 CSS 的 flexbox 布局或者使用绝对定位。以下是两种方法的示例：

1. 使用 flexbox 布局：

```html
<div class="boximg">
  <div class="center">
    <img src="../../public/Icon/Category.png">
  </div>
</div>
```

```css
.boximg {
  display: flex;
  justify-content: center; /* 水平居中 */
  align-items: center; /* 垂直居中 */
}

.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

在这个示例中，我们使用了一个外层的 `<div>` 元素 `.boximg` 来包裹 `<img>` 元素，并使用 flexbox 布局来实现水平和垂直居中。通过设置 `.boximg` 的 `display: flex`，我们将其变为一个 flex 容器，并使用 `justify-content: center` 和 `align-items: center` 来使其内容水平和垂直居中。同时，我们还使用了一个内层的 `<div>` 元素 `.center` 来实现 `<img>` 元素的居中。

2. 使用绝对定位：

```html
<div class="boximg">
  <img src="../../public/Icon/Category.png" class="center">
</div>
```

```css
.boximg {
  position: relative;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

在这个示例中，我们将 `.boximg` 设置为相对定位，并将 `<img>` 元素 `.center` 设置为绝对定位。通过设置 `.center` 的 `top: 50%` 和 `left: 50%`，我们将其定位到父元素的中心位置。然后，使用 `transform: translate(-50%, -50%)` 将其向左和向上移动自身宽度和高度的一半，从而实现水平和垂直居中。




























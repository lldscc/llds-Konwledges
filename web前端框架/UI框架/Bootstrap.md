[Bootstrap框架官方文档](https://www.bootcss.com)

# 引入

## 普通项目

1. 在线引入

   ```html
   <!-- Bootstrap 的 CSS 文件 -->
   <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css"
           integrity="sha384-xOolHFLEh07PJGoPkLv1IbcEPTNtaed2xpHsD9ESMhqIYd0nLMwNLD69Npy4HI+N" crossorigin="anonymous">
   ```


   ```html
   <!-- 引入script -->
   <!-- jQuery &&  bootstrap.min.js &&  popper.min.js 先是 jQuery，然后是 Popper，最后是 JavaScript 插件 -->
   <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js"
           integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj"
           crossorigin="anonymous"></script>
   <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
   <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
   ```

   

# 栅格化布局

采用网格布局的区域，称为"容器"(container)。容器内部采用网格定位的子元素，是项目（item）

注意：项目只能是容器的顶层子元素，不包含项目的子元素，比如上面代码的<>元素就不是项目，Grid布局只对项目生效。

|                       | 超小屏幕 手机 (<768px）    | 小屏幕 平板（≥768px）                               | 中等屏幕 桌面显示器 (≥992px)                        | 大屏幕 大桌面显示器 (≥1200px)                       |
| :-------------------: | :------------------------- | :-------------------------------------------------- | :-------------------------------------------------- | --------------------------------------------------- |
|     栅格系统行为      | 总是水平排列               | 开始是堆叠在一起的，当大于这些阈值时将变为水平排列C | 开始是堆叠在一起的，当大于这些阈值时将变为水平排列C | 开始是堆叠在一起的，当大于这些阈值时将变为水平排列C |
| `.container` 最大宽度 | None （自动）              | 750px                                               | 970px                                               | 1170px                                              |
|        类前缀         | `.col-xs-`                 | `.col-sm-`                                          | `.col-md-`                                          | `.col-lg-`                                          |
|    列（column）数     | 12                         | 12                                                  | 12                                                  | 12                                                  |
|  最大列（column）宽   | 自动                       | ~62px                                               | ~81px                                               | ~97px                                               |
|    槽（gutter）宽     | 30px （每列左右均有 15px） | 30px （每列左右均有 15px）                          | 30px （每列左右均有 15px）                          | 30px （每列左右均有 15px）                          |
|        可嵌套         | 是                         |                                                     |                                                     |                                                     |
|    偏移（Offsets）    | 是                         |                                                     |                                                     |                                                     |
|        列排序         | 是                         |                                                     |                                                     |                                                     |



```
# Bootstrap V4

## 基本模板

```html
<!doctype html>
<html lang="zh-CN">
  <head>
    <!-- 必须的 meta 标签 -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap 的 CSS 文件 -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/css/bootstrap.min.css" integrity="sha384-xOolHFLEh07PJGoPkLv1IbcEPTNtaed2xpHsD9ESMhqIYd0nLMwNLD69Npy4HI+N" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

    <!-- JavaScript 文件是可选的。从以下两种建议中选择一个即可！ -->

    <!-- 选项 1：jQuery 和 Bootstrap 集成包（集成了 Popper） -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-7ymO4nGrkm372HoSbq1OY2DP4pEZnMiA+E0F3zPr+JQQtQ82gQ1HPY3QIVtztVua" crossorigin="anonymous"></script>

    <!-- 选项 2：Popper 和 Bootstrap 的 JS 插件各自独立 -->
    <!--
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js" integrity="sha384-9/reFTGAW83EW2RDu2S0VKaIzap3H66lZH81PoYlFhbGU+6BZp6G7niu735Sk7lN" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.6.2/dist/js/bootstrap.min.js" integrity="sha384-Lge2E2XotzMiwH69/MXB72yLpwyENMiOKX8zS8Qo7LDCvaBIWGL+GlRQEKIpYR04" crossorigin="anonymous"></script>
    -->
  </body>
</html>
```

# 工具类

## 颜色
### 文本颜色text

![image-20231001192621062](https://cdn.jsdelivr.net/gh/Shuncsx/image/image-20231001192621062.png)

```html
<p class="text-primary">.text-primary</p>
<p class="text-secondary">.text-secondary</p>
<p class="text-success">.text-success</p>
<p class="text-danger">.text-danger</p>
<p class="text-warning">.text-warning</p>
<p class="text-info">.text-info</p>
<p class="text-light bg-dark">.text-light</p>
<p class="text-dark">.text-dark</p>
<p class="text-body">.text-body</p>
<p class="text-muted">.text-muted</p>
<p class="text-white bg-dark">.text-white</p>
<p class="text-black-50">.text-black-50</p>
<p class="text-white-50 bg-dark">.text-white-50</p>
```

### 背景颜色Background color

<img src="https://cdn.jsdelivr.net/gh/Shuncsx/image/image-20231001192354581.png" alt="image-20231001192354581" style="zoom: 50%;" />

```html
<div class="p-3 mb-2 bg-primary text-white">.bg-primary</div>
<div class="p-3 mb-2 bg-secondary text-white">.bg-secondary</div>
<div class="p-3 mb-2 bg-success text-white">.bg-success</div>
<div class="p-3 mb-2 bg-danger text-white">.bg-danger</div>
<div class="p-3 mb-2 bg-warning text-dark">.bg-warning</div>
<div class="p-3 mb-2 bg-info text-white">.bg-info</div>
<div class="p-3 mb-2 bg-light text-dark">.bg-light</div>
<div class="p-3 mb-2 bg-dark text-white">.bg-dark</div>
<div class="p-3 mb-2 bg-white text-dark">.bg-white</div>
<div class="p-3 mb-2 bg-transparent text-dark">.bg-transparent</div>
```

## 定位
### 更改定位

```html
<div class="position-static">...</div>
<div class="position-relative">...</div>
<div class="position-absolute">...</div>
<div class="position-fixed">...</div>
<div class="position-sticky">...</div>
```

### 固定在顶部

```html
<div class="fixed-top">...</div>
```

### 固定在底部

```html
<div class="fixed-bottom">...</div>
```

## 间距

`m` -对于设置了 `margin` 的类

`p` -对于设置了 `padding` 的类
## 排列

```css
class="row justify-content-start"
class="row justify-content-center"
class="row justify-content-end"
class="row justify-content-around"
class="row justify-content-between"


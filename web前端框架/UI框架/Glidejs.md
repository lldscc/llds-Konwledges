[Gidejs滑块官方文档](https://glidejs.com/)
# 安装
无依赖性的JavaScript ES6滑块和旋转木马。它重量轻，灵活，速度快。设计用于滑动。

## 配置

```html
npm install @glidejs/glide
//css
//Required Core Stylesheet  glide.core -核心样式，Glide.js工作所需 
<link rel="stylesheet" href="node_modules/@glidejs/glide/dist/css/glide.core.min.css">
// Optional Theme Stylesheet  glide.theme -视觉样式。标记的可选样式
<link rel="stylesheet"href="node_modules/@glidejs/glide/dist/css/glide.theme.min.css">

<div class="glide">
            <!-- 1.图片 -->
            <div class="glide__track" data-glide-el="track">
                <ul class="glide__slides">
                    <li class="glide__slide"><img src="./img/02/02.png" alt=""></li>
                    <li class="glide__slide"><img src="./img/02/03.jpg" alt=""></li>
                </ul>
            </div>
            <!-- 2.按钮 -->
            <div class="glide__arrows" data-glide-el="controls">
                <button class="glide__arrow glide__arrow--left" data-glide-dir="<">&lt
                </button>
                <button class="glide__arrow glide__arrow--right" data-glide-dir=">">&gt</button>
            </div>
    
            <!-- 3.控制原点 -->
            <div class="glide__bullets" data-glide-el="controls[nav]">
                <button class="glide__bullet" data-glide-dir="=0"></button>
                <button class="glide__bullet" data-glide-dir="=1"></button>
            </div>
</div>

// 初始化
<script src="node_modules/@glidejs/glide/dist/glide.min.js"></script>
<script>
  new Glide('.glide').mount()
</script>
```




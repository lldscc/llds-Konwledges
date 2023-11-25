# 基础语法

## forEach

当你需要遍历数组或类数组对象（如 NodeList）中的每个元素时，`forEach` 是一个非常方便的方法。它可以帮助你简化代码，提高可读性，并且不需要使用传统的 `for` 循环。

`forEach` 方法的基本语法如下：

```javascript
array.forEach(function(currentValue, index, array) {
  // 在这里执行对每个元素的操作
});
```

- `array`：要遍历的数组或类数组对象。
- `currentValue`：当前遍历的元素。
- `index`（可选）：当前元素的索引。
- `array`（可选）：正在遍历的数组或类数组对象。

在回调函数中，你可以执行对每个元素的操作。回调函数的参数可以根据需要选择使用。通常情况下，我们只需要使用 `currentValue` 参数，它表示当前遍历的元素。

以下是一个示例，演示了如何使用 `forEach` 遍历数组并打印每个元素：

```javascript
const array = [1, 2, 3, 4, 5];

array.forEach(function(element) {
  console.log(element);
});
```

在这个示例中，我们定义了一个数组 `array`，然后使用 `forEach` 方法遍历数组中的每个元素。在回调函数中，我们将每个元素打印到控制台。

`forEach` 方法会自动遍历数组中的每个元素，并按顺序执行回调函数。它会处理数组中的每个元素，直到遍历完所有元素为止。

需要注意的是，`forEach` 方法没有返回值，它仅用于遍历数组。如果你需要对数组中的元素进行转换或筛选，并返回一个新的数组，可以考虑使用 `map` 或 `filter` 方法。







## filter过滤

`filter` 是 JavaScript 中用于数组操作的一个高阶函数。它可以帮助你根据指定的条件筛选出符合条件的数组元素，并返回一个新数组，而不改变原始数组。以下是详细解释 `filter` 的用法：

语法：

```javascript
const newArray = array.filter(callback(element[, index[, array]])[, thisArg])
```

- `array`：要进行筛选操作的原始数组。
- `callback`：一个用于测试每个元素的函数，它可以接受三个参数：
  - `element`：当前正在被测试的数组 元素。
  - `index`（可选）：当前元素在数组中的索引。
  - `array`（可选）：原始数组自身。
- `thisArg`（可选）：在 `callback` 函数中可用作 `this` 的值。

`filter` 方法会遍历原始数组中的每个元素，并对每个元素调用 `callback` 函数。如果 `callback` 函数返回 `true`，则该元素会包含在新数组中，否则将被排除。

示例：

```javascript
const numbers = [1, 2, 3, 4, 5];

// 筛选出偶数
const evenNumbers = numbers.filter(function(element) {
  return element % 2 === 0;
});

console.log(evenNumbers); // 输出 [2, 4]
```

在上面的示例中，`filter` 方法通过传递一个回调函数来筛选出原始数组 `numbers` 中的偶数，最后返回新数组 `evenNumbers`。

你也可以使用箭头函数来更简洁地编写上述示例：

```javascript
const numbers = [1, 2, 3, 4, 5];

// 使用箭头函数筛选出偶数
const evenNumbers = numbers.filter(element => element % 2 === 0);

console.log(evenNumbers); // 输出 [2, 4]
```

总之，`filter` 是一个强大的数组方法，它可以根据指定的条件轻松筛选数组元素，创建一个新的包含符合条件元素的数组，而不修改原始



## reduce

这段代码是在JavaScript中进行操作的。它的作用是计算一个名为`list`的数组中所有对象的`num`属性的总和，并将结果存储在变量`total`中。

让我们一步步来解释这段代码：

1. `let total =`：这是声明一个名为`total`的变量，并使用`let`关键字来定义它。`let`关键字用于声明变量，而`total`是变量的名称。

2. `this.list`：这是一个对象内部的属性访问方式，其中`this`指的是当前对象。它假设在对象的上下文中存在一个名为`list`的属性，这个属性是一个数组。

3. `.reduce((sum, item) => sum + item.num, 0)`：这是对数组`list`应用了`reduce`方法的部分。`reduce`方法是用来对数组中的每个元素执行一个指定的函数，并将结果累积起来的方法。

   - `(sum, item) => sum + item.num`：这是一个箭头函数，它接受两个参数，`sum`和`item`。在每次迭代中，`sum`表示累积的总和，而`item`表示数组中的当前元素。箭头函数的主体部分是`sum + item.num`，它的作用是将当前元素的`num`属性的值加到累积的总和上。

   - `0`：这是`reduce`方法的第二个参数，它是初始的累积值。在第一次迭代时，`sum`将等于初始值0，并且会逐步累积到所有元素的`num`属性的总和。

所以，最终，变量`total`将包含`list`数组中所有对象的`num`属性的总和。这段代码使用了高阶函数`reduce`来实现这个功能，它是一种非常灵活和强大的数组操作方法。

## slice字符串截取

# 



## 箭头函数

JavaScript中的箭头函数是一种更简洁的函数声明方式，通常用于定义匿名函数或简化函数表达式。以下是箭头函数的基本语法：

```javascript
(parameters) => expression
```

其中：

- `parameters` 是函数的参数列表，可以是零个或多个参数，用括号括起来。
- `=>` 表示箭头函数的定义。
- `expression` 是函数体，通常包含一条表达式，该表达式的结果将成为函数的返回值。

下面是一些示例：

1. 无参数的箭头函数：

   ```javascript
   () => console.log("Hello, World!");
   ```

2. 单个参数的箭头函数：

   ```javascript
   (x) => x * 2;
   ```

3. 多个参数的箭头函数：

   ```javascript
   (a, b) => a + b;
   ```

4. 使用花括号 `{}` 来定义更复杂的函数体，需要显式返回值：

   ```javascript
   (x, y) => {
     const sum = x + y;
     return sum;
   }
   ```

5. 当只有一个参数时，括号可以省略：

   ```javascript
   x => x * 2;
   ```

箭头函数有一些特性和限制：

- 箭头函数没有自己的 `this` 上下文，它们继承父级作用域的 `this` 值。
- 通常用于简单的函数表达式和回调函数。
- 不适合用作构造函数（不能使用 `new` 关键字）。
- 不能在箭头函数内使用 `arguments` 对象，但可以使用剩余参数 `...`。

## 数组

### join方法

JavaScript 中的 `join()` 方法用于将数组的所有元素连接成一个字符串，并返回该字符串。你可以指定一个可选的分隔符，该分隔符将在连接数组元素时插入到它们之间。

```javascript
array.join([separator])
```

- `array`：要连接的数组。
- `separator`（可选）：指定的分隔符。如果省略该参数，数组元素将以逗号分隔并连接在一起。

### map方法

JavaScript 中的 `map()` 方法是用于数组的高阶函数之一，它允许你创建一个新数组，其中的元素是原始数组经过指定函数处理后的结果。 `map()` 方法不会改变原始数组，而是返回一个新的数组，其中包含了处理后的元素。以下是 `map()` 方法的语法：

```javascript
array.map(callback(currentValue[, index[, array]])[, thisArg])
```

- `array`：要处理的数组。
- `callback`：对每个元素执行的函数。该函数接受三个参数：
  - `currentValue`：当前处理的元素的值。
  - `index`（可选）：当前处理的元素的索引。
  - `array`（可选）：调用 `map()` 方法的数组本身。
- `thisArg`（可选）：执行 `callback` 函数时使用的 `this` 值。

下面是一个使用 `map()` 方法的示例：

```javascript
const numbers = [1, 2, 3, 4, 5];

// 使用 map 将每个元素加倍
const doubled = numbers.map(function (num) {
  return num * 2;
});

console.log(doubled); // 输出：[2, 4, 6, 8, 10]
```

你也可以使用箭头函数来更简洁地定义回调函数：

```javascript
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(num => num * 2);

console.log(doubled); // 输出：[2, 4, 6, 8, 10]
```

`map()` 方法常用于将数组中的元素进行一定的转换或映射，例如计算每个元素的平方、将字符串数组转换为大写、从对象数组中提取特定属性等。它是函数式编程中非常强大且常用的工具之

# DOM

DOM（文档对象模型）操作允许你使用JavaScript来访问、修改和控制网页的内容和结构。以下是一些常见的DOM操作：

1. **选取元素：**
   - 通过标签名称、类名、ID 或其他属性选取元素。例如，`document.getElementById()`、`document.querySelector()` 和 `document.querySelectorAll()`。

2. **操作元素内容：**
   - 修改元素的文本内容：`element.textContent` 或 `element.innerHTML`。
   - 修改元素的属性：`element.getAttribute()` 和 `element.setAttribute()`。

3. **创建和添加元素：**
   - 创建新元素：`document.createElement()`
   - 添加元素到文档中：`element.appendChild()` 或 `element.insertBefore()`。

4. **删除元素：**
   - 从父元素中删除子元素：`element.removeChild()`。

5. **修改元素样式：**
   - 改变元素的CSS类：`element.classList.add()`、`element.classList.remove()`、`element.classList.toggle()` 等。
   - 直接修改元素的样式属性：`element.style.property`。

6. **事件处理：**
   - 添加事件监听器：`element.addEventListener()`。
   - 移除事件监听器：`element.removeEventListener()`。

7. **查询元素关系：**
   - 查找父元素：`element.parentElement`。
   - 查找子元素：`element.children`。
   - 查找兄弟元素：`element.nextElementSibling` 和 `element.previousElementSibling`。

8. **滚动和尺寸：**
   - 获取文档的滚动位置：`window.scrollY` 和 `window.scrollX`。
   - 获取元素的尺寸和位置：`element.getBoundingClientRect()`。

9. **表单操作：**
   - 获取表单字段的值：`element.value`。
   - 提交表单：`form.submit()`。

10. **动态加载资源：**
    - 创建并加载新的脚本：`document.createElement('script')` 和 `element.src`。

这只是DOM操作的一小部分，JavaScript提供了丰富的API来处理和操作DOM。根据你的需求，你可以使用这些操作来构建交互性强、动态的网页应用程序。如果你有特定的DOM操作问题或需要更多示例，请随时提问。

## js事件

1. 点击事件（click）：当用户单击元素时触发，通常用于按钮、链接等。

2. 鼠标悬停事件（mouseover和mouseout）：当鼠标移入或移出元素时触发，可用于创建悬停效果。

3. 键盘事件（keydown、keyup和keypress）：当用户按下或释放键盘上的按键时触发，通常用于表单输入和键盘快捷键。

4. 表单事件（submit、reset、change）：当用户提交表单、重置表单或输入字段值发生变化时触发，通常用于表单验证和交互。

5. 页面加载事件（load）：当整个页面及其所有资源加载完成时触发，通常用于执行初始化操作。

6. 页面卸载事件（unload）：当用户离开页面或关闭浏览器时触发，通常用于执行清理操作。

7. 资源加载事件（readystatechange）：当文档、图片或其他资源加载状态发生变化时触发，用于处理资源加载完成后的操作。

8. 鼠标滚动事件（scroll）：当用户滚动页面时触发，通常用于实现滚动效果。

9. 窗口大小改变事件（resize）：当用户调整浏览器窗口大小时触发，通常用于响应式设计。

10. 鼠标拖动事件（drag和drop）：用于处理元素的拖动和放置操作，通常与HTML5的拖放API一起使用。

11. 触摸事件（touchstart、touchmove、touchend）：用于响应触摸设备上的触摸操作，如滑动、点击等。

12. 动画事件（animationstart、animationiteration、animationend）：用于处理CSS动画的开始、迭代和结束事件。

这只是一小部分常见的JavaScript事件，实际上有更多事件可以用于不同的交互场景。你可以使用事件监听器来捕获这些事件，然后执行相应的JavaScript代码以响应用户的交互行为。



## 原型

![image-20231114150442276](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231114150442276.png)

### 原型对象

+ **构造函数**都有一个prototype属性,指向另一个对象，就是**原型对象**
+ 这个对象可以挂载函数，对象实例化不会多次创建原型上的函数，节约内存
+ 定义在prototype对象上的方法。实例可以共享
+ 构造函数和原型对象中this都指向实例化的对象



### 对象原型

**实例对象**都会有一个属性__proto__,指向**构造函数**的**原型对象**prototype

### constructor构造函数

constructor 构造函数在原型对象中，是原型对象的属性, 指向我们定义构造函数





# BOM











# JS库： jQuery

是一个流行的JavaScript库,它提供了丰富的功能,可以简化HTML文档的遍历、操作、事件处理等操作,使开发者能够更轻松地实现各种交互效果。它最初由John Resig开发,目前由开源社区维护。

# 正则表达式

## 语法

```
/表达式/
```

### test()方法

返回值：true；flase

```js
const str = '1234567890';
// 定义正则表达式
const reg = /6/
// 调用正则表达式的test方法,判断是否符合正则表达式
console.log(reg.test(str))
```

### exec()

在一个指定字符串中执行一个搜索匹配

返回值：成功返回数组；反之null

## 元字符

特殊字符，特殊含义的字符：`[a-z]`指 a到z

### 边界符

表示位置，开头结尾，

| ^    | 开始                    |
| ---- | ----------------------- |
| $    | 结束                    |
| ^a$  | 精确匹配，只选一个a字符 |

### 量词

表示重复次数，某个模式出现的次数

| *      | 重复零次或者更多次 |
| ------ | ------------------ |
| +      | 重复一次或者更多次 |
| ？     | 重复零次或者一次   |
| {n}    | 重复n次            |
| {n,}   | 重复n次或者更多次  |
| {n，m} | 重复n到m次         |



### 字符类

如：`/d`表示0-9

| [abc]       | 包含abc任意字符返回true |
| ----------- | ----------------------- |
| [a-z]       | 包含a-z任意字符         |
| [a-zA-Z0-9] |                         |
| [^a-z]      | 除了a-z                 |
| .           | 除了换行符，其他        |
| /d          | 匹配0-9任一数字:[0-9]   |
| /w          | 相当于[a-zA-Z0-9]       |



## 修饰符

```
/表达式/修饰符
```

ⅰ是单词ignore的缩写，正则匹配时字母不区分大小写

g是单词global的缩写，匹配所有满足正则表达式的结果

### replace替换

```
字符串.replace(/正则表达式/,'替换的文本')
```










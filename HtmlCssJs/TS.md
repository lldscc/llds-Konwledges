## TS环境

插件一:手动转换

```ts
npm install -g typescript

//查看版本
tsc -version

//转换成js文件
tsc ts文件

//运行js文件
node js文件
```

插件二：自动转换并运行

```
npm install -g ts-node

//运行
ts-node ts文件名
```

## 基本概念

元组和数组是不同的数据类型,但它们之间存在一些相似之处。

元组是一个不可变的序列,其中的元素可以是不同类型的数据,如数字、字符串、对象等。元组用逗号分隔的元素序列表示,例如,`(1, 'hello', {name: 'Alice'})`就是一个元组。

数组是一个可变的序列,其中的元素必须是相同类型的数据,通常是数字或字符串。数组用方括号[]表示,例如,`[1, 2, 3]`就是一个数组。

虽然元组和数组是不同的数据类型,但它们有一些相似之处。元组可以包含多个元素,每个元素可以是不同类型的数据,而数组中的所有元素都必须是相同类型的数据。此外,元组和数组都可以通过索引访问其元素,例如,`arr[0]`可以访问数组中的第一个元素,`arr1[1]`可以访问元组中的第二个元素。

因此,元组和数组是相似的,但它们是不同的数据类型,并且具有不同的属性和行为。
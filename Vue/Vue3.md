# 初始化

16.0以上的Node.js

```
npm init vue@next  //创建一个vue应用

npm  install  //安装依赖

npm run dev     //启动
```

# 组合式API

## 入口 setup

```vue
<!-- 复杂写法 -->
<script>
export default {
  setup(){
    // 数据
    const message = 'Hello Vue 3.0'
    const printlog = () => {
      console.log('print')
    }
    return {
      message,
      printlog
    }
  }
}
</script>
```

```vue
<!-- 语法糖写法  添加setup -->
<script setup>
const message = 'Hello Vue 3.0'
const printlog = () => {
  console.log('print')
}
<script>
```

## 响应式数据ref

```js
// 响应式ref
// 1.导入ref函数
import { ref } from 'vue'
// 2.执行函数 参数可以是简单类型 也可以是对象类型
const count = ref(0)
// ref响应式数据通过value值修改
// console.log(count)
const add = () => {
  count.value++
}
```

## 计算属性computed

```js
// 计算属性computed
// 1.导入computed函数
import { computed } from 'vue'
const computedState = computed(() => {
  // filter函数是数组函数，用于过滤数组
  return list.value.filter(item => item>2)
})
// 验证响应式
setTimeout(() => {
  list.value.push(9,10,11)
}, 3000)
```



## 监听属性watch

```js
import { watch } from 'vue'
//单个
watch(num, (newVal, oldVal) => { 
     console.log(newVal, oldVal)
   }
 )
//多个  用数组
watch([num, name],
  ([newNum, newName], [oldNum, oldName]) => {
    console.log(newNum, oldNum)
    console.log(newName, oldName)
  }
)

//immediate参数：立即监听
watch(num, () => { 
    console.log('启动')
  },{
    immediate:true
  }
)
//deep，watch默认监听ref的浅层，deep开启深层监听
```

## 生命周期函数

```js
// 导入生命周期函数
import { onMounted } from 'vue';

onMounted(() => {
  console.log('Mounted');
});

```

## 父子通信

### 父传子

基本步骤：1. 父组件中给子组件绑定属性；2.子组件内部通过props选项接受

vue3中使用宏函数defineProps

```vue
//父组件
<script setup >
// setup语法下局部组件不需要注册，直接引用即可
import Son from './Son.vue'
import { ref } from 'vue'
const num = ref(1)

</script>
<template>
  <div>
    <son :num="num" message="父组件信息"></son>
  </div>
</template>
```



```vue
//子组件
<script setup>
//编译器宏函数defineProps用来接收父组件传来的数据
    defineProps({
        //接收父组件传来的数据
        message:String,
        num:Number
    })
</script>

<template>
    <div class="">{{ message }} --{{ num }}</div>
</template>
```





### 子传父

基本步骤：1. 父组件给子组件标签通过@绑定事件 2.子组件内部通过$emit方法触发事件

vue3中使用defineEmits

```vue
//父组件
<script setup >
// setup语法下局部组件不需要注册，直接引用即可
import Son from './Son.vue'
const getMessage = (msg) => {
  console.log(msg)
}

</script>
<template>
  <div>
    <h1>父组件</h1>
    <!-- 绑定事件 -->
    <son @get-message="getMessage"></son>
  </div>
</template>
```

```vue
//子组件
<script setup>
//宏函数defineEmits 相当于emit(this.$emit)
const emit = defineEmits(['get-message'])
const sendMsg = () =>{
    // 触发自定义事件，传数据给父组件
    emit('get-message', 'hello world')

}
</script>
<template>
    
    <div class="">
        <h5>子组件</h5>
        <button @click="sendMsg">点击触发</button>
    </div>
</template>
```

## Pinia

[状态管理库](https://pinia.vuejs.org/zh/introduction.html#basic-example)

安装

```bash
npm install pinia
```

1. 定义Store（state和action）

   ```jsx
   export const useCounterStore =  defineStore('counter', ()=>{
       // 定义数据state
       const counter = ref(0)
       // 定义修改数据的方法(action 同步异步)
       const increment = () => {
           counter.value++
       }
       // 以对象的方式return供组件使用
       return {
           counter,
           increment
           }
   
   })
   ```

   

2. 组件使用Store

   ```jsx
   // 导入方法
   import { useCounterStore } from '@/stores/counter'
   // 创建 counter 对象实例
   const counterStore = useCounterStore()
   console.log(counterStore)
   ```

   

异步同步

```jsx
//  getter同步定义使用computed
 const doubleCount = computed(()=>count.value*2)

```


























# Ajax



[接口测试网站](https://jsonplaceholder.typicode.com/)

## axios

**axios是ajax的第三方库**

axios.js文件链接: 
https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js

### 基本使用

### 配置

```js
//1.baseUrl配置
axios.defaults.baseURL="地址"
```



```js
axios({
  url: '目标资源地址',
    // 查询字符串参数
  params:{
     id:1
  }
}).then((result) => {
  // 对服务器返回的数据做后续处理
  //result返回的是对象数组，其中data是数据
})
```



### 请求方法

| 请求方法 | 操作             |
| -------- | ---------------- |
| GET      | 获取数据（默认） |
| POST     | 提交数据         |
| PUT      | 修改数据         |
| DELETE   | 删除数据         |
| PATCH    | 修改数据         |

例如：POST提交

```js
 axios({
    url: 'http://hmajax.itheima.net/api/register',
    method: 'POST',
    data: {
      username: 'itheima007',
      password: '7654321'
    }
  })
```



### 错误处理

使用 axios 的 catch 方法，捕获这次请求响应的错误并做后续处理，语法如下：

```js
axios({
  // ...请求选项
}).then(result => {
  // 处理成功数据
}).catch(error => {
  // 处理失败错误
})
```



## ES6异步

`async`:是一种返回 Promise 对象的函数。它使用 async 关键字声明

`await`： 只能在 async 函数内部使用。它用于等待一个 Promise 对象的解决，并返回解决后的值。

```js
//someAsyncFunction 是一个异步函数，使用 await 等待其完成，然后将结果赋给 result。
async function fetchData() {
  const result = await someAsyncFunction();
  console.log(result);
}
```






























#  Vue2使用

在 Vue 2 中使用 Axios 是一种常见的方式来进行网络请求。Axios 是一个基于 Promise 的 HTTP 客户端，可以在浏览器和 Node.js 中发送 HTTP 请求。

下面是在 Vue 2 中使用 Axios 的一般步骤：

1. 安装 Axios：首先，需要在项目中安装 Axios。可以使用 npm 或 yarn 进行安装，例如：
```bash
npm install axios
```

2. 引入 Axios：在需要使用 Axios 的组件中，通过 `import` 语句引入 Axios：
```javascript
import axios from 'axios';
```

3. 发送 GET 请求：使用 Axios 发送 GET 请求的示例：
```javascript
axios.get('/api/users')
  .then(response => {
    // 请求成功后的处理逻辑
    console.log(response.data);
  })
  .catch(error => {
    // 请求失败后的处理逻辑
    console.error(error);
  });
```

4. 发送 POST 请求：使用 Axios 发送 POST 请求的示例：
```javascript
axios.post('/api/users', { name: 'John', age: 25 })
  .then(response => {
    // 请求成功后的处理逻辑
    console.log(response.data);
  })
  .catch(error => {
    // 请求失败后的处理逻辑
    console.error(error);
  });
```

在上述示例中，`/api/users` 是请求的 URL，`response.data` 包含了服务器返回的数据。可以根据需要进行相应的处理。

此外，还可以设置请求头、传递参数、处理请求拦截和响应拦截等。Axios 提供了丰富的配置选项和拦截器，可以根据具体需求进行使用。

需要注意的是，在使用 Axios 发送请求时，通常会遇到跨域问题。可以通过配置服务器端的 CORS（跨源资源共享）或使用代理来解决跨域问题。

以上是在 Vue 2 中使用 Axios 的基本用法。根据实际需求，还可以深入学习 Axios 的更多功能和用法。
















Uniapp
https://blog.csdn.net/Bonsoir777/article/details/127770920?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170193423316800226520739%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=170193423316800226520739&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-127770920-null-null.142^v96^pc_search_result_base5&utm_term=uniapp%E8%AF%B7%E6%B1%82%E6%95%B0%E6%8D%AE&spm=1018.2226.3001.4187

+ 

  ```
  
  ```

  



### 





# Vue3使用

安装

```
npm i axios
```

# Vue封装接口

[教程](https://www.bilibili.com/video/BV18R4y1J7sm/?spm_id_from=333.337.search-card.all.click&vd_source=dc3fbe24cdee834b2736194bdadc19e7)

+ vue项目安装axios

  ```
  npm install axios --save
  ```

+ scr下创建utils文件夹，request.js文件(封装请求网址相同字段)

  ```js
  //request.js
  import axios from 'axios'
  
  const request = axios.create({
      baseURL:'https://jsonplaceholder.typicode.com'
  })
  export default request
  
  ```

  ```js
  //入口文件App.vue
  import request from './utils/request';
  export default {
    created(){
      request({
        method: 'GET',
        url:'/posts',
        params:{text:'123',hello:'world'}
      })
    }
  }
  
  ```

  得到请求地址：https://jsonplaceholder.typicode.com/posts

​				

+ scr下创建api文件夹（为每个创建单独的请求js文件）

  | [/posts](https://jsonplaceholder.typicode.com/posts)       | 100 posts    |
  | ---------------------------------------------------------- | ------------ |
  | [/comments](https://jsonplaceholder.typicode.com/comments) | 500 comments |
  | [/albums](https://jsonplaceholder.typicode.com/albums)     | 100 albums   |
  | [/photos](https://jsonplaceholder.typicode.com/photos)     | 5000 photos  |
  | [/todos](https://jsonplaceholder.typicode.com/todos)       | 200 todos    |
  | [/users](https://jsonplaceholder.typicode.com/users)       | 10 users     |

  如：创建comments.js

  ```js
  import request from '../utils/request';
  
  function getComments(params) {
      return request({
        method: 'GET',
        url:'/comments',
        params
      })
  
  }
  export default getComments;
  ```

  创建api/index.js文件(导入导出以上接口文件)

  ```js
  import comments from './comments';
  
  export default {
      comments,
  }
  ```

  

+ 在main.js中导入api/index.js文件，添加到vue的原型对象上，可以通过 `this.$api` 访问这些函数和方法。

  ```js
  import api from './api'
  Vue.prototype.$api = api
  ```

  

+ 使用













```js
// api.js
import axios from 'axios';

const instance = axios.create({
  baseURL: 'your_base_url', // 设置基础URL
  timeout: 10000, // 设置请求超时时间
  headers: {
    'Content-Type': 'application/json',
    // 可根据需要添加其他请求头
  },
});

// 请求拦截器
instance.interceptors.request.use(
  (config) => {
    // 可在发送请求之前进行一些处理，例如添加 token 等
    return config;
  },
  (error) => {
    return Promise.reject(error);
  }
);

// 响应拦截器
instance.interceptors.response.use(
  (response) => {
    // 可在处理响应数据之前进行一些处理
    return response.data;
  },
  (error) => {
    // 处理响应错误
    return Promise.reject(error);
  }
);

export default instance;
```

```js
// otherFile.js
import api from './api';

// 发起GET请求
api.get('/user/info')
  .then(response => {
    console.log(response);
  })
  .catch(error => {
    console.error(error);
  });

// 发起POST请求
api.post('/user/login', { username: 'your_username', password: 'your_password' })
  .then(response => {
    console.log(response);
  })
  .catch(error => {
    console.error(error);
  });

```


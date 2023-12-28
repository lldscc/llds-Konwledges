# 一、工程结构

- **AppScope > app.json5**：应用的全局配置信息。
- **entry**：HarmonyOS工程模块，编译构建生成一个HAP包。
  - **src > main > ets**：用于存放ArkTS源码。
  - **src > main > ets > entryability**：应用/服务的入口。
  - **src > main > ets > pages**：应用/服务包含的页面。
  - **src > main > resources**：用于存放应用/服务所用到的资源文件，如图形、多媒体、字符串、布局文件等。关于资源文件，详见[资源分类与访问](https://developer.harmonyos.com/cn/docs/documentation/doc-guides-V3/resource-categories-and-access-0000001544463977-V3)。
  - **src > main > module.json5**：Stage模型模块配置文件。主要包含HAP包的配置信息、应用/服务在具体设备上的配置信息以及应用/服务的全局配置信息。具体的配置文件说明，详见[module.json5配置文件](https://developer.harmonyos.com/cn/docs/documentation/doc-guides-V3/module-configuration-file-0000001427744540-V3)。
  - **build-profile.json5**：当前的模块信息、编译信息配置项，包括buildOption、targets配置等。其中targets中可配置当前运行环境，默认为HarmonyOS。
  - **hvigorfile.ts**：模块级编译构建任务脚本，开发者可以自定义相关任务和代码实现。
- **oh_modules**：用于存放三方库依赖信息。关于原npm工程适配ohpm操作，请参考[历史工程迁移](https://developer.harmonyos.com/cn/docs/documentation/doc-guides-V3/project_overview-0000001053822398-V3#section167081936119)。
- **build-profile.json5**：应用级配置信息，包括签名、产品配置等。
- **hvigorfile.ts**：应用级编译构建任务脚本。

# 二、装饰器

![image-20231219202729275](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231219202729275.png)

### 1.@Builder构造函数





# 三、ArkUI组件

## 内置组件

### 1.容器组件

#### 1.1Column与Row

Column容器：垂直布局     	Row容器：水平布局

间距：space

![31757117011502152](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/31757117011502152.png)



**主轴布局：**

![59318817011504962](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/59318817011504962.png)





**交叉轴布局：**

Column容器的主轴是垂直方向，交叉轴是水平方向，其参数类型为HorizontalAlign（水平对齐）：Start  Center  End

Row容器的主轴是水平方向，交叉轴是垂直方向，其参数类型为VerticalAlign（垂直对齐）：Top  Center  Bottom

![67150017011505762](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/67150017011505762.png)

#### 2.2Stack

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

### 2.基础组件

基础组件是视图层的基本组成单元，包括Text、Image、TextInput、Button、LoadingProgress等

#### （1）Text组件

Text组件用于在界面上展示一段文本信息，可以包含子组件Span。

可使用fontColor、fontSize、fontStyle、 fontWeight、fontFamily这些文本样式，分别设置文本的

颜色、大小、样式、粗细以及字体

#### （2）Image组件

[配置网络图片权限](https://developer.harmonyos.com/cn/docs/documentation/doc-guides-V3/permission-list-0000001544464017-V3)成功加载网络图片，您需要在module.json5文件中申明网络访问权限。

```
{
    "module" : {
        "requestPermissions":[
           {
             "name": "ohos.permission.INTERNET"
           }
        ]
    }
}
```

![image-20231219203928696](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231219203928696.png)



#### （3）TextInput组件

![30136717011488682](C:\Users\Lenovo\Downloads\30136717011488682.png)

#### （4）Button组件

![13470717011490212](C:\Users\Lenovo\Downloads\13470717011490212.png)

#### （5）Silder组件

![27241817011498432](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/27241817011498432.png)



#### （6）弹窗组件

- 确认类：例如警告弹窗AlertDialog。
- 选择类：包括文本选择弹窗TextPickerDialog 、日期滑动选择弹窗DatePickerDialog、时间滑动选择弹窗TimePickerDialog等。
- 自定义弹窗CustomDialog。

#### （7）Blank

空白组件























#### （0）资源引用类型

Resource是资源引用类型，用于设置组件属性的值。将资源文件（字符串、图片、音频等）统一存放于resources目录下.

在string.json中定义Button显示的文本。

```
{
  "string": [
    {
      "name": "login_text",
      "value": "登录"
    }
  ]
} 
```

在float.json中定义Button的宽高和字体大小。

在color.json中定义Button的背景颜色。

组件通过“$r('app.type.name')”的形式引用应用资源。app代表应用内resources目录中定义的资源；type代表资源类型（或资源的存放位置），可以取“color”、“float”、“string”、“plural”、“media”；name代表资源命名，由开发者定义资源时确定。

```
Button($r('app.string.login_text'), { type: ButtonType.Capsule })
  .width($r('app.float.button_width'))
  .height($r('app.float.button_height'))
  .fontSize($r('app.float.login_fontSize'))
  .backgroundColor($r('app.color.button_color'))
```



### 3.列表组件

#### 3.1List线性列表组件

List是很常用的滚动类容器组件，一般和子组件ListItem一起使用，List列表中的每一个列表项对应一个ListItem组件。

<img src="https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231221131800464.png" alt="image-20231221131800464" style="zoom:50%;" />

**设置List排列方向alignListItem**

List组件里面的列表项默认是按垂直方向排列的，Vertical（默认值）：子组件ListItem在List容器组件中呈纵向排列。Horizontal：子组件ListItem在List容器组件中呈横向排列。

**高度自动**

.layoutWeight（1）

#### 3.2Grid网格组件

Grid组件一般和子组件GridItem一起使用，Grid列表中的每一个条目对应一个GridItem组件。

<img src="https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231221135115770.png" alt="image-20231221135115770" style="zoom:50%;" />

```ts
// 表示这个网格为4列,设置一种滑动
.columnsTemplate('1fr 1fr 1fr')
// 表示这个网格为4行
.rowsTemplate('1fr 1fr 1fr 1fr')
// 列间距为10vp
.columnsGap(10)
// 行间距也为10vp
.rowsGap(10)
```

### 4.Tab组件

Tabs组件仅可包含子组件TabContent，每一个页签对应一个内容视图即TabContent组件

```ts
Tabs({ barPosition: BarPosition.Start, controller:this.controller }) {
    TabContent() {
    Column(){
    Text('Pink-HarmonyOS')
      .fontSize(40)       }.width('100%').height('100%').backgroundColor(Color.Pink)
}
 .tabBar('Pink') //设置tab标签名
    .....
}
```

通过TabContent的tabBar属性设置TabBar的显示内容。使用通用属性width和height设置了Tabs组件的宽高，使用barWidth和barHeight设置了TabBar的宽度和高度。

![image-20231221141847012](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231221141847012.png)

----------------

Tabs的布局模式有Fixed（默认）和Scrollable两种

------------------

设置TabBar位置和排列方向：BarMode.Scrollabl设置TabBar位置和排列方向：

BarPosition.Start：vertical属性方法设置为false（默认值）时，页签位于容器顶部。vertical属性方法设置为true时，页签位于容器左侧。

BarPosition.End：vertical属性方法设置为false时，页签位于容器底部。vertical属性方法设置为true时，页签位于容器右侧

---------------------

自定义TabBar样式：使用@Builder装饰器修饰的函数



### 5.弹窗组件







## 自定义组件

ArkTS通过struct声明组件名，并通过@Component和@Entry装饰器，来构成一个自定义组件。

```ts
@Entry
@Component
struct ToDoList {...}
```











### @Builder









### @Styles

 





















































# 四、状态管理

![image-20231221144844150](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231221144844150.png)

ArkUI框架提供了多种管理状态的装饰器来修饰变量，使用这些装饰器修饰的变量即称为状态变量。

| 场景                   | 装饰器             |
| ---------------------- | ------------------ |
| 组件内的状态管理       | @State             |
| 从父组件单向同步状态   | @Prop              |
| 与父组件双向同步状态   | @Link              |
| 跨组件层级双向同步状态 | @Provide和@Consume |



## 1.@State

![image-20231223142937317](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231223142937317.png)

## 2.@Prop、@Link 、@Provide与@Consume

父子组件通信

 <img src="C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231223173751918.png" alt="image-20231223173751918" style="zoom:50%;" />

**@Prop、@Link**

```ts
//1.任务进度卡片(自定义组件)（单向）
TaskStatistics({finishTask:this.finishTask,totalTask:this.totalTask})
//2.新增任务按钮  3.任务列表(双向)（不能用this，用$引用）
TaskList({finishTask:$finishTask,totalTask:$totalTask})
```

**@Provide与@Consume**

@Provide修饰父组件数据，不用传递参数；@Consume修饰子组件数据

## 3.@Observed与@ObjectLink

![image-20231223175312433](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231223175312433.png)

对象的属性发生修改，无法更新视图的变化，@Observed修饰对象，@ObjectLink修饰变量属性.











































# 五、生命周期

## 1.UIAbility的生命周期

















# 六、渲染控制

## ForEach

![image-20231222173507142](https://raw.githubusercontent.com/lldscc/PicGo_bed/main/image/image-20231222173507142.png)

## if-else



# 







# 七、页面跳转

+ 路由的配置

  `src > main > resources > base > profile`下的main_pages.json配置规则。

+ 导入路由模块，配置

  ```js
  import router from '@ohos.router';
  
  .onClick(()=>{
            router.pushUrl({url:'pages/First'})
  })
  ```

  ![image-20231223192340922](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231223192340922.png)

  

  ![image-20231223192931140](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231223192931140.png)
  
  
  
  返回上一页
  
  Router.back()
  
  获取传递的参数
  
  getParams() 
  
  
  
  
  
  
  
  # 八、动画
  
  ## 页面动画
  
  ![image-20231224101252032](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231224101252032.png)
  
  ![image-20231224182443870](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231224182443870.png)
  
  
  
  ## 组件转场动画
  
  
  
  ![image-20231224192802252](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231224192802252.png)
  
  
  
  
  
  
  
  
  
  
  
  #  网络请求
  
  

## 1.http请求

1.导入http模块

```ts
import http from '@ohos.net.http';
```

2.创建一个HTTP请求，返回一个HttpRequest对象。

```ts
// 每一个httpRequest对应一个http请求任务，不可复用
let httpRequest = http.createHttp();
```

3.请求地址和数据，可在aboutToAppear周期函数

```ts
httpRequest.request('接口地址',{
  method: http.RequestMethod.POST,     // 可选，默认为http.RequestMethod.GET
  // 开发者根据自身业务需要添加header字段
  header: {
    'Content-Type': 'application/json'
  },
  // 当使用POST请求时此字段用于传递内容
  extraData: {
    "data": "data to send",
  },
  connectTimeout: 60000, // 可选，默认为60s
  readTimeout: 60000, // 可选，默认为60s
}, (err,data) => {
  if (!err) {
    // data.result为http响应内容，可根据业务需要进行解析
    console.info('Result:' + data.result);
    console.info('code:' + data.responseCode);
    // data.header为http响应头，可根据业务需要进行解析
    console.info('header:' + JSON.stringify(data.header));
    console.info('cookies:' + data.cookies); // 8+
  } else {
    console.info('error:' + JSON.stringify(err));
    // 该请求不再使用，调用destroy方法主动销毁。
    httpRequest.destroy();
  }
})
```



## 2.Promise方式

避免地狱回调

```ts
  aboutToAppear() {
    setInterval(() => {
      // 2. 常见http请求对象
      let httpReq = http.createHttp()
      // 3. 发起请求
     let promise =  httpReq.request('https://api.apiopen.top/api/sentences')
      promise.then((data) => {
        this.poem = JSON.parse(`${data.result}`).result.name
        this.from = JSON.parse(`${data.result}`).result.from
      })
    }, 2000)
  }

```

# 数据

## 1.首选项

首选项为应用提供Key-Value键值型的数据存储能力，以Key-Value形式存储数据

Key是不重复的关键字，Value是数据值。

## 2.常用接口

保存数据（put）、获取数据（get）、是否包含指定的key（has）、删除数据（delete）、数据持久化（flush）等





# Stage模型

## 1.概述



![image-20231226190346538](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231226190346538.png)

## 2.Stage应用配置

> [Stage应用配置](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V2/application-configuration-file-overview-stage-0000001428061460-V2)

**app.json5**

- 应用的全局配置信息，包含应用的包名、开发厂商、版本号等基本信息。
- 特定设备类型的配置信息。

**module.json5**

- Module的基本配置信息，例如Module名称、类型、描述、支持的设备类型等基本信息。
- 应用组件信息，包含UIAbility组件和ExtensionAbility组件的描述信息。
- 应用运行过程中所需的权限信息。

## UIAbility生命周期

UIAbility的生命周期包括Create、Foreground、Background、Destroy四个状态，WindowStageCreate和WindowStageDestroy为窗口管理器（WindowStage）在UIAbility中管理UI界面功能的Forground和Background两个生命周期回调。

<img src="C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231220094609669.png" alt="image-20231220094609669" style="zoom: 50%;" />



![image-20231227154312554](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231227154312554.png)



## 页面及组件的生命周期

![image-20231227160140392](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231227160140392.png)



## UIAbility启动模式

<img src="C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231227163003214.png" alt="image-20231227163003214" style="zoom:67%;" />

![image-20231227163137526](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20231227163137526.png)

standerd，multion都会创建多个实例，multion会销毁，standerd多个实例存在。






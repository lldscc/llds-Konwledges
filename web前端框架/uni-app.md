# 组件

## scroll-view

可滚动视图区域。用于区域滚动

## navigator

页面跳转，类似HTML中的`<a>`，但只能跳转本地页面。目标页面必须在pages.json中注册











## 创建项目

### HBuilderX创建

### 命令行创建

```powershell
//创建
vue create -p dcloudio/uni-preset-vue my-project
//运行
npm run dev:%PLATFORM%
//打包
npm run build:%PLATFORM%
```

| **%PLATFORM%值** | 平台       |
| ---------------- | ---------- |
| h5               | H5         |
| mp-weixin        | 微信小程序 |







GlobleStyle全局外观

view相当于div标签
text相当于span标签



## 页面配置



## 分包

1. 项目根目录创建subpkg

2. pages.json中与pages平级声明subPackages节点，用来定义分包相关的结构。

```json
"subPackages": [
	{
	"root": "subpkg",
	"pages": []
	}
]
```

3. 创建uniapp页面选择分包





## 发布

http://mp.weixin.qq.com

### 命令行

1. `打包`

```
pnpm build:mp-weixin
```

2. 微信开发者工具`上传`
3. 微信公众平台`提交审核`









### Hbuilder





## API

### [系统信息API](https://uniapp.dcloud.net.cn/api/system/info.html)

`uni.getSystemInfo` `uni.getSystemInfoSync`








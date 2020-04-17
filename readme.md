# Eapp.js （e-app.js） 标准
> 文始集团前端项目（`web`,`web-app`,`h5`,`混合开发`,`微信小程序`）常用组件命名标准

## 标准研究会组员
[@epaii(会长)](https://github.com/epaii), [@宋阳](https://github.com/songyangphp) ,[@wutongshenyuan](https://github.com/wutongshenyuan),[@zhangman0](https://github.com/zhangman0),[@k](https://github.com/k1919)

## 标准内容列表
- [Eapp.ui 弹框类](#ui)
  - [alert](#ui-alert)
  - [confirm](#ui-confirm)
  - [loading](#ui-loading)
  - [stopLoading](#ui-stopLoading)
  -  [toast](#ui-toast)
- [Eapp.Http 数据请求](#Http)
  - [setBaseUrl](#Http-setBaseUrl)
  - [setBaseData](#Http-setBaseData)
  - [setHeader](#Http-setHeader)
  - [post](#Http-post)
  - [get](#Http-get)
  + [Loading](#Http-Loading)
     + [Loading.post](#Http-Loading.post)
     + [Loading.get](#Http-Loading.get)
- [Eapp.localData 本地存储](#localData)
  - [set](#localData-set)
  - [get](#localData-get)
  - [remove](#localData-remove)
  - [clear](#localData-clear)
- [Eapp.window 窗口](#window)
  - [open方法](#window-open)
  - [openAndCloseThis方法](#window-openAndCloseThis)
  - [closeThis方法](#window-closeThis)
  - [replace方法](#window-replace)
  - [onshow事件](#window-onshow)
  - [onload事件](#window-onload)
  - [onclose事件](#window-onclose)
  - [params属性](#window-params)
- [Eapp.event 事件](#event)
  - [on方法](#event-on)
  - [emit方法](#event-emit)
- [Eapp.user 用户](#user)
  - [isLogin方法](#user-is-login)
  - [info方法](#user-info)
<!-- ## 灵活应用
  - 在模块化开发中，如果挂载再到全局变量中如 -->


## 一 <a id="ui">Eapp.ui</a>
### 弹框类


目前支持
| 方法        | 作用     |
| :---------- | :------- |
| alert       | 弹出框   |
| confirm     | 询问框   |
| loading     | 加载层   |
| stopLoading | 停止加载 |
| toast       | 提示框   |

## 一<a id="ui">Eapp.ui</a>
### 弹框类

*使用方法*

```JavaScript

/**
 * 第一种方法 
 * @param object 自定义弹出层的样式及功能 {"key" : "value"}
 */
Eapp.ui.alert({msg: ‘中间提示消息’, title:'标题提示'},function(){
  
});

/**
 * 第二种方法
 * @param msg 表示弹出框的内容
 * @callback  表示执行成功后的回调
 */
Eapp.ui.alert(‘操作完成’,function(){});

/**
 * 第三种方法

 * @callback  表示执行成功后的回调
 */
Eapp.ui.alert(function(){});

```


###  <a id="ui-confirm">`Eapp.ui.confirm` 方法 </a>
*表示询问框（目前最多允许两个提示按钮）*

*使用方法*

```javascript
/**
 * @param data1 表示取消按钮字符
 * * @param data2 表示确定按钮字符
 */

Eapp.ui.confirmt(您确定要删除吗,onok,oncancel)
```


###  <a id="ui-loading">`Eapp.ui.loading` 方法</a>
*表示弹出加载层*

*使用方法*

```javascript
/**
 * @param data 加载层提示的信息
 */

Eapp.ui.loading(‘这个是加载层’);
```



### <a id="ui-stopLoading">`Eapp.ui.stopLoading` 方法</a>
*表示清除弹出加载层，配合加载层使用*

*使用方法*

```javascript
Eapp.ui.stopLoading();
```

### <a id="ui-toast">`Eapp.ui.toast `方法</a>
*表示弹出提示信息*

三种不同的公共样式 

- Eapp.ui.toast.success
- Eapp.ui.toast.fail
- Eapp.ui.toast.text

*使用方法*

```JavaScript

/**
 * 第一种方法 
 * @param object 自定义弹出层的样式及功能 {"key" : "value"}
 */
Eapp.ui.toast.success({msg: ‘中间消息’, title:'提示'});

/**
 * 第二种方法
 * @param msg 表示弹出框的内容

 */
Eapp.ui.toast.success(‘操作完成’);
Eapp.ui.toast.fail(‘操作失败’);
Eapp.ui.toast.text(提示);
```



自定义参数说明
| 方法        | 作用                                     |
| :---------- | :--------------------------------------- |
| title       | 标题内容                                 |
| msg         | 内容                                     |
| color       | 标题颜色                                 |
| offset      | auto 默认坐标，即垂直水平居中            |
| offset      | ['100px', '50px'] 定义top、left坐标      |
| area - 宽高 | 默认：auto 自适应     ['500px', '300px'] |


## 二 <a id="Http">Eapp.http</a>
### 请求数据
目前支持

| 方法         | 作用                    |
| :----------- | :---------------------- |
| setBaseUrl   | 设置请求远程地址        |
| setBaseData  | 设置常用的请求字段      |
| setHeader    | 设置请求headers         |
| post         | post请求                |
| get          | get请求                 |
| Loading      | 带loading效果的请求     |
| Loading.post | 带loading效果的post请求 |
| Loading.get  | 带loading效果的get请求  |


### <a id="Http-setBaseUrl">`setBaseUrl` 方法</a> 
*表示设置请求远程地址*


*使用方法*

```javascript
/**
 * @param url 要设置的远程地址
 */

Eapp.Http.setBaseUrl(url);
```

### <a id="Http-setBaseData">`setBaseData` 方法</a> 
*设置常用的请求字段*

*使用方法*

```javascript
/**
 * @param data 要设置常用的请求数据 Object 形如 {"key" : "value"}
 */

Eapp.http.setBaseData(data);
```

### <a id="Http-setHeader">`setHeader` 方法</a> 
*设置请求headers*

*使用方法*

```javascript
/**
 * @param data 要设置的header Object 形如 {"key" : "value"}
 */
Eapp.http.setHeader(data);
```


### <a id="Http-post">`post` 方法</a> 
*post请求*


|  参数          |                备注                |
|  :------- ---- |  :-----------------------------:  |
|  url            |        请求接口地址        |
|  data          |            请求数据            |
|  function  |  请求成功的回调方法  |
|  error        |  请求失败的回调方法  |

*使用方法*

```javascript
Eapp.http.post(url,data,function(data) {
  console.log(data);
},function(data) {
  alert(data.msg);
})
```

### <a id="Http-get">`get` 方法</a> 
*get请求*

| 参数     |        备注        |
| :------- | :----------------: |
| url      | 请求接口地址和数据 |
| function | 请求成功的回调方法 |
| error    | 请求失败的回调方法 |

*使用方法*

```javascript
Eapp.http.get('url',function(data) {
  console.log(data);
},function(data) {
  alert(data.msg);
})
```


## <a id="Http-Loading">`Loading` 方法</a> 

### <a id="Http-Loading.post">`Loading.post` 方法</a> 
*带loading效果的post请求*

| 参数     |        备注        |
| :------- | :----------------: |
| url      |    请求接口地址    |
| data     |      请求数据      |
| function | 请求成功的回调方法 |
| error    | 请求失败的回调方法 |
*使用方法*

```javascript
// 带loading的post请求
Eapp.http.loading.post('getdataurl',{ywid:11},function(data) {
  console.log(data);
},function(data) {
  alert(data.msg);
})

```
### <a id="Http-Loading.get">`Loading.get` 方法</a> 

*带loading效果的get请求*

| 参数     |        备注        |
| :------- | :----------------: |
| url      | 请求接口地址和数据 |
| function | 请求成功的回调方法 |
| error    | 请求失败的回调方法 |

*使用方法*

```javascript

// 带loading的get请求
Eapp.http.Loading.get(url,function(data) {
  console.log(data);
},function(data) {
  alert(data.msg);
})
```




## 三<a id="localData">Eapp.localData</a>
### 本地存储方法，可用于存储类似于token的东西


目前支持
| 方法   | 作用                   |
| :----- | :--------------------- |
| set    | 向本地存储数据元格     |
| get    | 获取已存储在本地的数据 |
| remove | 清除某一条本地数据     |
| clare  | 清除全部本地数据       |


###   <a id="localData-set">`Eapp.localData.set` 方法</a> 
*表示向本地存储数据*

*使用方法*

```JavaScript

/**
 * 第一种方法 
 * @param data 要存储的数据 Object 形如 {"key" : "value"}
 */
Eapp.localData.set(data);

/**
 * 第二种方法
 * @param key 要存储的数据的键
 * @param value 要存储的数据的值
 */
Eapp.localData.set(key, value);
```


###  <a id="localData-get">`Eapp.LocalData.get` 方法 </a>
*表示获取已存储在本地的数据*

*使用方法*

```javascript
/**
 * @param key 要取出数据的键值
 */

Eapp.localData.get(key);
```

###  <a id="localData-remove">`Eapp.localData.remove` 方法</a>
*表示清除某一条本地数据*

*使用方法*

```javascript
/**
 * @param key 要清除数据的键值
 */

Eapp.localData.remove(key);
```



### <a id="localData-clear">`Eapp.localData.clear` 方法</a>
*表示清除全部的本地数据*

*使用方法*

```javascript
Eapp.LocalData.clear();
```


## 四 <a id='window'>Eapp.window</a>
### 窗口操作，可用于打开关闭窗口
## 支持列表

### <a id='window-open'>`Eapp.window.open`方法</a>
*打开窗口*
```
open(uri,params)
```
*参数说明*

| 参数名 | 含义                           |
| :----- | :----------------------------- |
| uri    | 页面路径                       |
| params | 要传递的参数，格式为自定义对象 |
*用法*
```
Eapp.window.open('/home/personal',{id:1,title:个人中心});
```

### <a id='window-openAndCloseThis'>`Eapp.window.openAndCloseThis`方法</a>
*打开窗口并且关闭当前窗口*
```
openAndCloseThis()
```
*用法*
```
Eapp.window.openAndCloseThis()
```

### <a id='window-closeThis'>`Eapp.window.closeThis`方法</a>
*关闭当前窗口*
```
closeThis()
```
*用法*
```
Eapp.window.closeThis()
```
### <a id='window-replace'>`Eapp.window.replace`方法</a>
*替换当前窗口*
```
replace(uri,params)
```
*参数说明*
同open方法

*用法*
```
Eapp.window.replace('/home/personal',{id:1,title:个人中心})
```
### <a id='window-onshow'>`onshow`事件</a>
*页面显示*
```
// 当页面从被遮挡到再次显示的时候触发
onshow()
```
### <a id='window-onload'>`onload`事件</a>
*页面加载完成*
```
// 当页面加载完成的时候触发
onload()
```
### <a id='window-onclose'>`onclose`事件</a>
*关闭页面*
```
onclose(event)
```
*参数说明*
event有两个方法：

`event.close()`关闭窗口

`event.cancel()`取消关闭窗口
### <a id='window-params'>`params`属性</a>
*页面参数*
```
Eapp.window.params
// 获取从前面页面传过来的id和title
console.log(Eapp.window.params.id)
console.log(Eapp.window.params.title)
```


## 五<a id="event">Eapp.event</a>
### 事件发送和接收，主要用于多页面或者或组件之间的信息交互


目前支持
| 方法                    | 作用                 |
| :---------------------- | :------------------- |
| on(name, callback)      | 监听事件             |
| emit(name, data = null) | 发送事件（可带数据） |


###   <a id="event-on">`Eapp.event.on` 方法</a> 
*监听事件*

*使用方法*

```JavaScript

Eapp.event.on("login",function(user){
  console.log(user.token);
})

```


###  <a id="event-emit">`Eapp.event.emit` 方法 </a>
*触发事件*

```javascript
Eapp.event.emit("login",{token:"",uid:4})
```
 


## 六 <a id="user">Eapp.user</a>
### 用户模块，包含是否登录授权，及当前用户信息


目前支持
| 方法      | 作用                           |
| :-------- | :----------------------------- |
| isLogin   | 是否登录                       |
| info(key) | 用户信息，key为null 则返回所有 |


###   <a id="user-is-login">`Eapp.user.isLogin` 方法</a> 

*使用方法*

```JavaScript

 if(Eapp.user.isLogin())
 {

 }

```


###  <a id="user-info">`Eapp.user.info` 方法 </a>

```javascript
console.log(Eapp.user.info());
console.log(Eapp.user.info("token"));
```
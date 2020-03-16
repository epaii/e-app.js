# Eapp.js （e-app.js） 标准
> 文始集团前端项目（`web`,`web-app`,`h5`,`混合开发`,`微信小程序`）常用组件命名标准

## 标准研究会组员
[@apaii(会长)](https://github.com/epaii), [@宋阳](https://github.com/songyangphp) ,[@wutongshenyuan](https://github.com/wutongshenyuan)

## 标准内容列表
- [Eapp.localData 本地存储](#localData)
  - [set](#localData-set)
  - [get](#localData-get)
  - [remove](#localData-remove)
  - [clear](#localData-clear)



## 二 <a id="localData">Eapp.localData</a>
### 本地存储方法，可用于存储类似于token的东西


目前支持
| 方法   | 作用                   |
| :----- | :--------------------- |
| set    | 向本地存储数据元格     |
| get    | 获取已存储在本地的数据 |
| remove | 清除某一条本地数据     |
| clare  | 清除全部本地数据       |


###   <a id="localData-set">`Eapp.LocalData.set` 方法</a> 
*表示向本地存储数据*

*使用方法*

```JavaScript

/**
 * 第一种方法 
 * @param data 要存储的数据 Object 形如 {"key" : "value"}
 */
Eapp.LocalData.set(data);

/**
 * 第二种方法
 * @param key 要存储的数据的键
 * @param value 要存储的数据的值
 */
Eapp.LocalData.set(key, value);
```


###  <a id="localData-get">`Eapp.LocalData.get` 方法 </a>
*表示获取已存储在本地的数据*

*使用方法*

```javascript
/**
 * @param key 要取出数据的键值
 */

Eapp.LocalData.get(key);
```

###  <a id="localData-remove">`Eapp.LocalData.remove` 方法</a>
*表示清除某一条本地数据*

*使用方法*

```javascript
/**
 * @param key 要清除数据的键值
 */

Eapp.LocalData.remove(key);
```



### <a id="localData-clear">`Eapp.LocalData.clear` 方法</a>
*表示清除全部的本地数据*

*使用方法*

```javascript
Eapp.LocalData.clear();
```
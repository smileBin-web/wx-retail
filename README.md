# 新零售-微信小程序

## 代码分支管理
[gitflow-工作流][1]

## 样式

优先使用`less/variables.less`里定义的变量

## 尽量不要出现魔法字符串

请在`config/index.js`定义常量，然后在页面引用。

## 原生事件绑定

统一使用 `bind:eventName` 形式绑定事件。eg:

```js
<view bind:tap="functionName" />
```

## icon

icon组件使用的图片命名格式是：`icon-{name}-{state}`

## 图片

尽量使用网络图片，除非必须使用内置图片

## 服务

#### 服务命名
 
从功能上看，服务可分为：增、删、改、查，对应`http`方法为：`post`、`delete`、`put`、`get`。

所以命名服务时就按这四个方法开头：

- 新增服务：postXxx。比如新增地址: postAddress
- 删除服务：deleteXxx。比如删除䢑: deleteAddress
- 修改服务：putXxx。比如修改地址：putAddress
- 获取服务：getXxx。比如获取地址：getAddress; 获取地址列表:getAddressList

#### 服务使用

下面以获取配送时间接口为例：

```js

// 页面引用服务
import {
  getDeliveryTime,
  service,
} from '../../services/index';

//在页面page onLoad事件里调用服务

onLoad: function() {
  getDeliveryTime({test: 123})
    .then(function(data) {
      // data 为后台响应体中的 data
    })
    .catch(function(error) {
      /* error = {
        message, 错误信息
        from, 错误来源。API_ERROR_TYPE.API 后台接口返回的错误，比如校验不通过；API_ERROR_TYPE.HTTP 其他因素返回的错误, 比如断网等。
        data, 为后台响应体中的meta信息
      }
      /*
    })
}

```
调用方式：
`serviceName(params, options)`

`params` 可选， 为普通对象，用来存放接口参数。

`options` 可选，为普通对象，可配置的选项有：

参数 | 类型
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

参数 | 类型 | 必填 | 默认 | 说明 
---- | ----| ----| ----| ----| ----
| withLoadingTips | Boolean | 否 | true | 是否展示loading 状态
| successTips | Boolean或String | 否 | false | 请求成功时的提示行为。false: 不提示; true: 提示内容为后台接口返回的msg; String: 提示自定义的字符串
| failureTips | Boolean或String | 否 | true | 请求失败时的提示行为。false: 不提示; true: 提示内容为后台接口返回的msg; String: 提示自定义的字符串

## 微商城小程序视觉规范

小程序有它自己的设计思想 设计师可[参考微信小程序设计指南][3]设计界面

## 参考

[vscode-easy-wxless github 地址][2]

[1]:https://github.com/xfxb/fe-specification/blob/master/gitflow.md "gitflow-工作流"
[2]:https://github.com/yunfeizuo/vscode-easy-wxless "vscode-easy-wxless github 地址"
[3]:https://developers.weixin.qq.com/miniprogram/design/index.html?t=18092720 "微信小程序设计指南"


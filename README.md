## 1902面试题

## 一、html部分

1. 题目

   ```
   
   ```

   

## 二、javascript

## 三、jquery

## 四、Node

## 五、Vue.js

## 六、React 

### 1.React 15版本 vs React 16 版本

- 15 版本 虚拟dom 和 differ算法， 16版本是 filber算法
- props 和 state 定义方式不一样
- 生命周期不一样
- 类组件定义形式不同

## 七、混合开发 - 小程序

## 八、webpack

## 九、前端技术发展历史时间点

### 前端发展历史

html
  html [1990]----> html5 [2008.1.12]

css
  css 1.0 1996 
  css 2.0 1998
  css 3.0 2001

EcmaScript 
  1997年诞生
  2015  EcmaScript 2015
  2016  EcmaScript 2016          dart语言  vs  javascript

随着前端项目的逻辑越来越复杂和难以维护，那么前端这边引进了后端的架构思想（ MV* ）

M  Model      数据层
V  View       视图层
VM ViewModel  视图模型（ 业务逻辑  VM 是 由  P 改名得来的）
P  Presenter  提出者（ Controller 改名得来的 ）
C  Controller 控制器 ( 业务逻辑 )

Backbone.js  MVP    2010.10

Angular.js( 1.0 )   MVC    2010.10

Angular.ts ( 2.0 )  MVC -> MVVM 2016 目前已经更新到了 Angular8 ( 也属于angular2.0 版本 )

Vue 1.0   MVVVM  2014/07

Vue 2.0   MVVM   2016/09

React 2012 不太认可前端MVC这种架构思想， 你可以将React单纯看做是MVC中V

github统计量 （ 国际使用量 ）不代表大陆地区       单位是： K

angular.js   angular.ts       vue             React  

  59.6          49.1                  142              131

学习难度： Vue < React < Angular( 2.0 )

前端流行

  移动  web    &&  hybird app( 混合app )

  app
    1. native app ( 安卓  ios  java ME)
    2. webapp ( 应用在浏览器中的app )
    3. Hybird app ( 混合app ) 
       1. webapp 嵌入 第三方原生应用库（ 可以访问原生设备（手机） 的接口权限，比如：照相机 ）

### MV*的图示

MVC
  | C改名为P 
MVP
  | P更像是媒人了（ 连接 M  V 的桥梁）
MVVM
  | VM 是 由 p改名得来的  VM 和 V 的关系更加的亲密
  | "MVVM":双向数据绑定，View的变动，映射在 ViewModel，反之一样

注意：
    我们以上的这几个框架都是： 单向数据流（ 数据由 父级 流向 子级 ）
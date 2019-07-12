## 1902面试题

## 一、html - css 

1. 栅格化
2. flex
3. dpi
4. rem
5. 清除浮动的方式
6. 居中的方式
7. 浏览器  ie6 有哪些兼容 ？

## 二、javascript

1. 数组去重

   - es6   set   +   解构赋值
   - indexOf 
   - 利用对象的键值对唯一

2. 数组排序

   - 快速排序
   - 选择排序
   - 冒泡排序

3. 面向对象继承

   - 原型继承
   - 原型链继承
   - 混合继承
   - 类继承

4. this改变的方式

   - call
   - apply
   - bind

5. this指向问题

   - 由调用它的父级来定

6. new做了什么?

7. 什么是ajax?

8. get vs post

9. http vs https

10. 深拷贝 && 浅拷贝

    - 深拷贝： 值拷贝

    - 浅拷贝： 地址的拷贝， 只拷贝一层

    - 实现：

      - 深拷贝： 递归

        ```javascript
        function deepClone (sourceObj, targetObj) {
            let cloneObj = targetObj || {}
            if(!sourceObj || typeof sourceObj !== "object" || sourceObj.length === undefined){
                return sourceObj
            }
            if(sourceObj instanceof Array){
                cloneObj = sourceObj.concat()
            } else {
                for(let i in sourceObj){
                    if (typeof sourceObj[i] === 'object') {
                        cloneObj[i] = deepClone(sourceObj[i], {})
                    } else {
                        cloneObj[i] = sourceObj[i]
                    }
                }
            }
            return cloneObj
        }
        ```

    - 工具实现深拷贝

      - lodash
      - Immutable.js

## 三、jquery

1. 事件代理【 委托 】
2. 选择器 【 ~  +  ^ 】               nth-of-type   nth-child
3. jquery扩展
   - $.fn.extends

## 四、Node

1. 你使用过哪些包管理工具?
   - npm
   - cnpm 
   - yarn 
2. Node使用了什么模块化/
   - Common.js

## 五、Vue.js

1. Vue是什么？

   - Vue是一个js渐进式框架
   - Vue是一个MVVM框架
   - Vue 1.0   2014年
   - Vue 2.0   2016年

2. Vue几个指令

   - v-html
   - v-text
   - v-on
   - v-bind
   - v-if
   - v-for
   - v-model
   - v-show

3. Vue数据响应/ 深入响应式原理/双向数据绑定原理/跟踪监测

   - 数据修改，视图更新
   - 双向数据绑定原理使用了v-model指令
   - 数据劫持 && 事件的订阅发布
   - es5 Object.defineProperty

4. Vue非响应式情况

   - 数据的下标
   - 数据的length
   - 解决： Vue.set    this.$set           Object.asign 对象合并

5. Object.keys        Object.value

6. JSX

7. Prop验证

   ```javascript
   // 
   Vue.component('hello',{
       props: {
           num: Number,
           m: {
               validate ( value ) {
                   return value > 1000
               }
           }
       }
   })
   ```

8. 动态组件  +  is 属性

   ```javascript
   <component is = "A"></component>
   ```

9. 异步组件

10. 自定义指令、过滤器、插件【 Loading 】

11. cli

    - cli2
    - cli3      
    - vue.config.js

12. vue-router

    - 3.x版本
    - 动态路由、路由传参、路由接参
    - 编程式导航 【 const { push,replace } = this.$router__proto__ 】
      - push
      - replace
    - 路由钩子（ 路由监听 ）导航守卫
      - 全局导航守卫
      - 路由独享守卫
      - 组件内守卫
    - mode有几种
      - history
      - hash
      - abstrict

13. vuex

    - vuex是做什么的？
      - vuex是vue状态管理工具
      - vuex是一个集中式的存储仓库
    - vuex组成
      - actions  、 mutations  、 state
      - 后端数据交互
        - actions
      - 数据修改
        - mutations
      - 数据流程
        - state->component->actions->mutations->state
      - 辅助工具 【 解构 】
        - mapState  mapActions mapMutations mapGetters
        - mapState  mapGetters     往    computed 中
        - mapActions mapMutations 往   methods中

14. vue是否封装过组件？

    - Loading

    - banner

    - Vue.use()                 install

      ```javascript
      // 封装
      import tpl from './tpl.vue'
      const Loading = {
          install ( Vue ) {
              Vue.component( 'loading', {
                  template: tpl
              })
          }
      }
      export default Loading 
      
      
      // 使用
      
      import Loading from './Loading'
      Vue.use( Loading )
      ```

      

    15. Vue是否封装过自定义指令          
        - bind
        - inserted 
    16. methods vs computed vs watch
        - methods 事件处理程序
        - computed 
          - 类似全局变量使用
          - 有逻辑
        - watch
          - 大量数据
          - 异步操作
    17. vue组件通信
        - 父子组件通信： props
        - 子父组件通信： 自定义事件
        - 非父子组件通信： ref 、 bus
        - 多组件状态共享： vuex
        - 数据预载： vue-router



## 六、React 

1. React 15版本 vs React 16 版本

   - 15 版本 虚拟dom 和 differ算法， 16版本是 filber算法

   - props 和 state 定义方式不一样

     ```javascript
     // 15版本
     // 类组件
     const Hello = React.createClass({
         //属性
         getDefaultProps ( ) {
             return {
                 name: '1902'
             }
         }
         // 状态
         getInitalState () {
         	return {
             	msg: 'hello React'
         	}
     	}
     })
     
     // 16版本
     class Hello extends Component{
         //属性  外部传入  内部设置
         static defaultProps = {}
     	// state
     
     	// state = {} 
         constructor ( props ) { // props是父组件
     		super( props ) // 让子组件继承父组件的传入的props  this.props = props
             this.state = {}
         }
         
     }
     ```

     

   - 生命周期不一样

     ```javascript
     // 15.x
         //初始化
             getDefaultPorps
             getInitalState
             componentWillMount
             render
             componentDidMount
     
         //运行中
             componentWillReceiveProps
             shouldComponentUpdate
             componentWillUpdate
             componentDidUpdate
             
         //销毁
             componentWillUnmount
         
     // 16.x
     // 初始化
             constructor 
             sataic  getDeviredStateFromProps   // 未来版本
             componentWillMount
             render
             componentDidMount
     // 更新阶段
             componentWillReceiveProps
             shouldComponentUpdate
             componentWillUpdate
             getSnapshotBeforeUpdate()   // ---- 将来会使用
             componentDidUpdate
     // 销毁阶段
             componentWillUnmount
     // 错误处理阶段
             componentDidCatch
       
     ```

     

   - 类组件定义形式不同

     ```javascript
     // 15
     React.createClass({})
     // 16
     class Hello extends Component{}
     ```

     

2. React组件通信

   - 父子组件通信： 将一个数据绑定在子组件身上
   - 子父组件通信： 父组件绑定一个方法给子组件，子组件调用这个方法
   - 非父子组件通信： ref
   - 跨组件通信： Context
   - 多组件状态共享： Flux  Redux  mobx

3. React - setState

   - 有两个参数
     - 第一个可以是对象，也可以是函数，但是函数必须要有返回值，
     - 第二个参数是一个回调函数 
   - setState 不能在componentWillUpdate componentDidUpdate中使用
     - 会造成死循环

4. 高阶组件

   - 共用方法、属性复用
   - 外层组价完成一些任务，里层组件直接使用任务结果

5. React-Hooks

   - 函数式组件中使用
   - 使用过哪些 Hooks   【 useState useEffect 】

6. React路由懒加载

   - webpack注释语法

     ```
     const Foo = () => import(/* webpackChunkName: "group-foo" */ './Foo.js')
     ```

   - Switch 组件

7. React组件封装

   - Banner
   - 返回顶部
   - 弹出框

8. React高性能的原因

   - Virtual DOM 
     - 减少了真实dom操作

9. React性能优化的方案

   - 无状态组件
   - shouldComponentUpdate
   - 高阶组件
   - 组件通信： redux

10. 组件的生命周期

    - 数据请求：  componentDidMount
    - dom操作【 第三方库实例化 】： componentDidMount    componentDidUpdate

11. React版本问题

    - React 16.x      React 16.8.6
    - React-router     4.4【 5 】  答： 4版本

12. React-router  3   vs  React 4

    - 3的版本是传统的路由思想： 路由表 react-router
    - 4的版本一切皆组件 react-router-dom

13. React-router

    - 路由如何监听： withRouter    App      componentWillReceiveProps   componentDidMount

    - Switch 

    - exact 路径完全匹配

    - 动态路由 - 路由传参 - 路由接参

    - Route / Link / NavLink 

    - mode有几种？ HashRouter     BrowserRouter   

    - 场景性问题： 头部、底部的监听

      - 编程式导航 【  const { push , replace } = this.props.history】

        - push 【 历史记录会存放 】
        - replace 【 历史记录不会存放 】

        

      - 跳转

        - go
        - back

14. 状态管理

    - redux
      - 组成部分
        - store  、 actionCreators 、 reducer  
      - redux数据分片（ reducer 划分 ）  **react-redux**
        - combineReducers     bindActionCreators 
      - redux中数据修改
        - reducer
      - redux数据请求
        - actionCreator中书写后端数据交互
        - redux-thunk 
        - 在actionCreators中返回 函数，函数参数 是 dispatch
      - redux使用过哪些中间件
        - redux-thunk   redux-log   redux-promise  redux-saga 
    - mobx
      - es6装饰器 
      - 组成部分
        - @actions  @computed  @overserable  
      - @inject   注入
      - @oberserver

## 七、混合开发 - 小程序

1. 小程序有哪些类型文件
   - json
   - wxml
   - wxss
   - js
2. 是否使用过小程序框架
   - mpvue
   - taro
3. setData 修改数据
4. 是否封装过小程序请求？
   - 只能使用 Promise
5. 小程序大小是 2M

## 八、webpack - gulp

1. 是否使用webpack搭建过项目？
2. webpack做过哪些配置？
   - 入口
   - 出口
   - 转换器： css-loader vue-loader jsx-loader sass-loader style-loader
   - 插件： css抽离  html产出   图片打包 静态资源拷贝
   - 服务器配置
   - 错误资源定制
3. 使用过哪些前端自动化工具【 工程化工具 】
   - webpack
   - gulp
   - rollup
   - parcel
   - FIS
4. webpack版本
   - webpack 1.0    AMD
   - webpack 2.0  引入ES Modlue
   - webpack 3.0 - 4.0    ES模块化支持完整， webpack添加了注释语法



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

## 十、版本控制管理工具： git / svn

1. git命令你知道哪些？
   - git add .
   - git commit -m 
   - git merge
   - git checkout 分支名称
   - git branch 分支名称
   - git push 
   - git pull 更新 
2. git 冲突
   - 解决： 手动合并之后  在上传
   - 避免： 
     - git pull 先更新  ， 在上传



## 十一、互联网项目团队开发流程

<https://blog.csdn.net/qwfys200/article/details/82811057>



## 十二、前端有几个环境

开发环境

生产环境

测试环境

预上线环境

上线环境

## 十三、前端模块化

1. AMD [ define ]         require.js
2. CMD  [ define ]        sea.js
3. Common.js
4. es模块化
   - export        批量导出
   - export default   单一导出

## 十四、前端的异步流程

1. 传统
   - 回调函数
   - 事件
2. 流行
   - Promise
   - generator函数
   - async函数 [ 底层  generator 函数 ]
   - nextTick
   - async.js第三方库

## 十五、前端跨域方式

1. 前端跨域
   1. jsonp
   2. 反向代理 
      - http-proxy-middleware
      - nginx
2. 后端跨域
   - 单一设置请求头
   - 统一设置请求头
   - 使用cors中间件跨域

## 十六、浏览器兼容  vs  移动端兼容

1. 浏览器兼容： <https://blog.csdn.net/lmb55/article/details/50950901>

2. 移动端兼容： 

   - 1px兼容

   - 安卓浏览器看背景图片，有些设备会模糊，原因是手机的分辨率太小

   - 防止手机中页面放大或缩小： 在meta中设置viewport user-scalable = no

   - 上下拉滚动条卡顿： overflow-scrolling: touch;

   -  禁止复制选中文本： user-select: none;

   - 长时间按住页面出现闪退：-webkit-touch-callout: none;

   - 动画定义3D硬件加速： transform: translate 3d(0,0,0);

   -  formate-detection 启动或禁止自动识别页面中的电话号码，content = "yes/no"

   - a标签添加tel是拨号功能

   - 安卓手机的圆角失效： background-clip: padding-box;

   - 手机端300ms延迟： fastclick

   - 横平时字体加粗不一致： text-size-adjust: 100%;

     ```html
     <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
     <meta name="apple-mobile-web-app-capable" content="yes" />
     <meta name="apple-mobile-web-app-status-bar-style" content="black" />
     <meta name="format-detection"content="telephone=no, email=no" />
     <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
     <meta name="apple-mobile-web-app-capable" content="yes" /><!-- 删除苹果默认的工具栏和菜单栏 -->
     <meta name="apple-mobile-web-app-status-bar-style" content="black" /><!-- 设置苹果工具栏颜色 -->
     <meta name="format-detection" content="telphone=no, email=no" /><!-- 忽略页面中的数字识别为电话，忽略email识别 -->
     <!-- 启用360浏览器的极速模式(webkit) -->
     <meta name="renderer" content="webkit">
     <!-- 避免IE使用兼容模式 -->
     <meta http-equiv="X-UA-Compatible" content="IE=edge">
     <!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
     <meta name="HandheldFriendly" content="true">
     <!-- 微软的老式浏览器 -->
     <meta name="MobileOptimized" content="320">
     <!-- uc强制竖屏 -->
     <meta name="screen-orientation" content="portrait">
     <!-- QQ强制竖屏 -->
     <meta name="x5-orientation" content="portrait">
     <!-- UC强制全屏 -->
     <meta name="full-screen" content="yes">
     <!-- QQ强制全屏 -->
     <meta name="x5-fullscreen" content="true">
     <!-- UC应用模式 -->
     <meta name="browsermode" content="application">
     <!-- QQ应用模式 -->
     <meta name="x5-page-mode" content="app">
     <!-- windows phone 点击无高光 -->
     <meta name="msapplication-tap-highlight" content="no">
     <!-- 适应移动端end -->
     --------------------- 
     作者：阿Q虾米 
     来源：CSDN 
     原文：https://blog.csdn.net/yc123h/article/details/51356143 
     版权声明：本文为博主原创文章，转载请附上博文链接！
     ```

     

     h5移动端  ios/安卓兼容： <https://segmentfault.com/a/1190000015131445>

     


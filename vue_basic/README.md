# 第1章:Vue 核心

## 课程简介

1. vue 基础
2. vue-cli
3. vue-router
4. vuex
5. element-ui
6. vue3

## Vue简介

### Vue是什么？

一套用于**构建用户界面**的**渐进式**JavaScript框架

数据----vue--->界面

渐进式：从一个**轻量小巧的核心库**逐渐递进到**复杂的核心库**。Vue可以自底向上逐层的应用。

​	简单应用：只需一个轻量小巧的核心库

​	复杂应用：可以引入各式各样的Vue插件

### 谁开发的？

作者：尤雨溪

- 2013年 受到Angular框架的启发，尤雨溪开发出一款轻量级框架——Seed。同年12月，Seed更名为Vue，版本号0.6.0

- 2014年 Vue正式对外发布，版本号0.8.0

  Taylor otwell在Twitter上发表动态，说自己正在学习Vue.js

- 2015年 10月27日，正式发布Vue1.0.0 Evangelion（新世纪福音战士）

- 3016年 10月1日，正式发布Vue2.0.0 Ghost in the Shell（攻壳机动队）

- 2020年 9月18日，正式发布Vue3.0.0 One Piece（海贼王）

### Vue的特点

1. 采用**组件化**模式，提高代码复用率、且让代码更好维护

   ![component](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/component.png)

2. **声明式**编码，让编码人员无需这届操作DOM，提高开发效率。

   

   ![data-to-dom](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/data-to-dom.png)

   （命令式编码：写一步动一步，一步一步命令着做。声明式编码：写个声明就可以进行）

   ![commands-directives](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/commands-directives.png)

3. 使用**虚拟DOM**+优秀的**Diff算法**，尽量复用DOM节点。

   ![](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/javascript-realize.png)

   （diff:对比）

   ![vue-realize](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/vue-realize.png)

### 与其它 JS 框架的关联

1. 借鉴 Angular 的**模板**和**数据绑定**技术
2. 借鉴 React 的**组件化**和**虚拟DOM** 技术

### 前置JavaScript知识

- ES6语法规范
- ES6模块化
- 包管理器
- 原型、原型链
- 数组常用方法
- axios
- promise
- ......

### Vue 周边库

1. vue-cli: vue 脚手架
2. vue-resource
3. axios
4. vue-router: 路由
5. vuex: 状态管理
6. element-ui: 基于 vue 的 UI 组件库(PC 端)
7. ......

### Vue官网使用指南

1. 学习-->教程（重要）

2. 学习-->API（重要）

   vue字典，是用来查的，不是一个个看的

3. 学习-->风格指南

   必要的、强烈推荐、推荐、谨慎使用

4. 学习-->示例

5. 学习-->Cookbook

   vue编码技巧：

   1. js
   2. Vue

   区别于指南：指南教你编码好坏、Cookbook教你编码技巧

6. 生态系统-->工具

   1. Devtools
   2. Vue CLI
   3. Vue Loader

7. 生态系统-->核心插件

   1. Vue Router
   2. Vuex
   3. Vue服务器渲染

8. 资源列表-->Awesome Vue、资源列表-->浏览和Vue相关的包

   （awesome:了不起的）

   https://awesomejs.dev/for/vue/

   https://awesomejs.dev/for/react/

   https://awesomejs.dev/

### 搭建vue开发环境

1. 引入开发版的Vue
   1. 在console中验证Vue是否被引入
   2. 运行有两个提示：
      1. 安装vue-devtools
      2. 提示vue用的版本是开发版，不是发布版
2. 安装vue-devtools

3. 关闭开发版提示

​        如何关闭上述提示？

​          1.  AP-->全局配置

​          2.  打印vue.config可看到全局配置属性

​          3.  关闭vue.config.productionTip=false

 vue.js可看到警告提示[vue warn]的源码（对开发中报的vue的原因查找很有作用）

## 初识 Vue

<img src="/Users/liyang/Library/Application Support/typora-user-images/image-20211002132749111.png" alt="image-20211002132749111" style="zoom:100%;" />

## 1.3. 模板语法 

### 1.3.1. 效果

![image-20211002132814902](/Users/liyang/Library/Application Support/typora-user-images/image-20211002132814902.png)

### 1.3.2. 模板的理解

html 中包含了一些 JS 语法代码，语法分为两种，分别为:

1. 插值语法(双大括号表达式)
2. 指令(以 v-开头)

### 1.3.3. 插值语法

1. 功能: 用于解析标签体内容
2. 语法: {{xxx}} ，xxxx 会作为 js 表达式解析

### 1.3.4. 指令语法

1. 功能: 解析标签属性、解析标签体内容、绑定事件
2. 举例:v-bind:href = 'xxxx' ，xxxx 会作为 js 表达式被解析
3. 说明:Vue 中有有很多的指令，此处只是用 v-bind 举个例子

## 1.4. 数据绑定 

### 1.4.1. 效果

![image-20211002132916130](/Users/liyang/Library/Application Support/typora-user-images/image-20211002132916130.png)

### 1.4.2. 单向数据绑定

1. 语法:`v-bind:href ="xxx"` 或简写为 :href 
2. 特点:数据只能从 data 流向页面

### 1.4.3. 双向数据绑定

1. 语法:`v-mode:value="xxx"` 或简写为 `v-model="xxx"`
2. 特点:数据不仅能从 data 流向页面，还能从页面流向 data

## 1.5. MVVM 模型

1. M:模型(Model) :对应 data 中的数据
2. V:视图(View) :模板
3. VM:视图模型(ViewModel) : Vue 实例对象

![image-20211002133110122](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133110122.png)

## 1.6. 事件处理 

### 1.6.1. 效果

![image-20211002133155911](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133155911.png)

### 1.6.2. 绑定监听

1. v-on:xxx="fun"
2. @xxx="fun"
3. @xxx="fun(参数)"
4. 默认事件形参: event 5. 隐含属性对象: $event

### 1.6.3. 事件修饰符

1. .prevent : 阻止事件的默认行为 event.preventDefault() 
2. 2. .stop : 停止事件冒泡 event.stopPropagation()

### 1.6.4. 按键修饰符

1. keycode : 操作的是某个 keycode 值的键 
2. .keyName : 操作的某个按键名的键(少部分)

## 1.7. 计算属性与监视 

## 1.7.1. 效果

![image-20211002133317228](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133317228.png)

### 1.7.2. 计算属性-computed

1. 要显示的数据不存在，要通过计算得来。
2. 在 computed 对象中定义计算属性。
3. 在页面中使用{{方法名}}来显示计算的结果。

### 1.7.3. 监视属性-watch

![image-20211002133406347](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133406347.png)

1. 通过通过 vm 对象的$watch()或 watch 配置来监视指定的属性
2. 当属性变化时, 回调函数自动调用, 在函数内部进行计算

## 1.8. class 与 style 绑定 

### 1.8.1. 理解

1. 在应用界面中, 某个(些)元素的样式是变化的
2. class/style 绑定就是专门用来实现动态样式效果的技术

### 1.8.2. class 绑定

1. :class='xxx'
2. 表达式是字符串: 'classA'
3. 表达式是对象: {classA:isA, classB: isB}
4. 表达式是数组: ['classA', 'classB']

### 1.8.3. style 绑定

1. :style="{ color: activeColor, fontSize: fontSize + 'px' }"
2. 其中 activeColor/fontSize 是 data 属性

## 1.9. 条件渲染 

### 1.9.1. 条件渲染指令

1. v-if 与 v-else 
2. v-show

### 1.9.2. 比较 v-if 与 v-show

1. 如果需要频繁切换 v-show 较好
2. 当条件不成立时, v-if 的所有子节点不会解析(项目中使用)

## 1.10. 列表渲染 

### 1.10.1. 效果

![image-20211002133526678](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133526678.png)

![image-20211002133549860](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133549860.png)

![image-20211002133602943](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133602943.png)

### 1.10.2. 列表显示指令

遍历数组: v-for / index 

遍历对象: v-for / key

## 1.11. 收集表单数据

![image-20211002133705834](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133705834.png)

## 1.12. 过滤器 

### 1.12.1. 效果

![image-20211002133718943](/Users/liyang/Library/Application Support/typora-user-images/image-20211002133718943.png)

### 1.12.2. 理解过滤器

1. 功能: 对要显示的数据进行特定格式化后再显示
2. 注意: 并没有改变原本的数据, 是产生新的对应的数据

## 1.13. 内置指令与自定义指令 

### 1.13.1. 常用内置指令

1. v-text : 更新元素的 textContent
2. v-html : 更新元素的 innerHTML
3. v-if : 如果为 true, 当前标签才会输出到页面
4. v-else: 如果为 false, 当前标签才会输出到页面
5. v-show : 通过控制 display 样式来控制显示/隐藏
6. v-for : 遍历数组/对象
7. v-on : 绑定事件监听, 一般简写为@
8. v-bind : 绑定解析表达式, 可以省略 v-bind
9. v-model : 双向数据绑定
10. v-cloak : 防止闪现, 与 css 配合: [v-cloak] { display: none }

### 1.13.2. 自定义指令 

**1. 注册全局指令**

```vue
Vue.directive('my-directive', function(el, binding){ el.innerHTML = binding.value.toupperCase()
})
```



**2. 注册局部指令**

```vue
directives : { 'my-directive' : {
bind (el, binding) {
 el.innerHTML = binding.value.toupperCase()
} }
}
```


  1) 使用指令

v-my-directive='xxx'

## 1.14. Vue 实例生命周期 

### 1.14.1. 效果

![image-20211002134159075](/Users/liyang/Library/Application Support/typora-user-images/image-20211002134159075.png)

### 1.14.2. 生命周期流程图

![image-20211002134233560](/Users/liyang/Library/Application Support/typora-user-images/image-20211002134233560.png)

### 1.14.3. vue 生命周期分析

1) 初始化显示

\* beforeCreate() 
\* created()
 \* beforeMount() 
\* mounted()

2) 更新状态: this.xxx = value

\* beforeUpdate() 

\* updated()

3) 销毁 vue 实例: vm.$destory()

\* beforeDestory() 

\* destoryed()

### 1.14.4. 常用的生命周期方法

1. mounted(): 发送 ajax 请求, 启动定时器等异步任务
2. beforeDestory(): 做收尾工作, 如: 清除定时器


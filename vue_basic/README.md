# 笔记

## 课程简介

1. vue 基础
2. vue-cli
3. vue-router
4. vuex
5. element-ui
6. vue3

## Vue简介

### 1.Vue是什么？

一套用于**构建用户界面**的**渐进式**JavaScript框架

数据----vue--->界面

渐进式：从一个**轻量小巧的核心库**逐渐递进到**复杂的核心库**。Vue可以自底向上逐层的应用。

​	简单应用：只需一个轻量小巧的核心库

​	复杂应用：可以引入各式各样的Vue插件

### 2.谁开发的？

作者：尤雨溪

- 2013年 受到Angular框架的启发，尤雨溪开发出一款轻量级框架——Seed。同年12月，Seed更名为Vue，版本号0.6.0

- 2014年 Vue正式对外发布，版本号0.8.0

  Taylor otwell在Twitter上发表动态，说自己正在学习Vue.js

- 2015年 10月27日，正式发布Vue1.0.0 Evangelion（新世纪福音战士）

- 3016年 10月1日，正式发布Vue2.0.0 Ghost in the Shell（攻壳机动队）

- 2020年 9月18日，正式发布Vue3.0.0 One Piece（海贼王）

### 3.Vue的特点

1. 采用**组件化**模式，提高代码复用率、且让代码更好维护

   ![component](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/imgs/component.png)

2. **声明式**编码，让编码人员无需这届操作DOM，提高开发效率。

   

   ![data-to-dom](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/imgs/data-to-dom.png)

   （命令式编码：写一步动一步，一步一步命令着做。声明式编码：写个声明就可以进行）

   ![commands-directives](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/imgs/commands-directives.png)

3. 使用**虚拟DOM**+优秀的**Diff算法**，尽量复用DOM节点。

   （diff:对比）

   ![](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/imgs/javascript-realize.png)

   ![](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/imgs/vue-realize.png)

4.学习Vue之前要掌握的JavaScript基础知识？

- ES6语法规范
- ES6模块化
- 包管理器
- 原型、原型链
- 数组常用方法
- axios
- promise
- ......

## Vue官网使用指南

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


 

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

## 初识 Vue

### 效果

![hello](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/hello.png)

### 搭建vue开发环境

1. 引入开发版的Vue

   在console中验证Vue是否被引入

2. 运行有两个提示：

   1. 安装vue-devtools
   2. 提示vue用的版本是开发版，不是发布版

### 关闭生成生产提示

1. API-->**全局配置**

2. 打印vue.config可看到全局配置属性

3. 关闭`vue.config.productionTip = false`

    vue.js可看到警告提示[vue warn]的源码（对开发中报的vue的原因查找很有作用）

![vuejs](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/vuejs.png)

### Hello案例

1. 引入开发版的Vue

   ```vue
   <script type="text/javascript" src="../js/vue.js"></script>
   ```

2. 准备好一个容器

   ```vue
   <div id="demo"></div>
   ```

   **报错**：加载静态资源错误，页签图标找不到[^1]

   **报错**：属性或方法age未定义[^2]

2. **创建Vue实例，建立和dom联系**

   ```javascript
   const x = new Vue({
     el: "#demo", //el用于指定当前Vue实例为哪个容器服务，值通常为css选择器字符串。
     data: {
       //data中用于存储数据，数据供el所指定的容器去使用，值我们暂时先写成一个对象。
       name: "atguigu",
       address: "北京",
     },
   });
   ```

   1. 学习`mvvm`后才把x学位`vm`
   2. 参数是`配置对象`
   3. el是css的id选择器，找到容器。(document.getElementById('root'))

   **报错**：Vue是构造函数，需要关键词new[^3]

3. 和dom建立起联系后，进行**数据绑定**

   ```vue
   <div id="demo">
     <h1>Hello，{{name.toUpperCase()}}，{{address}} {{age}}</h1>
   </div>
   ```

   1. data用于存储可变数据，使用对象。（**后面再使用其他东西**）
   2. dom中使用插值语法:{{}}。（和对象没任何关系）

### 总结

1. 想让Vue工作，就必须**创建一个Vue实例**，且要**传入一个配置对象**；

2. root容器里的代码**依然符合html规范**，只不过混入了一些特殊的Vue语法；

3. root容器里的代码被称为**【Vue模板】**；

4. **Vue实例和容器是一一对应**的；（一个vue实例不能同时接管多个容器）

5. 真实开发中**只有一个Vue实例**，并且会配合着组件一起使用；（data可以拆成多个data（组件））

6. {{xxx}}中的xxx要写**js表达式**，且xxx可以自动读取到data中的所有属性；（js表达式是特殊的js语句，**特殊在会产生一个值**）

   注意区分：js表达式 和 js代码(语句)
   1. 表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方：
      1. a
      2. a+b
      3. demo(1)
      4. x === y ? 'a' : 'b'
   2. js代码(语句)
      1. if(){}
      2. for(){}

7. 一旦data中的数据发生改变，那么页面中用到该数据的地方也会**自动更新**；

## 模板语法 

### 效果



![template-syntax](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/template-syntax.png)

### 两大分类：

1. **插值语法**：

   功能：用于解析标签体内容。

   写法：`{{xxx}}`，xxx是js表达式，且可以直接读取到data中的所有属性。

   ```vue
   <h3>你好，{{name}}</h3>
   ```

2. **指令语法**：

   功能：用于解析标签（包括：标签属性、标签体内容、绑定事件.....）。

   举例：`v-bind:href="xxx"` 或  简写为 `:href="xxx"`，xxx同样要写js表达，且可以直接读取到data中的所有属性。

   备注：Vue中**有很多的指令，且形式都是：`v-????`**，此处我们只是拿v-bind举个例子。

   ```vue
   <a v-bind:href="school.url.toUpperCase()" x="hello">点我去{{school.name}}学习1</a>
   <!-- <a href="{{school.url}}" x="hello">点我去{{school.name}}学习2</a> -->
   <!-- <a :href="{{school.url}}" x="hello">点我去{{school.name}}学习2</a> -->
   <a :href="school.url" x="hello">点我去{{school.name}}学习2</a>
   ```

   **报错**：编译模板出错：属性内插值语法被移除[^4]

   **报错**：编译模板出错：无效表达式，意外标记 '{'[^5]

### 简写

1. 普通写法

   `v-bind:href="xxx"`

   `v-????:href="xxx"`

2. 简写

   `:href="xxx"`（v-bind简写的是**指令**）

   `v-????="xxx"`（v-????简写的是**绑定属性**，每个指令都有默认的绑定属性）

## 数据绑定 

### 效果

![image-20211002132916130](/Users/liyang/Library/Application Support/typora-user-images/image-20211002132916130.png)

### 两种方式：

1. 单向绑定(`v-bind`)：数据只能从data流向页面。

2. 双向绑定(`v-model`)：数据不仅能从data流向页面，还可以从页面流向data。

### 简写

1. 普通写法

   ```vue
   单向数据绑定：<input type="text" v-bind:value="name"><br/>
   双向数据绑定：<input type="text" v-model:value="name"><br/>
   ```

2. 简写

   ```vue
   单向数据绑定：<input type="text" :value="name" /><br />
   双向数据绑定：<input type="text" v-model="name" /><br />
   <!-- <h2 v-model:x="name">你好啊</h2> -->
   ```

   备注：

   1. 双向绑定一般都应用在**表单类元素**上（如：input、select等）
   2. **`v-model:value` 可以简写为 `v-model`**，因为v-model默认收集的就是value值。
   3. **报错**：编译模板出错：v-model才能实现双向绑定，v-model只能应用在表单类元素（输入类元素）上[^6]

## el与data的两种写法

为穿插知识点，应该在**组件**中去讲

### el的2种写法：

1. new Vue时候**配置el属性**。
2. 先创建Vue实例，随后再通过`vm.$mount('#root')`指定el的值。、
         1. 把容器中的模板交给实例进行解析
         2. 解析之后把解析完的内容放回容器（挂载）

### 挂载注意点

```js
const v = new Vue({
  //el:'#root', //第一种写法
  data:{
  	name:'尚硅谷'
  }
})
console.log(v)
v.$mount('#root') //第二种写法
```

1. $mount：山、**挂载**
2. \$mount在构造函数（new Vue）中才能找到，打印v并不能直接看到$mount，而得从**原型**中找

### data的2种写法：

1. 对象式

   ```js
   data:{
     name:'尚硅谷'
   }
   ```

2. 函数式

   ```js
   data() {
     console.log("@@@", this); //此处的this是Vue实例对象
     return {
     	name: "尚硅谷",
     };
   }
   ```

### 函数式data注意点

1. 如何选择：目前哪种写法都可以，以后学习到**组件时，data必须使用函数式**，否则会报错。
   1. data在组件中必须使用函数式，**否则会报错**。
   2. data函数式**必须返回对象**
   3. data函数式**是给Vue调用的，所以在date函数式中打印this是Vue对象**[(VM（数据代理）)](#VM（数据代理）)
   4. data()是**`data:function()`的简写**

   ```js
   // 普通写法
   data:function() {
     return {
     	name: "尚硅谷",
     };
   },
   // 简写
   data() {
     return {
     	name: "尚硅谷",
     };
   },
   ```

2. 一个重要的原则：

   由**Vue管理的函数，一定不要写箭头函数**，一旦写了箭头函数，this就不再是Vue实例了。（而是Window）

   ​	data()是学习的第一个Vue管理的函数
   
   ```js
   // 普通函数
   data:function() {
     console.log("@@@", this); //此处的this是Vue实例对象
     return {
     	name: "尚硅谷",
     };
   },
   // 箭头函数
   data:()=> {
     console.log("@@@", this); //此处的this是Window实例对象
     return {
     	name: "尚硅谷",
     };
   },
   ```
   
   

## MVVM 模型

[vue官网解释](https://cn.vuejs.org/v2/guide/instance.html)：虽然没有完全遵循 [MVVM 模型](https://zh.wikipedia.org/wiki/MVVM)，但是 Vue 的设计也受到了它的启发。因此在文档中经常会使用 `vm` (`ViewModel` 的**缩写)** 这个变量名表示 `Vue实例`。

### 基于MVVM启发的vue设计：

1. M：模型(Model) ：**data中的数据**（`Plain JavaScript Object`：一般js对象）
2. V：视图(View) ：**模板代码**（`DOM`）
3. VM：视图模型(ViewModel)：**Vue实例**（**Vue**：`DOM Listeners`、`Data Bindings`）

直意：`Vue实例`为`data`与`DOM`做了个桥梁、纽带

![MVVM](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/MVVM.png)

### 使用vm代表Vue实例：

在文档中经常会使用 vm (ViewModel 的缩写) 这个变量名表示 `Vue实例`（`vm`就是**数据代理**）

**由于MVVM的思想，所以以后都用vm命名Vue实例**

```js
const vm = new Vue({
  el: "#root",
  data: {
    name: "尚硅谷",
    address: "北京",
  },
});
console.log(vm);
```

### 模板中都能有什么？

```vue
<h1>学校名称：{{name}}</h1>
<h1>学校地址：{{address}}</h1>
<!-- <h1>测试一下1：{{1+1}}</h1> -->
<!-- <h1>测试一下2：{{$options}}</h1> -->
<!-- 初始化选项：https://cn.vuejs.org/v2/api/#vm-options -->
<!-- 以下在原型中 -->
<!-- <h1>测试一下3：{{$emit}}</h1> -->
<!-- 触发当前实例上的事件:https://cn.vuejs.org/v2/api/index.html#vm-emit -->
<!-- <h1>测试一下4：{{_c}}</h1> -->
```

观察发现：

1. data中所有的属性，最后都出现在了vm身上。

2. **vm身上所有的属性** 及 **Vue原型上所有属性**，在Vue模板中都可以直接使用。

   1. **$options**
   2. **$emit（原型中）**
   3. **$mount（原型中）**

   ![proto](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/proto.png)

3. **所有带$都是vue给程序员使用的**属性或对象

![image-20211012214536494](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/$.png)

## 数据代理

### 回顾`Object.defineproperty`方法：

定义：

给一个**对象添加/定义属性**使用（`define`(定义)`property`(属性)）

基本用法：

```js
let person = {
	name:'张三',
	sex:'男',
}
Object.defineProperty(person,'age',{
	value:18
})
```

**淡色**代表不可被枚举

![defineproperty](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/defineproperty.png)

配置项：

1. 基本配置项

   1. `enumerable`

      控制属性是否可以枚举，默认值是false

      ```js
      let person = {
      	name:'张三',
      	sex:'男',
      }
      Object.defineProperty(person,'age',{
      	value:18,
        enumerable: false //控制属性是否可以枚举，默认值是false
      })
      // 不可枚举
      console.log(Object.keys(person))
      for (const key in person) {
        console.log("@", person[key]);
      }
      ```

      ![enumerable](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/enumerable.png)

   2. `writable`

      控制属性是否可以被修改，默认值是false

      ```js
      let person = {
      	name:'张三',
      	sex:'男',
      }
      Object.defineProperty(person,'age',{
      	value:18,
        writable: false //控制属性是否可以被修改，默认值是false
      })
      // 不可修改
      person.age = 19;
      console.log(person);
      ```

      ![writable](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/writable.png)

   3. `configurable`

      控制属性是否可以被删除，默认值是false

      ```js
      let person = {
      	name:'张三',
      	sex:'男',
      }
      Object.defineProperty(person,'age',{
      	value:18,
        configurable: false, //控制属性是否可以被删除，默认值是false
      })
            // 不可被删除
            delete person.age;
            console.log(person);
      ```

      ![image-20211101165359303](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/configurable.png)

2. 高级配置项

   ```js
   let number = 18;
   let person = {
     name: "张三",
     sex: "男",
   };
   Object.defineProperty(person, "age", {
     // 当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
     get() {
       return number;
     },
     //当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值
     set(value) {
       number = value;
     },
   });
   console.log(person);
   ```

   ​	![getter-setter](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/getter-setter.png)

   1. `getter`

      当有人读取person的age属性时，`get函数`(`getter`)就会被调用，且返回值就是age的值

      1. Invoke property getter（调属性getter） （Invoke映射，getter即get()配置项（get属性名+function函数））
      2. 每次访问age属性都会触发get

      ```js
      let number = 18;
      let person = {
        name: "张三",
        sex: "男",
      };
      Object.defineProperty(person, "age", {
        // get()是get:function aaa()的简写，aaa是gat的自定义名称，可在控制台看到
        get() {
          console.log("有人读取age属性了");
          return number;
        },
      });
      console.log(person);
      ```

      ![getter](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/getter.png)![getter-on](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/getter-on.png)

   2. `setter`

      当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值

      ``` js
      let number = 18;
      let person = {
        name: "张三",
        sex: "男",
      };
      Object.defineProperty(person, "age", {
        // 当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
        get() {
          console.log("有人读取age属性了");
          return number;
        },
        //当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值
        set(value) {
          console.log("有人修改了age属性，且值是", value);
          number = value;
        },
      });
      console.log(person);
      ```

      number和person明明是两个对象，但是借住`defineProperty`使`number`与`person.age`产生关联

      ![setter-on](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/setter-on.png)

### Vue中的应用：

1. **数据代理**
2. **数据劫持**
3. **计算属性**

### 何为数据代理

数据代理：通过一个对象**代理**另一个对象中**属性的操作（读/写）**

```js
let obj = { x: 100 };
let obj2 = { y: 200 };

Object.defineProperty(obj2, "x", {
  get() {
    return obj.x;
  },
  set(value) {
    obj.x = value;
  },
});
```

通过修改代理对象(obj2)去操作对象(obj1)

![data-proxy](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/data-proxy.png)

### Vue中的数据代理：

1.先看效果，invoke property getter：用属性getter

访问vm上的address时getter工作，修改是setter工作，他们都有对应的set()、get()，读取和修改改的是date.address

![image-20211111125340105](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111125340105.png)

验证vm.address通过getter、setter读取和修改data.address  

![image-20211111125304094](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111125304094.png) 验证getter，修改data中的name![image-20211111125453771](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111125453771.png)

验证setter， 拿不到配置项的data，vm一定会存到自己的属性中(因为不存怎么拿)，vm._data = data

![image-20211111130024029](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111130024029.png)

![image-20211111130213618](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111130213618.png)

![image-20211111130325004](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111130325004.png)

2.示意图：

第一个箭头：存数据。并没有做数据代理，也能实现功能 ，此时通过_data.的方式也能在模板中使用

第二个箭头：数据代理。目的：让编码更方便

![diagram-data-proxy](https://cdn.jsdelivr.net/gh/coalyer/image-store/blog/vue_basic/diagram-data-proxy.png)

![image-20211111130526419](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111130526419.png)

3.总结：

1. 通过vm对象来代理data对象中属性的操作（读/写）

2. Vue中数据代理的好处：

   更加方便的操作data中的数据

3. 基本原理：

   通过Object.defineProperty()把data对象中所有属性添加到vm上。

   为每一个添加到vm上的属性，都指定一个getter/setter。

   在getter/setter内部去操作（读/写）data中对应的属性。

细节：

vm._data中也有getter、setter，是做了个数据劫持

想实现name改变，模板中name实时改变，就要对_data中数据进行数据劫持

![image-20211111130927698](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111130927698.png)

![image-20211111130808309](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111130808309.png) 

## 1.6. 事件处理 

### 事件的基本使用

效果：

<img src="/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211002133155911.png" alt="image-20211002133155911" style="zoom:25%;" />

验证showInfo能不能接收参数

第一个参数是默认事件对象

![image-20211111131415988](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111131415988.png)

总结事件对象有啥：

1、enent.target(经常用)：拿到事件对象（元素），拿到元素后可以做很多事如：enent.target.innerText

​	

![image-20211111131645096](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111131645096.png)

验证showInfo事件中的this是谁？

this是vue对象

  ![image-20211111131901328](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111131901328.png)

当写成箭头函数时，this是window对象，如果要接受vue的管理，就不能用箭头函数

![image-20211111132053519](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111132053519.png)

![image-20211111132234515](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111132234515.png)

简写形成

用@符，不是去调v-on，因为那是v-bind的机械

![image-20211111132428314](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111132428314.png)

传其他参数

有这种需求，如：页面上有学生信息，点击删除要把学生的id传给删除事件

一个参数会丢失事件对象

![image-20211111132801437](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111132801437.png)

通过$event从新把事件对象传进来

![image-20211111132955831](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111132955831.png)

mounted中的方法是不做数据代理的

可以放到data中做代理，但是会让vue很累，数据代理是代理数据用的，代理方法没意义

![image-20211111133152286](/Users/liyang/项目整理/13.vue全家桶学习项目/vue-starter-kit/vue_basic/README.assets/image-20211111133152286.png)

总结：

事件的基本使用：

1.使用v-on:xxx 或 @xxx 绑定事件，其中xxx是事件名；

2.事件的回调需要配置在methods对象中，最终会在vm上；

3.methods中配置的函数，不要用箭头函数！否则this就不是vm了；

4.methods中配置的函数，都是被Vue所管理的函数，this的指向是vm 或 组件实例对象；

5.@click="demo" 和 @click="demo($event)" 效果一致，但后者可以传参；



绑定监听

1. v-on:xxx="fun"
2. @xxx="fun"
3. @xxx="fun(参数)"
4. 默认事件形参: event 5. 隐含属性对象: $event

### 事件修饰符

### 1.6.3. 事件修饰符

1. .prevent : 阻止事件的默认行为 event.preventDefault() 
2. .stop : 停止事件冒泡 event.stopPropagation()

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

1. mounted(): 发送 ajax 请求,启动定时器等异步任务测试
2. beforeDestory(): 做收尾工作, 如: 清除定时器

[^1]: \[Vue warn]: Failed to load resource: the server responded with a status of 404 (Not Found)
[^2]: \[Vue warn]: Property or method "age" is not defined on the instance but referenced during render. Make sure that this property is reactive, either in the data option, or for class-based components, by initializing the property.
[^3]: \[Vue warn]: Vue is a constructor and should be called with the \`new` keyword
[^4]: [Vue warn]: Error compiling template:href="{{school.url}}": Interpolation inside attributes has been removed. Use v-bind or the colon shorthand instead. For example, instead of \<div id="{{ val }}">, use \<div :id="val">.
[^5]: [Vue warn]: Error compiling template:invalid expression: Unexpected token '{' in {{school.url}} Raw expression: :href="{{school.url}}"
[^6]: [Vue warn]: Error compiling template: \<h2 v-model="name">: v-model is not supported on this element type. If you are working with contenteditable, it's recommended to wrap a library dedicated for that purpose inside a custom component.


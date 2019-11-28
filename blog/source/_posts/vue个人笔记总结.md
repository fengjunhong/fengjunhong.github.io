---
title: vue个人笔记总结
date: 2019-11-28 09:53:20
categories: vue
tags:
	- 个人笔记
---
### es6的用法

#### let

```javascript
特点：
1、局部作用域
2、不会存在变量提升
3、变量不能重复声明
```

#### const

```javascript
特点：
1、局部作用域
2、不会存在变量提升
3、不能重复声明,只声明常量,不可变的量
```
<!--more-->
### vue的介绍

#### vue的基本引入和创建

1.下载

```javascript
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

2.引包

```javascript
<script src="./vue.js"></script>
```

3.实例化

```javascript
// 3、实例化对象
new Vue({
      el:"#app", // 绑定那块地
      data:{
           name:"冯绍峰",
           msg:"黄瓜"
       }
})
```

#### Vue的模板语法

可以插入任何你想插入的内容,除了if else ,if else用三元运算符代替

```html
<!--模板语法-->
<h2>{{ msg }}</h2>
<h2>{{ 'haha' }}</h2>
<h2>{{ 1+1 }}</h2>
<h2>{{ {'name':'alex'} }}</h2>
<h2>{{ person.name }}</h2>
<h2>{{ 1>2 ? '真的' : '假的' }}</h2>
<h2>{{ msg.split('').reverse().join('') }}</h2>
```

#### vue的指令系统

v-text和v-html

```html
v-text 相当于innerText
v-html 相当于innerHtml
```

v-if 和v-show

```js
v-show 相当于 style.display
```

v-if 和 v-show的区别

```js
v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。

v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。

相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。

一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。
```

v-bind 和 v-on

```js
v-bind 可以绑定标签中任何属性
v-on   可以监听js中所有事件
```

v-bind

```javascript
<body>
    <div id="app" >
        <img v-bind:src="imgSrc" v-bin:alt="error">
    </div>
<!--1、引包-->
<script src="./vue.js"></script>
<script>
    //数据驱动视图  设计模式 MVVM Model View ViewModel
    new Vue({
        el:"#app",
        data() {
            // data是一个函数 函数中return一个对象，可以是空对象 但不能不return
            return{
                imgSrc:"1.jpg",
                error:"美女校花"
            }
        }
    })
</script>

</body>
```

v-on

```javascript
<body>
<!--1、引包-->
<script src="./vue.js"></script>
<style>
    .box {
        width: 500px;
        height: 300px;
        background-color: red;
    }
</style>
<div id="content">
    <button v-on:click="handlerClick" v-text="btn_isShow"></button>
    <div class="box" v-show='isShow'></div>
</div>
<script src="vue.js"></script>
<script>
    new Vue({
        el: "#content",
        data() {
            return {
                msg: "<h2 style='color: blue;'>alex</h2>",
                isShow: true,
                btn_isShow:"隐藏"
            }
        },
        methods: {
            handlerClick() {
                if(this.isShow==true){
                    this.btn_isShow="显示"
                }else{
                    this.btn_isShow="隐藏"
                }
                this.isShow = !this.isShow
            }
        }
    })
</script>

</body>
```

#### 组件之间的传值

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-zqrnkhV4-1574906191338)(C:\Users\Mr.Feng\AppData\Roaming\Typora\typora-user-images\image-20191120212450590.png)]

- 父组件向子组件传值

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div id="app" >
        <App/>
    </div>
<!--1、引包-->
<script src="./vue.js"></script>
<script>
    Vue.component('Vbtn',{
        data() {
            return{}
        },
        props: ['id'],
        template:`<button>{{ id }}</button>`
    })

    let Vheader={
        data(){
            return{}
        },
         //只要声明了父组件的属性，就可以使用
        props:['msg',],
        template:`<div>
                        <h2>{{ msg }}</h2>
                   </div>
                   `
        ,
    }
    //1、声子
    let App = {
        data(){
            return{
                text:"我是父组件的数据",
            }
        },
        template: `<div class="a">
                        <Vheader :msg="text"></Vheader>
                    </div>
                    `
        ,
        components: {
            Vheader
        }
    }
    new Vue({
        el:"#app",
        data(){
            return{
                msg:"alex",
            }
        },
        components:{
            //2、挂子
            App
        }
    })
</script>
</body>
</html>
```

- 子组件向父组件传值

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div id="app" >
        <App/>
    </div>
<!--1、引包-->
<script src="./vue.js"></script>
<script>
    Vue.component('Vbtn',{
        data() {
            return{}
        },
        props: ['id'],
        template:`<button @click="clickHandler">{{ id }}</button>`,
        methods:{
            clickHandler(){
                this.id++
                //每个组件中的指的基当期组件对象
                console.log(this)
                //this.$emit('父组件声明自定义的事件','传值')
                this.$emit("clickHandler",this.id)
            }
        }
    })

    let Vheader={
        data(){
            return{}
        },
        created() {
            console.log(this)
        },
        props:['msg','post'],
        template:`<div>
                        <h2>{{ msg }}:{{ post.id }}</h2>
                        <h3>{{ post.title }}</h3>
                        <Vbtn :id="post.id" @clickHandler="clickHandler"></Vbtn>
                   </div>
                   `
        ,
        methods: {
            clickHandler(val){
                this.$emit("click_handler",val)
            }
        }
    }
    //1、声子
    let App = {
        data(){
            return{
                text:"我是父组件的数据",
                post: {
                      id: 1,
                      title: 'My Journey with Vue'
                }
            }
        },
        created() {
            console.log(this)
        },
        template: `<div class="a">
                        我是父组件的 {{ post.id }}
                        <Vheader :msg="text" :post="post" @click_handler="click_handler"></Vheader>
                    </div>
                    `
        ,
        components: {
            Vheader
        },
        methods:{
            click_handler(val){
                this.post.id=val
            }
        }
    }
    new Vue({
        el:"#app",
        data(){
            return{
                msg:"alex",
            }
        },
        created() {
            console.log(this)
        },
        components:{
            //2、挂子
            App
        }
    })
</script>
</body>
</html>
```

- 平行组件之间的传值

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div id="app" >
        <first></first>
        <second></second>
    </div>
<!--1、引包-->
<script src="./vue.js"></script>
<script>
    //声明全局Vue对象
    let bus=new Vue()
    //组件二
    Vue.component("second",{
        data() {
            return{
                text:""
            }
        },
        created(){
            bus.$on('testData',(val)=>{
                console.log(this)
                this.text=val
            })
        },
        template: `<h3>{{ text }}</h3>`
    })

    //组件一
    Vue.component("first",{
        data() {
            return{
                msg:"我是组件1️⃣"
            }
        },
        template:`<button @click="clickHandler">数据迁移</button>`,
        methods:{
            clickHandler(){
                bus.$emit("testData",this.msg)
            }
        }
    })
    //创建Vue实例
    new Vue({
        el:"#app",
        data(){
            return{}
        }
    })
</script>
</body>
</html>
```

#### 生命周期钩子函数

- beforeCreate  组件创建之前

- created           组件创建之后

- beforeMount   组件挂载之前

- mounted         组件挂载之后

   [外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-2WDmruFs-1574906191341)(C:\Users\Mr.Feng\AppData\Roaming\Typora\typora-user-images\image-20191121222550856.png)]

- beforeUpdate 

- updated 

- activated       

     激活当前组件

- deactivated     

  ​    keep- alive Vue提供的内置组件，主要作用 ,让组件产生缓存

​    停用当前组件

- beforeDestroy   

-  destroyed     

​    如果开了定时器,一定要关闭定时器、

#### vue-router的基本使用

```html
<!DOCTYPE html><html lang="en">
    <head>    
    <meta charset="UTF-8">    
    <title>Title</title>
    </head>
    <body>    
        <div id="app">        
            <App/>   
        </div>    
        <script src="vue.js"></script>    
        <script src="vue-router.js"></script>
        <script>    
            const Home = {        
                data(){            
                    return{}        
                },        
                template: `<div>我是主页</div>`    
            }    
            const Course = {        
                data(){            
                    return{}        
                },        
                template: `<div>我是免费课程</div>`    
            }    
            // 创建router实例    
            const router = new VueRouter({        
                // 定义router规则        
                routes:[            
                    {               
                        path:'/',                
                        component : Home            
                    },            
                    {                
                        path:'/Course',                
                        component : Course            
                    }        
                ]    
            })    
            let App = {        
                data() {            
                    return {}        
                },        
                template: `<div>                        
                            <div class="header">                            
                                <router-link to="/">首页</router-link>                            
                                <router-link to="/Course">免费课程</router-link>                        						  </div>                        
                              <router-view></router-view>                   
            			   </div>                  
						`,    
            }    
            new Vue({        
                el : "#app",        
                router,        
                data(){            
                    return{}        
                },        
                components:{            
                    App        
                }    
            })</script></body></html>
```

#### 命名路由

```javascript
routes:[    # 定义路由规则
    {        
        path:'/dfssf',        
        name:'Home',        
        component : Home    
    },    
    {        
        path:'/Coursedddddddddddddddddd',        
        name:'Course',        
        component : Course    
    }]


template: `<div>
                <div class="header">
                    <router-link :to="{name:'Home'}">首页</router-link>
                    <router-link :to="{name:'Course'}">免费课程</router-link>
                </div>
                <router-view></router-view>
		 </div>
		`,
```

  #### 动态路由匹配

```javascript
  提醒一下，当使用路由参数时，例如从 /user/foo 导航到 /user/bar，原来的组件实例会被复用。因为两个路由都渲染同个组件，比起销毁再创建，复用则显得更加高效。不过，这也意味着组件的生命周期钩子不会再被调用。
```

```js
  created(){     
      this.user_id = this.$route.params.id   //因此使用此方法，无法获取用户的id
      consolo.log(this.$route)
  }
```
- 复用组件时，想对路由参数的变化作出响应的话，你可以简单地 watch (监测变化) $route 对象：


```js
watch: {
    '$route' (to, from) {
      // 对路由变化作出响应...
    }
  }
```

![image-20191125231714548.png](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pLmxvbGkubmV0LzIwMTkvMTEvMjgvYnFLa0VmclZCTzF0VElDLnBuZw?x-oss-process=image/format,png)
####  编程式的导航 
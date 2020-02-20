# 什么是 Vue CLI

CLI是Command -Line Interface,翻译为命令行界面，俗称脚手架

使用vue-cli 可以快速搭建Vue开发环境以及对应的webpack配置

# 使用前提 -Node -webpack

依赖于node，需要8.9或更高版本



# 安装vue脚手架3

直接使用全局安装-g

```bash
npm install -g @vue/cli
```

检查版本

```
vue --version
```

# 拉取 2.x 模板 (旧版本)

Vue CLI >= 3 和旧版使用了相同的 `vue` 命令，所以 Vue CLI 2 (`vue-cli`) 被覆盖了。如果你仍然需要使用旧版本的 `vue init` 功能，你可以全局安装一个桥接工具：

这样既可以使用2，也可以使用3

```bash
npm install -g @vue/cli-init
```

## --------------------------

# 脚手架二

#### 创建项目

```
vue init webpack 项目名称
```

#### vue编译步骤

template-ast-render-vdom-UI

#### 选项

安装时的选项

```
project name： 项目名称（回车默认创建时的名称）
project description：项目描述
Author： 作者
Vue build:构建项目时用哪一个来构建（上下键选择，推荐第二个,在vue项目运行步骤中，第二个去掉了template到ast的步骤，直接从render开始，所以编译步骤更少，所以项目大小会更小）


Install vue-router？（Y/N）: 是否安装路由 (还没学，暂时no)
Use ESLint to lint your code?(Y/N):是否安装eslint(自动检测代码是否规范，代码格式不规范，编译器会报错)，如果选择安装，它会让你选择一种规范模式（可以选择第一个标准，也可以直接不安装）
Set up unit tests（Y/N）：单元测试（用的比较少，暂时不要）
Setup e2e tests with Nightwatch?(Y/N):端到端测试，要安装Nightwatch（暂时不要）

最后会让你选择管理项目是用npm，还是用Yarn （暂时用npm，Yarn是谷歌facebook联合推出的一个新的包管理工具）
```

#### 文件夹解读

build，config文件夹都是webpack的设置。node_modules是当前项目依赖的node的包。

src文件夹存放自己的写的代码，写代码都在这里面写

static文件夹，放一些静态的资源。会原封不动的放到打包的文件夹







## --------------------------

# 脚手架三

vue-cli3基于webpack4打造,vue-cli2基于webpack3打造

vue-cli3的设计原则是 “0配置”，移除配置文件根目录下的build，config文件夹

还提供了vue ui命令，提供了可视化配置，更加人性化

移除了static文件夹，新增了public文件夹，并且index.html移动到public中

#### 创建项目

```
vue create 项目名称
```

#### 选项

```
Please pick a preset:选择一个预设
default(默认，会添加babel，eslint)，Manually 手动（建议）。

Check the features needed for your project:检查项目所需的功能
空格选择和取消，与2差不多，只不过一次性选择完毕

Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
您希望在哪里放置Babel，ESLint等的配置？（使用箭头键）
In dedicated config files ：单独配置一个文件(建议)
In package.json ：放在package.json后面

Save this as a preset for future projects? (y/N)
将其保存为预设以供将来的项目使用吗？ （是/否）
保存为一个预设模板，下次创建项目第一个选项会多一个。保存的话会让你取一个名字

最后选择包管理工具 选择npm
```

#### 文件夹解读

public ： 放一些静态的资源。会原封不动的放到dist文件夹

.browserslistrc ： 浏览器的一些配置

.gitignore： 忽略设置（把一些不想上传和共享的文件忽略）

babel.config ： 对bable进行配置

package.json : 包管理设置

#### 运行

npm run serve

# ---------------------------------

# Vue 项目管理器

在终端任何目录输入vue ui启动本地管理器

**用户图形化界面 管理整个项目相关的配置**

创建项目可以直接在这里创建，也可以通过命令创建

主要的是项目管理，选择导入，找到项目根目录，点击导入项目就可以进入到管理界面，里面可以进行相关的一切配置，包括打包运行等

# 自定义配置文件

可以在根目录定义一个vue.config.js文件，定义一些我们独有的配置

# ---------------------------------

# 路由Vue-Router

#### 什么是路由

路由是一个网络工程里面的术语

就是通过互联网的网络信息从源地址传输到目的地址的活动

#### 认识vue-router

vue-router是vue官方的路由插件，它和vue是深度集成的，适合构建单页面富应用

**vue-router是基于路由和组件的**

路由用于设定访问路径，将路径和组件映射起来

在vue-router的应用中，页面的路径的改变就是组件的切换

#### 安装和使用

#### **安装**

```bash
npm install vue-router --save
```

#### 配置

安装完成后在src文件夹下，会有一个router路由文件夹，路由的相关配置都是在里面的index.js配置

**第一步，导入相关包**

```javascript
import VueRouter from 'vue-router'
import Vue from 'vue'
```

**第二步，通过Vue.use(插件)，安装插件**

只要是插件，都要通过这个方法安装

```javascript
Vue.use(VueRouter)
```

**第三步，创建VueRouter对象**

```javascript
const router = new VueRouter({
    
})
```

**第四步，配置路由和组件之间的映射关系routes**

单独抽离出来，然后在VueRouter对象中引用

```javascript
const routes=[

]
const router = new VueRouter({
  //配置路由和组件之间的映射关系routes
  routes
})
```

**第五步，导出，然后在vue实例main.js中 导入使用**

导入的如果是文件夹，自动找到里面的index.js

```javascript
export default router

import router from './router'
```



# 使用vue-router

#### **第一步，创建路由组件**

一个路径和一个组件形成映射关系

在components文件夹创建相关的vue组件

#### **第二步，创建映射关系**

一个映射关系就是一个对象。有两个属性

path：如果有该url，就映射下面的component组件

component：组件名

**注意：映射组件时先导入组件**

```javascript
import Home from '../components/Home'
import About from '../components/About'
const routes=[
  {
    path:"/home",
    component:Home
  },
  {
    path:"/about",
    component:About
  }
];
const router = new VueRouter({
  routes
})
```

#### **第三步，使用路由**

在App.vue中使用两个标签来使用路由

因为在子组件中只有路径发生改变才会执行，一开始就显示的东西要写在主vue文件中



**router-link:** 是vue_router中注册的全局组件.最终会被渲染为a标签

点击后，URL就会发生对应的变化。会找到对应的组件，触发路由映射关系，渲染到rputer-view的位置

**router-link:to属性**：指定跳转的路径

**router-link:tag属性**：指定渲染为什么组件。默认是渲染为a标签

**router-link:replace属性**：禁用浏览器的返回按钮，没有值

```
当router-link对应的路由匹配成功时，会自动给当前元素设置一个router-link-active的class。

在进行高亮显示的导航菜单，或者底部tabbar时，会使用到该类

通常不会修改名字，直接在style使用默认的名字。

如果想要修改的话，在VueRouter对象中新加一个属性

linkActiveClass:"active" 
router-link-active改为active
```





**router-view：**作为占位，决定渲染出来的组件放在什么位置

```javascript
<template>
  <div id="app">
    <router-link to="/home">首页</router-link>
    <router-link to="/about">关于</router-link>
    <router-view></router-view>
  </div>
</template>

<script>
  export default {
    name:"App"
  }
</script>

<style>

</style>
```



#### meta 元数据

meta：元素据，用来描述数据的数据

```javascript
  {
    path:"/about",
    component:About,
    meta:{
        title:"首页"
    }
  },
```







# 路由的跳转

#### 默认路由

当路径为空的时候，默认显示首页组件，使用redirect重定向

```javascript
const routes=[
  {
    path:"",
    redirect:"/home"
  },
  {
    path:"/home",
    component:Home
  },
  {
    path:"/about",
    component:About
  }
];
```

#### 路径显示的方式

默认 hash 模式 —— 使用 URL 的 hash 来模拟一个完整的 URL

如果不想要很丑的 hash，我们可以用路由的 **history 模式**

创建VueRouter对象的时候新添加一个属性即可

```javascript
const router = new VueRouter({
  routes,
  mode:"history"
});
```

#### 通过代码修改路径

可能在方法中或者别的地方也需要修改路径

```javascript
  export default {
    name:"App",
    methods:{
      home(){
          //push => pushState
          //$router = 大的路由对象
        this.$router.push('/home') //有返回按钮
        this.$router.push('/home/',this.userId) //跟属性的方法
        this.$router.replace('/home')  //没有返回按钮
      },
      add(){
        this.$router.push('/add')
        this.$router.replace('/add')
      }
    }
  }
```

# 动态路由

#### 什么是动态路由

在某些情况下，一个页面的path路径可能是不确定的，比如我们进入用户界面，希望是下面的路径：

/user/zhangasan，/user/lisi

除了有前面的/user之外，后面还跟上了用户的ID

**这种path和Component的匹配关系，我们称之为动态路由（也是数据传递的一种方式）**

#### 1.路由配置

```javascript
  {
    path:"/user/:user_id",
    component:User
  }
```

#### 2.动态获取属性值

通过v-bind来拼接

'/user/' 加上单引号表示user是一个真实的字符串

```javascript
<template>
    <router-link :to="'/user/'+user_id">用户</router-link>
    <router-view></router-view>
  </div>
</template>

export default {
    name:"App",
    data(){
      return{
        user_id:"zhangsan"
      }
    },
  }
```







# 路由的懒加载

#### 为什么使用懒加载

路由中通常会定义很多不同的页面，最后打包到一个js文件，会造成这个文件非常的大，

如果我们一次性从服务器请求下来这个页面，可能需要花费一点的时间，甚至出现短暂空白的情况。



**使用懒加载就可以避免这种情况**

#### 懒加载做了什么

路由懒加载的主要作用就是将路由对应的组件打包成了一个个的js代码块

只有在这个路由被访问的时候，才会加载对应的组件





#### 使用懒加载

使用懒加载后，不需要导入组件，而是进行动态获取



通过赋值的方式写，比较清晰好管理



打包后，static的js文件夹的文件会从3个变成多个，一个懒加载对应一个js文件

```javascript
const Home = () => import('../components/Home')
const About = () => import('../components/About')
const User = () => import('../components/User')

// 第一步安装插件
Vue.use(VueRouter);

// 第二步创建对象
const routes=[
  {
    path:"",
    redirect:"/home"
  },
  {
    path:"/home",
    component:Home
  },
  {
    path:"/about",
    component:About
  },
  {
    path:"/user/:user_id",
    component:User
  }
];
```





# 嵌套路由

路由嵌套是一个常见的功能

​	比如在home页面中，我们希望通过/home/news，和/home/message访问一些内容

​	一个路径映射一个组件，访问这两个路径也会分别渲染两个组件





#### 一：创建对应的子组件

创建对应的子组件，并且在路由映射中配置对应的子路由



因为是home的子级，所以写在home的children属性里面，也使用懒加载

也有默认值

```javascript
{
    path:"/home",
    component:Home,
    children:[
      {
        path:"",
        redirect:'news'
      },
      {
        path:"news",
        component:Home_News
      },
      {
        path:"news",
        component:Home_Message
      }
    ]
  },
```





#### 二：使用router标签

App.vue的<router-view>标签是显示主路由的。

所以home的子路由的<router-view>标签要写在Home.vue里面

并且也要配置<router-link>标签

路径要写完整路径

```vue
<template>
  <div>
    <h2>我是首页</h2>

    <router-link to="/home/news">新闻</router-link>
    <router-link to="/home/message">消息</router-link>
    <router-view></router-view>
  </div>
</template>
```









# 参数传递的方式

#### $route和$router的去区别

$router为VueRouter的实例，想要导航到不同的URL，则使用$router.push方法

$route 为当前router跳转对象里面可以获取的name,path,query,params等（当前活跃的组件）





传递参数主要有2种类型：params和query

#### Params类型

配置路由：

```javascript
  {
    path:"/user/:user_id",
    component:User
  }
```



传递方式：通过v-bind传递一个对象，在path后面跟上对应的值

user_id是data中的一个动态属性

```vue
<router-link :to="'/user/'+user_id" tag="button">用户</router-link>
```





$route: 表示当前活跃的组件，注意和$router的区别



接收：

```vue
<template>
    <h2>我是用户</h2>
    <h2>{{$route.params.user_id}}}</h2>
</template>
```

传递后形成的路径

```
/router/123,	/router/abc
```





#### query类型



也是通过v-bind传递一个对象



路由的配置就是普通的配置方法



path的属性用来跳转，query属性的值也是一个对象，用来传递参数

```vue
<router-link :to="{path:'/profile',query:{name:'lwy'}}">档案</router-link>

```

url中?后面拼接的就是query的值

```
http://192.168.43.18:8080/profile?name=lwy
```

取值$route.query

```vue
<template>
  <div>
    <h2>我是profile组件</h2>
    <p>{{$route.query.name}}</p>
  </div>
</template>
```





#### 通过代码传递

需要在方法中或者别的地方传递

```vue
<template>
  <div id="app">
    <button @click="UserClick">用户</button>
    <button @click="ProfileClick">档案</button>
    <router-view></router-view>
  </div>
</template>

<script>
  export default {
    name:"App",
    data(){
      return{
        user_id:'zhangsan'
      }
    },
    methods:{
      UserClick(){
        this.$router.push('/user/' + this.user_id) 
      },
      ProfileClick(){
        this.$router.push({
          path:"/profile",
          query:{
            name:'lwy',
          }
        })
      }
    }
  }
</script>

<style>

</style>

```







# 导航守卫

#### 什么是导航守卫

可以对来回跳转之间的一些过程做一些监听

#### 生命周期函数

在组件被创建出来时，会回调一个created（）函数

当模板的内容全部被挂载到Dom之后，会回调mounted（）函数

在界面发生刷新时，回调updated（）函数

销毁时：回调destroyed()

处于活跃状态: 回调activated() ，使用了keep-alive才有效

处于非活跃状态: 回调deactivated() ，使用了keep-alive才有效



可以用生命周期函数来实现一些功能，写在最外层，不是methods里面







### 全局守卫

上面我们使用的2个导航守卫，被称之为全局守卫

#### 前置守卫函数

在index.js中使用router实例的beforeEach 前置守卫函数

**守卫（guard）：**回调的意思

**前置钩子：**在跳转之前的回调



**to：**即将要进入目标的路由对象

**from：**当前导航即将要离开的路由对象

**next（）：**  进入管道中下一个钩子，也可以传递参数 （必须调用）

**next（false）：** 中断当前导航，如果url改变了（可以是用户手动或后退按钮），那么url地址会重置到from路由对应的地址

**next（{path:"/"}）:** 跳转到新地址，当前导航被中断，一般和判断条件使用

```javascript
router.beforeEach((to, form, next) => {
  next()
})
```

**案例：**

```javascript
router.beforeEach((to, form, next) => {
  document.title = to.matched[0].meta.title
  next()
})

使用路由中元数据的值
```







#### 后置钩子函数

**钩子（hook）：**也是回调的意思

**后置钩子：**在跳转完成之后的回调



不需要调用next属性，因为已经执行完了



```javascript
router.afterEach((to, form) => {
  console.log('完成');

});
```







### 路由独享守卫

你可以在路由配置上直接定义守卫：

**beforeEnter**（to, from, next） => {

}

进入到该路由就会回调它(这里也需要调用next（）)

```javascript
  {
    path: "/about",
    component: About,
    meta: {
      title: "关于"
    },
    beforeEnter:(to, from, next) => {
      console.log("欢迎进入关于页面");
      next()
    }
  },
```

### 组件内的守卫

```js
const Foo = {
  template: `...`,
  beforeRouteEnter (to, from, next) {
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
  },
  beforeRouteUpdate (to, from, next) {
    // 在当前路由改变，但是该组件被复用时调用
    // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
    // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave (to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  }
}
```

# 组件保留状态

### keep-alive

keep-alive是Vue内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染

**简单理解：**离开某一个组件的时候，不要让这个组件频繁的被销毁和创建，让它保持活着的状态

所以，当使用了keep-alive的时候，组件只有活跃和非活跃状态，诞生和死亡状态只有一次



router-view也是一个组件，如果直接包在keep-alive里面，所有路径匹配到的视图组件都会被保存，而不是每次都要重新创建一个组件



使用很简单

```vue
    <keep-alive><router-view/></keep-alive>
```

**发现：组件内部的状态并没有保存**

**解决方法：**

一、先把/home的children子级为空重定向关闭

二、把首页的初始路径保存为一个变量

```
    data(){
      return{
        path:"/home/news"
      }
    },
```

三、在Home.vue通过内置回调函数activated来保存上一次离开时URL的状态

```vue
    activated() {
      this.$router.push(this.path)
    },
```



**四、然后用组件内守卫的beforeRouteLeave方法**

```javascript
  beforeRouteLeave (to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  }
```

```vue
    beforeRouteLeave(to, from, next){
      this.path = this.$route.path;
      next()
    }
```





### keep-alive的属性

多个组件都被<keep-alive><router-view/></keep-alive>声明，但是其中某几个组件，需要被频繁的创建

这时候就需要用到keep-alive的属性了

include： 字符串或正则表达式，只有匹配的组件会被缓存

exclude： 字符串或正则表达式，只有匹配的组件都不会被缓存



这里属性值的是组件中自己的name值

```vue
    <keep-alive exclude="Profile,User">//这里不能加空格
      <router-view/>
    </keep-alive>
```

# 路径的别名

### 

有时候路径过长或层级过深，修改路径时十分麻烦

可以通过给路径起别名来简化，并且代码的位置发生改变，不用修改路径

### 脚手架二

路径的别名属于webpack的配置，所以找到webpack.base.conf.js文件		resolve的alias下进行配置

```javascript
resolve:{
  extensions:['.js','.vue','.json']
  alias:{
    "@": resolve('src'),
  }
}
```

这里给src文件夹起了一个别名为@



**注意： 在src中寻找别名需要加上~符号，import才可以直接寻找**

```vue
<img src="../assets/images/tabbar/我的.png" alt="">
如果assets是在src下面的文件夹，就可以写成
<img src="~@/assets/images/tabbar/我的.png" alt="">
```

或者添加一个

```javascript
resolve:{
  extensions:['.js','.vue','.json']
  alias:{
    "@": resolve('src'),
    "&&":resolve('src/assets/images')
  }
}
```

那上面的路径就可以直接写成

```vue
<img src="~&&/tabbar/我的.png" alt="">
```

### 脚手架三

因为脚手架三的配置文件默认隐藏，所以我们在自己创建的vue.config.js文件夹配置

```javascript
module.exports={
  configurWebpack:{
    resolve:{
      //extensions这里不需要了，因为vue默认配置了
      alias:{
        "assets":"@/assets",  //脚手架三写法
      }
    }
  }
}
```

其余步骤和上面一样

**使用**

```css
<style>
@import "assets/css/base.css"
</style>
```

注意： 在html中使用别名，需要加~

# ------------------------------------

# Promise

#### 什么是promise

**ES6的一个重要特性，Promise是异步编程的一种解决方案，对你的异步操作做一些相关的封装，使代码易于维护**

#### 什么时候用到Promise

一般是有异步操作时使用，对这个异步操作进行封装

#### 基本使用

Promise是一个内置对象，用new使用，有2个参数,resolve,reject

#### **resolve参数的使用**

成功时调用

```javascript
        new Promise((resolve, reject) => {
            //第一次网络请求
            setTimeout(() => {
                resolve()
            }, 1000)
        }).then(() => {
            //第一次拿到结果
            return new Promise((resolve, reject) => {
                //第二次网络请求
                setTimeout(() => {
                    resolve()
                }, 1000)
            }).then(() => {
                // 第二次拿到结果
            })
        })
```

就相当于把原来在setTimeout的处理的代码提取到了外面,不在内部处理





虽然代码变多了，但是逻辑更清楚了





#### reject参数的使用

网络请求可能成功可能失败，sesolve是成功时执行的代码，reject是sesolve失败执行的代码



reject()函数传递到.catch

```javascript
        new Promise((resolve, reject) => {
            setTimeout(() => {
                resolve()
                reject()
            }, 1000)
        }).then(() => {
        
        }).catch(() => {
           
            
        })
```



#### **传递参数**

```javascript
        new Promise((resolve, reject) => {
            setTimeout(() => {
                resolve("hello world")
                reject("连接失败")
            }, 1000)
        }).then(data => {
            console.log(data);           
        }).catch(date => {
            console.log(date);
        })
```



#### Promise的三种状态

首先，当我们开发中有异步操作时，就可以给异步操作包装一个Promise

​	异步操作之后会有2种状态



padding：等待状态，比u人正在进行网络请求，或者定时器没有到时间

fulfill：满足状态，当我们主动回调了resolve时，就处于该状态，并且会回调.then()

reject：拒绝状态，对我们主动调用了reject时，就处于这个状态，并且会回调.catch()

#### Promise的All方法

判断多个请求

```javascript
        Promise.all([
            new Promise((resolve, reject) => {
                setTimeout(() => {
                    resolve('results1')
                }, 2000)
            }),
            new Promise((resolve, reject) => {
                setTimeout(() => {
                    resolve('results2')
                }, 1000)
            }),
        ]).then(results => {
            console.log(results);

        })
```

如果2个请求都完成，才会进入到.then方法

这里的.then方法的参数拿到的是是一个数组，包含了所有请求的结果



# -----------------------------------

# Vuex

#### 什么是vuex

vuex是一个专门为vue.js应用程序开发的**状态管理模式**

它采用 **集中式存储管理** 应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

简单理解就是一个状态管理工具

#### 什么是状态管理

状态管理模式，集中式存储管理

可以理解为：把多个组件共享的变量全部存储在一个对象里面

然后，将这个对象放在顶层的Vue实例中，让其他组件可以使用



所以，vue就提供了一个在多个组件之间共享状态的插件vuex



#### 安装

```bash
npm install vuex --save
```



# 五大核心

在src下创建文件夹store（仓库），然后创建index.js,用来存放vuex代码

```javascript
import Vue from 'vue'
import Vuex from 'vuex'

//安装插件
Vue.use(Vuex)

//创建对象.真正创建的是Vuex中的Store类
const store = new Vuex.Store({
  state:{
	conter:0
  },
  mutations:{

  },
  actions:{

  },
  getters:{

  },
  modules:{

  }
})

//导出
export default store
```

在main.js导入注册，和路由一样

store的所有属性都是固定的



#### state属性

**state：存放状态相关的信息,**

在其他组件访问：$store.state.变量名

```html
<h2>{{$store.state.conter}}</h2>		
```



#### mutations属性

**mutations：对state属性的修改一定在这里进行**

**不要在mutations进行异步操作**

里面定义的都是函数，并且会把state默认传递过去

```
  state:{
    conter:1
  },
  mutations:{
    increment(state){
      state.conter++
    },
    decrement(state){
      state.conter--
    }
  },
```

在这里处理后，在别的组件就可以使用了

**this.$store.commit（）来获取**

```
  methods: {
    addition(){
      this.$store.commit("increment")
    },
    subtraction(){
      this.$store.commit("decrement")
    }
  },
```

**注意事项：**

我们通过提交mutation的方式，而非直接改变store.state.conter

这是因为Vuex可以更明确的追踪变化，所以不要直接修改

##### **mutations参数的传递**

参数被称为mutation的载荷（Payload）

**外部组件传递进来**

外部组件调用时传递一个count，count的值是调用addCount传入的

```
    addCount(count){
      this.$store.commit('incrementCount',count)
    }
```

在mutation通过定义形参接收count

```
    incrementCount(state,count){
      state.conter += count
    }
```

如果参数不止一个，Payload也可以是一个对象



##### Mutation的响应规则

Vuex的store中的state时响应式的，当state中的数据方式改变时，Vue组件会自动更新

这就要求我们必须遵守一些Vuex对应的规则： 

1.提前在store中初始化好所需的属性

2.当给state中的对象添加新的属性时，使用下面的方式

​			使用vue.set（要修改的对象，索引值，修改后的值）（数组传索引，对象传字符串）

​			用新对象给旧对象赋值

3.删除属性

Vue.delete(要删除的对象，要删除对象中的属性)







#### getters属性

有时候需要对state的数据进行一些处理后再展示就用到getters，类似计算属性

**语法：**

```
  getters:{
    greaterAge: state => {
      return state.conter + 2
    }
  },
```

**其他组件调用**

```html
    <h2>
      getters处理后的数据
      {{$store.getters.greaterAge}}
    </h2>
```

也可以先传递到mutations属性，再做一层处理后，在别的组件直接调用mutations中的方法

**也可以进行多次嵌套处理，把gettes传入进去**

```
  getters:{
    greaterAge: state => {
      return state.conter * 2
    },
    greaterAges: (state,getters) => {
      return getters.greaterAge + 1
    }
  },
```

然后调用greaterAges就可以了，直接再这里处理，不用在别的组件处理

**getters的参数传递**

不能返回一个确定的东西，要返回一个函数

```
  getters:{
    greaterAge: state => {
      return state.conter * 2
    },
    greaterAdd: (state) => {
      return sum => {
        return state.conter * sum
      }
    }
  },
```

调用greaterAdd时传入sum就行了









#### actions属性

我们强调，**不要在mutation中进行异步操作**

​		actions就是用来代替mutation进行异步操作的

actions中定义的也是函数，有一个context默认参数，**context：上下文**

可以理解为 ：context = store对象



在actions可以直接通过commit来拿到mutations的方法**来进行异步修改**

因为actions的默认参数context就等于store对象，所以可以直接用context.commit

```
context.commit('aUpdateInfo')
```

然后在外部组件获取actions中修改后的方法，而不直接commit获取mutations的方法

通过this.$store.dispatch来绑定action中的方法

```
this.$store.dispatch('aUpdateInfo')
```







##### actions参数的传递

同样是外部组件传递进来

```
  methods: {
    aupdateInfo(){
      this.$store.dispatch('aUpdateInfo','我是payload')
    }
  },
```

index.js通过参数接收

```
  actions:{
    aUpdateInfo(context,pa){
      setTimeout(() => {
        context.commit('info')
        console.log(pa);
      },1000)
    }
  },
```

也可以传递一个对象，对面里面可以传递参数和回调函数





##### 和Promise结合使用

**actions可以和Promise异步处理结合使用**



#### modules属性

module是模块的意思，为什么在Vuex中我们要使用模块呢？
**Vue使用单一状态树，**就意味着很多状态都会交给Vuex来管理

当应用变得非常复杂时，store对象就有可能变得相当臃肿

为了解决这个问题，Vuex允许我们将store分割成模块单独放在modules中，而每个模块有自己的state，mutation，actions，getters等

```javascript
const store = new Vuex.Store({
  modules:{
    a:moduleA,
    b:moduleB,
  },
})


const moduleA = {
  state:{
    as:100
  },
  mutations:{},
  actions:{},
  getters:{}
}
const moduleB = {
  state:{},
  mutations:{},
  actions:{},
  getters:{}
}
```



访问模块中的属性可以直接通过{{$store.state.a.as}}来访问，因为它会默认把属性放到主store对象中

模块中的方法也是通过this.$store.commit（）来获取



##### 调用store对象的属性

如果想要在模块中调用store对象的属性怎么办？

在模块的形参中还可以传递一个**rootState参数**

通过这个参数就可以获取store对象的属性

rootState.counter



##### 模块中的actions属性

模块中使用actions属性的 context 不再指向store对象，而是指向它自己

使用context.commit方法也是指向的自己的mutations中的方法

##### 调用store对象的方法

通过context .rootGetters就可以拿到根mutations中的方法，不需要形参



# Devtools插件

**推荐使用**

Devtools是vue官方提供的一个浏览器插件，可以帮助我们捕捉mutation的快照

谷歌浏览器扩展商店直接安装，然后F12目录后面就多了一个vue的选项

ctrl + 2 切换为vuex的检测。可以查看vuex代码每一次的运行状态，

**Vuex的store状态的更新唯一方式：提交Mutation**







# ES6语法 对象的解构

```
const obj = {
	name:"why",
	age:18,
	height:1.88
}

原本的写法：
const name = obj.name
const age = obj.age
const height = obj.height

对象解构语法：
const {name, age, height}  = obj
相当于取出obj对象中的name, age, height
可以直接用了： console.log(name)

注意：顺序可以乱，可以用多少属性取多少属性




案例：
actions:{
	add({state,commit,rootState}){
		commit（"increment"）
	}
}
这里本来应该是一个context形参对象，但是我们通过解构写法，只取出context对象的中3个属性来使用
```







# Vuex代码的分离

##### state

state代码就分离到index.js内部

写法

```
const state = {
    as:100
}

const store = new Vuex.Store({
  state,
})
```

##### mutations

mutations建议在store文件夹下面新建一个js文件,在index.js记得导入

写法

```
export default{
  increment(state){
    state.conter++
  },
}
```

index.js

```
const store = new Vuex.Store({
  state,
  mutations,
})
```

##### actions

和mutations方法一样

##### getters

和mutations方法一样

##### modules

modules推荐在store文件夹下面再创建一个modules文件夹，专门用来存放模块

modules文件夹下的js文件就是一个一个的小模块





**modeleA.js**

```javascript
export default {
    state:{},
    mutations:{},
    actions:{},
    getters:{}
}
```

**导入**

```
import moduleA from './modules/modeleA'
```

**然后放到modeles处**

```
  modules:{
    a:moduleA,
  },
```

##### store最后结果

```javascript
const store = new Vuex.Store({
  state,
  mutations,
  actions,
  getters,
  modules:{
    a:moduleA,
    b:moduleB,
  },
})
```

# ------------------------------------

# axios网络模块

#### 安装

因为axios是一个独立的框架，所以要单独安装

```bash
npm install axios --save
```

#### 基本使用

```javascript
axios({
  url:"http://123.207.32.32:8000/home/multidata",
  method:"get",
  params:{ //专门针对get请求的参数拼接
    type:"pop",
    page:1
  }
}).then( res => {
  console.log(res);
})
```

**params：**把里面的参数以url的形式拼接到？的后面。和get请求是对应的



#### 发送并发请求

多个请求同时到达再继续执行代码

**使用axios.all,可以放入多个请求的数组**

```javascript
axios.all([
  axios({
    url:"http://123.207.32.32:8000/home/multidata",
  }),
  axios({
    url:"http://123.207.32.32:8000/home/multidata",
    params:{ 
      type:"sell",
      page:5
    }
  })
]).then( res => {
  console.log(res);
})
```

**axios.all([])返回的结果是一个数组，使用axios.spread可将数组[res1,res2]展开为res1,res2**

```javascript
axios.all([
  axios({
    url:"http://123.207.32.32:8000/home/multidata",
  }),
  axios({
    url:"http://123.207.32.32:8000/home/multidata",
    params:{ 
      type:"sell",
      page:5
    }
  })
]).then(axios.spread((res1, res2) => {
  console.log(res1);
  console.log(res2);
}))
```





#### 全局配置

一些全局的公共配置可以写到外面

**比如这里通过defaults方法设置了请求根目录和超时时间**

```javascript
axios.defaults.baseURL = "http://123.207.32.32:8000"
axios.defaults.timeout = 5000
```

这样在url就不用写根目录了

```
url:"/home/multidata",
```

#### 常见配置选项

```
请求地址
​		url:"/user"

请求类型
​		method:"get"

请求根路径
​		baseURL:"http://123.207.32.32:8000"

请求前的数据处理
​		transformRequest:[function(data){}]

请求后的数据处理
​		transformResponse:[function(data){}]		

自定义的请求头
​		headers:{"x-Requested-With":"XMLHttpRequest"},

URL查询对象
​		params:{id:22}
```

# axios实例

上面的2种使用方法都是使用的全局的axios和对应的配置在进行网络请求

一般在使用axios时，为了应对多个服务器的不同ip地址，不会直接使用全局的axios，而是会创建对应的实例



#### 基本使用

```javascript
const instance1 = axios.create({
  baseURL:"http://123.207.32.32:8000",
  timeout:5000
})
instance1({
  url:"/home/multidata"
}).then(res => {
  console.log(res);
})

instance1({
  url:"/home/multidata",
  params:{
    type:"pop",
    page:1
  }
}).then(res => {
  console.log(res);
})
```

# axios的封装

为了网络请求代码的复用性和维护性

可以单独封装出来，在别的文件引用

在src下面新建一个network的文件夹用来存放网络层的封装，里面创建一个request.js文件







#### 封装

**为了考虑扩展性，使用export function**

使用Promise来封装

instance本身返回就是一个Promise类型，所以可以直接return，不用返回一个Promise对象

```javascript
import axios from 'axios'


export function request(config) {
  //创建axios实例
  const instance = axios.create({
    baseURL: "http://123.207.32.32:8000",
    timeout: 5000
  })
  return instance(config)
}

```

#### 使用

发送网络请求时直接面向request就可以了

```javascript
import {request} from "./network/request"

request({
  url:"/home/multidata",
}).then(res => {
  console.log(res);
}).catch(err => {
  console.log(err);
})
```

# 拦截器





**axios提供了4种拦截器：**

请求成功，请求失败，响应成功，响应失败

**可以拦截实例对象或全局对象**

```javascript
  instance.interceptors
  axios.interceptors
```

#### 拦截请求

请求拦截的作用：

1.某些给服务器传递的数据不符合要求，我们可以拦截进行处理后，再给服务器

2.每次发送网络请求时，都希望在界面显示加载动画

3.某些网络请求（比如登录（token）），必须携带一些特殊的信息





拦截请求通过interceptors.request.use，要求传递2个参数，都是函数

**比如我们对axios的封装添加一个请求拦截器**



```js
import axios from 'axios'


export function request(config) {
  //创建axios实例
  const instance = axios.create({
    baseURL: "http://123.207.32.32:8000",
    timeout: 5000
  })

  //axios的拦截器
  instance.interceptors.request.use(config => {
    //成功时进入
    console.log(config);
    //注意拦截完成处理后，要放行，不然外部就无法获取数据
    return config
  }, err => {
    //失败时进入
    console.log(err);
    return err
  })


  return instance(config)
}
```









#### 拦截响应

拦截请求通过interceptors.response.use()，要求传递2个参数，都是函数

**比如我们对axios的封装添加一个响应拦截器**

```javascript
import axios from 'axios'


export function request(config) {
  //创建axios实例
  const instance = axios.create({
    baseURL: "http://123.207.32.32:8000",
    timeout: 5000
  })



  //响应拦截
  instance.interceptors.response.use(res => {
        //成功时进入
    console.log(res);
    return res
  }, err => {
        //失败时进入
    console.log(err);
    return err
  })




  return instance(config)
}

```


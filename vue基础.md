# 渐进式框架

Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**

渐进式意味着你可以将vue作为你应用的一部分嵌入其中 ，作为项目的一部分，比如可以一部分用jquery，一部分用vue

# 安装方式

### 一、CDN引入

```html
//开发环境版本，包含了有帮助的命令行警告
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
//生产环境版本，优化了尺寸和速度
<script src="https://cdn.jsdelive.net/npm/vue"></script>
```

### 二、下载引入

```
开发环境	https://vuejs.org/js/vue.js
生产环境	https://vuejs.org/js/vue.min.js
```

### 三、npm安装

# 编程范式

原生js的编程范式：命令式编程



vue的编程范式，声明式编程

# 基础代码格式规范

```javascript
<body>
    <div class="app">
        <h3>当前计数:{{counter}}</h3>
        <button @click="add">+</button>
        <button @click="sub">-</button>
    </div>

<script src="vue.js"></script>
<script>
    const app = new Vue({
        el:'.app',
        data:{
            counter:0
        },
        methods:{
            add:function(){
                this.counter++;
            },
            sub:function(){
                this.counter--;
            }
        }
    })
</script>
```

### 基础属性

创建vue对象的时候，传入了一些options：{}

**el属性**：对象挂载

**data属性**：存储数据

​	这些数据可以是我们直接定义出来的，比如上面

​	也可以来自网络，或者从服务器加载的

**methods属性**:定义方法

**@click**：监听事件，执行methods里面的方法

# --------------------------------

# 插值操作

## 静态插入

### v-once

只渲染元素和组件一次，随后的渲染，使用了此指令的元素/组件及其所有的子节点，都会当作静态内容并跳过

### v-for	

迭代普通数组

```
data:{
      movies:[1,2,3,4,5,6]
}
<li v-for='item in movies'>{{item}}</li>
```

### v-html

将字符串解析为html标签

```
url：“<a>百度一下</a>”
<h2 v-html='url'></h2>
```

### v-pre

原封不动的展示，不做解析

```
mes:'你好'
<p v-pre>{{mes}}</p>
输出为：{{mes}}
```

### 

## 动态绑定

### v-bind

 这样src才是动态绑定，不然{{imgurl}}和'imgurl'是不识别的

```
<img v-bind:src = imgurl alt="">

imgurl:'https://865465adadd'

语法糖写法

<img :src = imgurl alt="">

imgurl:'https://865465adadd'
```



### v-bind动态操作class

**vue中实现添加和删除类名的操作**

```html
<h1 :class=‘getClass()’></h1>
//普通class和动态class可以共存，不会覆盖
<button v-on:click='btnClick()'></button>
data:{
    isActive:true;
    isline:true;
}
methods:{
    btnClick:function(){
        this.isActive = !this.isActive
    }
    getClass:function(){
        return {active:this.isActive,line:this.isline}
    }
}
```

### v-bind动态绑定style



**对象语法：**

```html
    <div id="app">
        <!-- <h2 :style='{key属性名：value属性值}'>{{message}}</h2> -->
        <h2 :style="{fontSize:fontSize,color:color}">{{message}}</h2>
    </div>
    <script src="../vue.js"></script>
    <script>
        const app = new Vue({
            el:'#app',
            data:{
                message:'你好',
                fontSize:'50px',
                color:'red',
            }
        })
    </script>
```

**数组语法：**

```html
<body>
    <div id="app">
        <!-- <h2 :style='{key属性名：value属性值}'>{{message}}</h2> -->
        <h2 :style=[baseStyle]>{{message}}</h2>
    </div>
    <!-- 数组语法 -->
    <script src="../vue.js"></script>
    <script>
        const app = new Vue({
            el:'#app',
            data:{
                message:'你好',
                baseStyle:{color:"red",fontSize:"50px"}
            },
        })
    </script>
</body>
```



# 计算属性操作

又多了一个基础属性computed：存储计算属性的方法，引用时不需要加小括号

```html
<body>
    <div id="app">
        <h2>{{fullName}}</h2>
    </div>
    <script src='../vue.js'></script>
    <script>
        const app = new Vue({
            el: '#app', //绑定
            data: { //属性
                fName : "kode",
                lName : "Bryant"
            },
            computed: { //计算属性
                fullName:{
                    set:function(){

                    },
                    get:function(){
                        return this.fName + ' ' + this.lName
                    }
                }
            },
            methods: { //方法
    
            },
        })
    </script>
</body>
```

**一般情况下不用写set方法，所以可以直接简写**

```html
            computed: { //计算属性
                fullName:function(){
                        return this.fName + ' ' + this.lName
                    }
            },
```



# -----------------------------------

# 事件监听

### v-on

**基本使用**

```
<button v-on:click="add()">+</button>
//绑定methods中的方法
语法糖写法：
<button @click="add()">+</button>

```

**参数传递**

 传递浏览器对象event要加上$

```
<button @click="add(abc,$event)">+</button>

methodds:{
	add(abc,event){
		console.log(abc)
	}
}
```



### v-on修饰符

@click.stop = 'add()'  	阻止冒泡

@click.prevent= 'add()'  阻止默认行为

@keyup.key值= 'add()'   监听键盘点击

@click.once= 'add()'  只触发一次

# -----------------------------------

# 条件判断

不常用，这种判断不建议写在标签里面

### 	v-if

 	v-if等于true才进行渲染，true或false可以绑定方法进行判断后来返回

```html
<body>
    <div id="app">
        <h2 v-if="false">{{message}}</h2>
    </div>
    <script src='../vue.js'></script>
    <script>
        const app = new Vue({
            el: '#app', //绑定
            data: { //属性
                message : "Nihoa",
            },
        })
    </script>
</body>
```



### v-else

当v-if 为false的时候 执行，一般和v-if配合使用

这里打印的是123

```html
<body>
    <div id="app">
        <h2 v-if="false">{{message}}</h2>
        <h2 v-else>123</h2>
    </div>
    <script src='../vue.js'></script>
    <script>
        const app = new Vue({
            el: '#app', //绑定
            data: { //属性
                message : "Nihoa",
            },
        })
    </script>
</body>
```

### v-else-if

在v-if和v-else之间使用，进行多次分支判断





### v-show

用法与v-if类似，只是为false时的隐藏方式不同

v-if是直接删除html元素

v-show是添加一个display:none 的行内样式

### v-if和v-show的选择

需要在显示隐藏之间频繁切换时，用v-show

只有一次切换时使用v-if

# -----------------------------------

# 遍历

### v-for遍历数组	

​	需要获得下标，在前面加个括号，再添加一个index

再后面加上一个key = item，可以使得内部性能更高

```html
<body>
    <div id="app">
        <ul>
            <li v-for="(item,index) in names" :key = "item">{{index}},{{item}}</li>
        </ul>
    </div>
    <script src='../vue.js'></script>
    <script>
        const app = new Vue({
            el: '#app', //绑定
            data: { //属性
                names:[123,1321,4545,7986,25]
            },
        })
    </script>
</body>
```

### v-for遍历对象

可以同时获取key和value，不加括号只有一个值的话，获取的是value

```html
<body>
    <div id="app">
        <ul>
            <li v-for='(value,key) in info'>{{value}}--{{key}}</li>
        </ul>
    </div>
    <script src='../vue.js'></script>
    <script>
        const app = new Vue({
            el: '#app', //绑定
            data: { //属性
                info: {
                    name: 'lwy',
                    age: 18,
                    height: 18
                }
            },
        })
    </script>
</body>
```



### 哪些数组方法是响应式的

并不是通过任何方法修改数组都是响应式的，随着数据更而改更改页面的。

push() 添加元素到末尾 list.push('aaa','bbb')

pop（）删除最后一个元素 list.pop()

shift（）删除第一个元素 list.shift()

unshift（）添加元素到开头 list.unshift('aaa','bbb')

splice（）

sort（）排序

reverse（）反转





# -----------------------------------



# 过滤器

又多了一个基础属性 

filters  //过滤器

```vue
const app = new Vue({
    el: '#app', //绑定
    data: { //属性

    },
    computed: { //计算属性

    },
    methods: { //方法

    },
    filters:{//过滤器
      showPrice(price){   
        return '￥'+price.toFixed(2)
      }
    }
  })

语法： <td>{{item.price | showPrice}}</td>
showPrice方法过滤item.price
```



# 调用方法时的参数问题

没有参数时，括号可以省略，但是会默认传递一个event

有参数时（abc，event），需要手动传递event，通过$event拿到



# -----------------------------------



# 绑定表单

### v-model双向绑定

 

```html
<body>
  <div id="app">
    <input type="text" name="" id="" v-model="message">
  </div>
  <script src='../vue.js'></script>
  <script>
    const app = new Vue({
      el: '#app', //绑定
      data: { //属性
        message:"你好啊"
      },
    })
  </script>
</body>
```

input通过v-model绑定了data里面的变量，input的值发生变化时，message同时改变

而修改message的值，input框的内容也会更改，这就是一个简单的双向绑定

### v-model原理

v-model其实是一个语法糖，他的背后本质上是包含2个操作

1.v-bind绑定一个value

2.v-on绑定一个input事件

```html
<input type="text" v-model="message">
等同于
<input type="text" :value="message" @input="message"=$event.target.value>
```

### v-model单选框应用

 

```html
<body>
  <div id="app">
    <label for="male">
      <input type="radio" id="male" value="男" v-model="sex">男
    </label>
    <label for="female">
      <input type="radio" id="female" value="女" v-model="sex">女
    </label>
    <h2>{{sex}}</h2>
  </div>
  <script src='../vue.js'></script>
  <script>
    const app = new Vue({
      el: '#app', 
      data: { 
        sex:"男"
      },
    })
  </script>
</body>
```



### v-model多选框应用

```html
<body>
  <div id="app">
    <!-- 一个单选框 -->
    <!-- <label for="consent">
      <input type="checkbox" id="consent" v-model="ifage">同意协议
    </label>
    <button :disabled="!ifage">123</button>
    <h2>{{ifage}}</h2> -->

    <!-- 多选框 -->
    <input type="checkbox" value="篮球" v-model="hobbies">篮球
    <input type="checkbox" value="足球" v-model="hobbies">足球
    <input type="checkbox" value="电脑" v-model="hobbies">电脑
    <h2>{{hobbies}}</h2>
  </div>
  <script src='../vue.js'></script>
  <script>
    const app = new Vue({
      el: '#app', 
      data: { 
        // ifage: false,
        hobbies:[]
      },
    })
  </script>
</body>
```





### 值绑定

表单的默认值不要写死，从服务器动态获取，就是v-bind动态的给value赋值而已

```html
<body>
  <div id="app">
    <label v-for="item in orighin" :for="item">
      <input type="checkbox" :value='item' :id="item" v-model='hobbies'>{{item}}
    </label>
    <h2>{{hobbies}}</h2>
  </div>
  <script src='../vue.js'></script>
  <script>
    const app = new Vue({
      el: '#app', 
      data: { 
        hobbies:[],
        orighin:['篮球','足球','兵乓球','台球']
      },
    })
  </script>
</body>
```







# v-model修饰符

### v-model.lazy

默认情况下数据发生改变，data中的数据就会立即改变

lazy修饰符可以让数据在失去焦点或者回车时才更新



### v-model.number

v-model默认输入的是字母还是数字，都会被当成字符串处理

添加.number可以让绑定的数据为number类型



### v-model.trim

如果输入的内容首位有很多空格，我们可以直接用trim修饰符去掉





# ----------------------------------------------------------------------

# 组件化开发

### 什么是组件

组件 (Component) 是 Vue.js 最强大的功能之一。组件可以扩展 HTML 元素，封装可重用的代码。在较高层面上，组件是自定义元素，Vue.js 的编译器为它添加特殊功能。

### 组件对象的类型

子组件对象的类型是VueComponent类型

父组件类型是一个vue实例

### 一，创建组件构造器对象

通过vue的extend()方法

 模板属性template，传入我们自定义的组件模板

```html
<script>
    // 1.创建组件构造器
    const Comp = Vue.extend({
      // 模板属性template
      template: `  
      <div>
        <h2>我是标题</h2>
      </div>`
    })
  </script>
```



### 二，注册组件

使用vue的component方法，第一个参数是你这个组件的名字，第二个参数是你构造器的名字

```
Vue.component('my-cpn', comp)
```



### 三，使用组件

直接使用组件名字的标签就可以调用

必须放在vue的实例标签才能使用

```
<my-cpn></my-cpn>
```





# 全局组件和局部组件



### 全局组件的注册

在script标签内部，构造器下面注册

全局组件在任何vue实例标签下都可以使用

```
Vue.component('my-cpn', comp)
```



### 局部组件的注册

局部组件在单独的vue下面注册，只可以在当前vue实例使用

   

**用到一个新的属性  components**

```html
<body>
  <div id="app">
    <my-cpn></my-cpn>
  </div>
  <script src='vue.js'></script>
  <script>
    // 1.创建组件构造器
    const comp = Vue.extend({
      // 模板属性template
      template: `  
        <div>
          <h2>我是标题</h2>
          <p>我是内容</p>
          <p>我也是内容</p>  
        </div>`
    })


    const app = new Vue({
      el: '#app', 
	  components:{
          //key为使用时的标签名，value为构造器的名字
          cpn:comp
      }
    })
  </script>
</body>
```





# 父组件和子组件

构造器内部 也可以声明一个components属性用来注册，但是在这里注册的，作用域也只在内部

一般是在父组件下面注册它的子组件。如果子组件也想要在父组件外面使用，需要在根组件vue实例下面重新注册一次



而父组件则需要在根组件 vue实例下面进行注册使用

```html
<body>
  <div id="app">
    <cpn2></cpn2>
  </div>
  <script src='vue.js'></script>
  <script>
    const cpnC1 = Vue.extend({
      template: `  
        <div>
          <h2>我是标题</h2>
          <p>我是内容</p>
          <p>我也是内容</p>  
        </div>`
    })
    const cpnC2 = Vue.extend({
      template: `  
        <div>
          <h2>我是标题2</h2>
          <p>我是内容2</p>
          <cpn1></cpn1>
          <p>我也是内容2</p>  
        </div>`,
        components:{
          cpn1:cpnC1
        }
    })

    const app = new Vue({
      el: '#app', //绑定
      components:{ //注册组件
        // cpn1:cpnC1,
        cpn2:cpnC2,
      }
    })
  </script>
</body>
```



### 注册组件的语法糖

省去了调用extend（）的步骤，直接用一个对象来代替

但是底层仍然是通过extend方法实现的，这只是一个语法糖

### 全局注册

```html
<body>
  <div id="app">
    <cpn1></cpn1>
  </div>
  <script src='vue.js'></script> 
  <script>
    Vue.component('cpn1', {
      template: `
      <div>
        <h2>123123</h2>
      </div>
    `
    })
    const app = new Vue({

    })
  </script>
</body>
```

### 局部注册

```html
<body>
  <div id="app">
    <cpn1></cpn1>
  </div>
  <script src='vue.js'></script>
  <script>
    const app = new Vue({
      el: '#app', //绑定
      components: { //注册组件
        'cpn1': {
          template: `
            <div>
              <h2>123123</h2>
            </div>
          `
        }
      }
    })
  </script>
</body>
```



# 模板的分离写法

通过template标签定义模板，然后注册的时候直接绑定这个标签就可以

```html
<body>
  <div id="app">
    <cpn></cpn>
  </div>
    
  <template id="cpn">
    <div>
      <h2>我是标题</h2>
    </div>
  </template>
    
  <script src='vue.js'></script>
  <script>
    Vue.component('cpn',{
      template:'#cpn'
    })
    const app = new Vue({
      el: '#app', //绑定
    })
  </script>
</body>
```







# 组件中的数据存放

组件是一个单独功能模块的封装：

​			这个模块有自己的HTML模板，也应该有属性自己的数据data，也可以有methods等属性

​			**可以把组件看作一个单独Vue的实例来使用**

**注意：**

组件中data是一个函数，而且必须有return返回，不能是一个对象

```html
<script>
      <template id="cpn">
    	<div>
      		<h2>{{title}}</h2>
    	</div>
      </template>
	 Vue.component('cpn',{
      template:'#cpn',
      components:{

      },
      data(){
        return{
          title:"你好"
        }
      },
      methods:{
          
      }
    })
</script>
```

# ---------------------------------

# 父子组件的通信

### 父传子

1.通过子组件的props属性，接收父组件标签传递过来的值,

2.props属性接收数据时还可以定义各种属性进行限制

**type定义接收值的类型**，(string,number,boolean,array,object,date,function,symbol)

​		**注意:**type类型是对象或者数组时，默认值必须是一个函数（有return返回），可以跟多种类型，

​					用数组包起来

```
type:[object,array]
default(){
	return{measg:"你好"}
}
```

**default定义默认值**（未获得数据显示默认值）

**required：true**（一个布尔值，表示使用这个组件时必须传递这个值，不然就会报错）

```html
<body>
  <div id="app">
    <cpn v-bind:cmovies="movies" :ms='mes'></cpn>
  </div>

  <template id="cpn">
    <div>
      <ul>
        <li v-for="itme in cmovies">{{itme}}</li>
      </ul>
      <p>{{ms}}</p>
    </div>
  </template>

  <script src='vue.js'></script>
  <script>
    // 父传子 props
    const cpn = {
      template: "#cpn",
      props: {
        cmovies: Array,
        ms: {
            type:String,
            default:'123'
        },
        required：true
      },
    }

    const app = new Vue({
      el: '#app', //绑定
      data: { //属性
        mes: "你好",
        movies: [123, 3432, 3543, 34645, 1213]
      },
      components: { //注册组件
        'cpn': cpn
      }
    })
  </script>
</body>
```

### 值传递的驼峰命名问题

如果传递的值为驼峰命名，那么在根组件的子组件标签内部，得进行转义

```html
<cpn :cMovies="cMovies" :aMs='aMs'></cpn>
↓
<cpn :c-movies="cMovies" :a-ms='aMs'></cpn>
```



### 子传父

通过自定义事件传递

1.先在子组件中获取数据，然后在子组件methods方法中通过**this.$emit('自定义事件名'，item)**,创建一个自定义事件

第二个参数是你要传递的数据（先在子组件获取好）

```
      methods:{
        addClick(item){
          this.$emit('itemClick',item)
        }
      }
```



2.然后在父组件模板的 子组件标签上面进行接收事件

​	并且为它绑定父组件methods中的方法

​	然后在这个方法里面对数据进行处理

```
  <div id="app">
    <cpn @itemClick="cpnClick"></cpn>
  </div>
```

**注意：**

​		自定义对象传递的数据，会自动被定义的函数接收传递，进行默认传递到methods里面

​		平常会自动传递一个event浏览器对象，但是在这里没有这个对象，所以默认传递子组件中this.$emit('itemClick',item)给的item数据

​		所以这里不写<cpn @itemClick="cpnClick(item)"></cpn>

**案例：**

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>

<body>
  <!-- 父组件模板 -->
  <div id="app">
    <cpn @item_click="cpn_click"></cpn>
  </div>
  <!-- 子组件模板 -->
  <template id="cpn">
    <div>
     <button v-for="item in categories" @click='addClick(item)'>
       {{item.name}}
     </button>
    </div>
  </template>
  <script src='vue.js'></script>
  <script>
    // 子组件
    const cpn = {
      template: "#cpn",
      data(){
        return{
          categories:[
            {id:'aaa',name:"热门推荐"},
            {id:'bbb',name:"手机数码"},
            {id:'ccc',name:"家用电器"},
            {id:'ddd',name:"电脑办公"},
          ]
        }
      },
      methods:{
        addClick(item){
          this.$emit('item_click',item)
        }
      }
    }

    //父组件
    const app = new Vue({
      el: '#app', //绑定
      components: { //注册组件
        'cpn': cpn
      },
      methods:{
        cpn_click(item){
          console.log(item);
        }
      }
    })
  </script>
</body>

</html>
```



# --------------------------------

# 父子组件的直接访问

### 父组件访问子组件

### $children操作所有组件

父组件的方法中写,操作父组件的第几个子标签，索引就写几

 this.$children[0].message()   //获取方法

 this.$children[0].name   //获取属性

### $refs操作单个组件

1.先给父组件下的子组件添加ref标识，可以理解为id,**ref的值会作为key**

```html
<div id="app">
	<cpn ref="cpn"></cpn>
    <button @click='addclick'></button>
</div>
```

2.在父组件的方法中就可以直接通过$ref.标识来获取子组件的数据了

```html
      methods: { //方法
        btnclick(){
			console.log(this.$ref.cpn)
			//获取属性
			console.log(this.$ref.cpn.name)
			//获取方法
			console.log(this.$ref.cpn.add())
        } 
      },
```

### 子组件访问父组件

$parent

### 子组件访问根组件

$root



# ---------------------------------

# 组件插槽slot

### 作用

组件插槽可以让组件具有更高的扩展性,

抽取共性，保留不同：为了避免多次的封装，把重复的东西封装，不一样的预留为插槽

### 基本使用

```html
  <div id="app">
    <cpn><button>按钮</button></cpn>
    <cpn></cpn>
    <cpn></cpn>
    <cpn></cpn>
  </div>
  <template id="cpn">
    <div>
      <h1>我是组件</h1>
      <slot></slot>
    </div>
  </template>
```

在子组件添加一个slot标签插槽，在父组件使用的时候就可以进行替换

这里把一个子组件的插槽替换为了一个button按钮

### 插槽默认值

  

```html
  <div id="app">
      <cpn><h2></h2></cpn>
    <cpn></cpn>
    <cpn></cpn>
    <cpn></cpn>
  </div>
  <template id="cpn">
    <div>
      <h1>我是组件</h1>
        <slot><button>按钮</button></slot>
    </div>
  </template>
```

可以给插槽一个默认值，如果不想进行修改，默认就显示插槽里面的东西

这里只有第一个子组件进行了修改，其余的都是默认值一个按钮

### 多个修改值

如果修改值有多个，而只有一个插槽，会全部放到这一个插槽里面

------



# 具名插槽

### 基本使用

有多个插槽，而只需要改变其中某一个时，就要用到具名插槽，给插槽起名字，通过name属性

使用时，通过slot属性来指定名字

```html
  <div id="app">
    <cpn>
      <span slot="left">我把左插槽替换了</span>
      <button slot="center">我把中插槽替换了</button>
      <p slot="right">我把右插槽替换了</p>
    </cpn>
  </div>
  <template id="cpn">
    <div>
      <slot name='left'><span>左</span></slot>
      <slot name="center"><span>中</span></slot>
      <slot name='right'><span>右</span></slot>
    </div>
  </template>
```

 

------





# 作用域插槽

### 编译作用域的概念



使用变量时，它会看这个变量是在哪个里面使用的，而不是看这个变量是在哪个里面声明的



在vue实例和组件有相同的变量，在vue实例中使用时，会去vue实例中寻找。相反，在组件中使用时，会去组件中寻找

### 作用域插槽基本使用



**目的：父组件替换子组件插槽的标签，但是内容由子组件提供**

简单理解：（父组件对子组件的数据展示进行修改）

slot加上name是具名函数，这里有个新属性 :data=‘pLanguages’

**data属性 ：**   随意，但是父组件要通过这个名字来取数据

**pLanguages：** 就是你要传递的数据,存储到data中

```html
      <slot :data="pLanguages">
        <ul>
          <li v-for="item in pLanguages">{{item}}</li>
        </ul>
      </slot>
```

**父组件中：**

2.5以前需要用template模板来接收，2.5以后不需要

这里通过 slot-scope="slot" 来定义接收的标签

然后通过slot.data就可以使用子组件中的数据了

```html
  <div id="app">
    <cpn>
      <div slot-scope="slot">
        <span v-for="item in slot.data">{{item}} --- </span>
      </div>
    </cpn>
  </div>
```

### 案例：

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>

<body>
  <div id="app">
    <cpn></cpn>
    <cpn>
      <!-- 目的是获取子组件的pLanguages -->
      <div slot-scope="slot">
        <span v-for="item in slot.data">{{item}} --- </span>
      </div>
    </cpn>

  </div>
  <template id="cpn">
    <div>
      <slot :data="pLanguages">
        <ul>
          <li v-for="item in pLanguages">{{item}}</li>
        </ul>
      </slot>
    </div>
  </template>
  <script src='../vue.js'></script>
  <script>
    const app = new Vue({
      el: '#app', //绑定
      data: { //属性
        message: "你好"
      },
      computed: { //计算属性

      },
      methods: { //方法

      },
      filters: { //过滤器

      },
      components: { //注册组件
        cpn: {
          template: "#cpn",
          data() {
            return {
              pLanguages: ["python", 'java', 'javascript', 'c++', 'c#', 'go']
            }
          }
        }
      }
    })
  </script>
</body>

</html>
```

# ---------------------------------------------------------------------

# 模块化开发

常见的模块化规范

CommonJS，AMD，CMD，ES6的Modeules



### 模块化文件夹创建

项目文件夹创建

dist 					 webpack打包后的文件放到这里（以后传递到服务器发布）

src文件夹 			放js文件等源码等文件

在html主页面直接引用dist中打包后的一个主js文件





### CommonJs规范的导出方式

```javascript
function add(num1, num2) {   
  return num1 + num2
}
function mul(num1, num2) {
  return num1 * num2
}

module.exports = {
  add,
  mul
}
```

### CommonJS规范的引入方式

```javascript
const {add,mul} = require('./mathUtils')  //src中


console.log(add(20,30));
console.log(mul(20,30));
```

### ES6规范导出方式

```javascript
export const name = "why"
export const age = 18
export const height = 1.88
```

### ES6规范引入方式

info是文件名

```javascript
import {name, age , height} from "./info"
console.log(name);
console.log(age);
console.log(height);
```



# -----------------------------------





# Webpack

### 什么是Webpack

webpack是一款模块加载器兼打包工具，它能把各种资源，例如JS（含JSX）、coffee、样式（含less/sass）、图片等都作为模块来使用和处理。 webpack 的核心是 依赖分析,把依赖分析出来了，其他都是细枝末节了



### 安装

webpack首先需要安装Node.js,Node.js自带了软件包管理工具npm



安装最新版本(不建议)

```bash
npm install --save-dev webpack
```

安装特定版本 webpack（比如 3.x.x）：

```bash
npm install -g webpack3.5.5
```

如果你使用 webpack 4+ 版本，你还需要安装 CLI。

```bash
npm install --save-dev webpack-cli
```

以下的 NPM 安装方式，将使 `webpack` 在全局环境下可用：

```bash
npm install --global webpack
```

查看版本

```
webpack -v
```





### 基本使用

**1.对模块化项目的src文件夹打包到dist文件夹**

cmd中cd命令进入项目根目录，然后运行命令

```bash
webpack ./src/index.js ./dist/bundle.js
```

**命令解读：**

把src中的根文件index.js文件进行打包，打包到dist，在dist下创建一个新的bundle.js文件

**注意：**

1.这里只打包一个主入口文件，因为其余的文件都与这个文件有依赖关系。webpack会自动处理各个模块之间的依赖关系

2.bundle.js文件，是webpack处理文件依赖后生成的一个js文件，直接在index.html引入即可

2.修改代码后要重新打包





### webpack的配置

上面写了一个打包的命令，这里可以对它进行优化,让webpack自动寻找入口和出口

**1.根目录下创建一个webpack.config.js文件，名字暂时固定**

**语法：**

```javascript
const path = require('path')

module.exports = {
  entry:"./src/index.js",   //入口
  output:{                  //出口
    path:"./dist",          //绝对路径(node语法动态获取)
    filename:"bundle.js"    //文件名
  }
}
```

**注意：**

node语法动态获取绝对路径，需要node中的path包的支持

1.根目录下执行,对npm进行初始化

```
npm init
```

2.然后会提示package name输入名字，随便写（比如linkwebpack）

3.一直回车到 entry point:（webpack.config.js） 叫你选择一个入口文件，随便写一个adb.js，这里暂时用不到，然后一路回车

4.最后会提示是否ok直接回车完成



**这样项目下面多了一个package.json文件，这个文件会告诉你当前项目的一些信息**

**packge.json: 通过npm init生成，npm包管理文件，要使用node的一些东西，都要有这个文件**

打开看一下

```json
{
  "name": "meetwebpack",  // 刚刚设置的项目名字
  "version": "1.0.0",	  //版本号
  "description": "",	  //描述，刚刚没有写
  "main": "abc.js",		  //入口文件
  "scripts": {			  //脚本，npm输入test，会执行后面的
    "test": "echo \"Error: no test specified\" && exit 1"
  },	
  "author": "",		//作者
  "license": "ISC"  //协议（开源需要，不开源不需要）
}

```

**完成后，完善webpack.config.js文件的代码**

```javascript
const path = require('path')

module.exports = {
  entry:"./src/index.js",   //入口
  output:{                  //出口
    path:path.resolve(__dirname,"dist"), //动态的绝对路径
    filename:"bundle.js"    //文件名
  }
}
```

**1.先把node中全局的一个path包导出赋值**

**2.调用path的resolve()函数，作用是对2个参数的路径进行拼接**

**3.node中的全局变量__dirname,这个变量保存的就是当前文件所在的路径**

**4.然后把后面的dist拼接到当前路径，这样它就是一个绝对路径了**



最后还需要做一层映射，把webpack命令映射到package.json文件的脚本中

```javascript
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack"
  },
```

这样npm run build命令就会替换webpack命令

这样在根目录执行npm run build 命令就可以直接打包项目了

**这样替换映射命令有什么好处？**

因为在终端输入都是在全局找，而我们映射后，它优先在本地寻找，**而我们开发时最好使用本地安装**

**本地安装**

版本号是自己的webpack版本号（--save-dev是开发时依赖，项目打包后不需要继续使用）

```
npm install webpack@3.5.5 --save-dev
```

安装完成后package.json多了一段代码

```javascript
  "devDependencies": {		//开发时依赖，项目打包后不需要继续使用
    "webpack": "^3.5.5"
  }
```

我们项目下面还多了一个node_modules，直接把全部库下载到了本地





# 核心一：loader

### loader是什么

loader是webpack中的一个核心概念，开发不仅仅需要处理js文件，还要ES6转ES5，TypeScript转ES5，将scss，less转css，将.jsx,.vue等转成js等等

对于webpack本身的能力来说，对于这些转化是不支持的，

那怎么办那，给webpack扩展对应的loader就可以了

### **一，通过npm安装需要使用的loader**

##### css文件需要的loader

在src中，创建一个css文件夹，放需要的css文件，

**注意：** 必须在入口文件index.js进行引用，不然没有任何依赖关系

```javascript
//引用css文件
require('./css/normal.css')
```

处理css文件要用2个loader。项目根目录下，同样安装的是开发时依赖

```bash
npm install --save-dev css-loader
```

```bash
npm install style-loader --save-dev
```





##### less文件需要的loader



**注意：** 必须在入口文件index.js进行引用，不然没有任何依赖关系

```javascript
//依赖less文件
require("./css/special.less")
```

处理css文件要用1个loader。项目根目录下，同样安装的是开发时依赖

```bash
npm install --save-dev less-loader less
```

注意：less的作用是对css转换，所以css的2个loader也要安装





##### 图片所需要的loader

因为图片是在css文件里面写的，所以依赖css文件就可以了



处理图片要用1个loader。项目根目录下，同样安装的是开发时依赖

```bash
npm install --save-dev url-loader
```









##### ES6语法处理

如果webpack打包的js文件，里面的ES6语法没有转化为ES5。那么一些还不支持es6的浏览器可以无法运行我们的代码

所以我们希望将es6代码转化为es5，**那么就需要用到babel**

**安装：**

```bash
npm install --save-dev babel-loader@7 babel-core babel-preset-es2015
```

























### **二，在webpack.config.js中的module关键字进行配置**

##### css文件的loader的配置

安装完成后，在webpack.config.js配置loader模组。

```javascript
  module: {
    rules: [  //rules规则
      {
        test:/\.css$/,    //匹配什么样的文件
        use:["style-loader",'css-loader']
      }
    ]
  }
```

style-loader负责将样式添加到DOM中，css-loader负责将css文件加载

使用多个loader时，是从右向左的顺序来处理的

**完成后重新打包运行，就可以看到效果了**





##### less文件的loader配置

rules是一个数组，所以写在下面，不用重新写一个module

```javascript
  module: {
    rules: [  //rules规则
      {
        test:/\.css$/,
        use:["style-loader",'css-loader']
      },
      {
        test:/\.less$/,
        use:["style-loader",'css-loader','less-loader']
      }
    ]
  }
```



less主要的目的是转换css代码，所以css的2个loader也要一起配置，注意顺序

**完成后重新打包运行，就可以看到效果了**





##### 图片loader的配置

```javascript
  module: {
    rules: [  //rules规则
      {
        test:/\.(png|jpg|gif|jpeg)$/,
        use:[
          {
            loader:"url-loader",
            options:{
                //当加载的图片，小于limit时，会将图片编译成base64字符串形式
              limit:10240000000
            }
          }
        ]
      }
    ]
  }
```

**完成后重新打包运行，就可以看到效果了**



##### 配置ES6语法处理

```javascript
  module: {
    rules: [  //rules规则
      {
        test: /\.js$/,
        //exclude 排除
        //include 包含
        exclude: /(node_modules | bower_components)/,
        use: {
          loader: "babel-loader",
          options: {
            presets: ["es2015"]
          }
        }
      }
    ]
  }
```

# 核心二：plugin

**什么是plugin**

plugin是插件的意思，通常是对于某个现有的架构进行扩展，比如打包优化，文件压缩等

**和loader的区别**

loader主要用于转化某些类型的模块，他是一个转换器

plugin是插件，他是对webpack本身的扩展，是一个扩展器

**使用步骤**

于loader类似，通过npm安装需要的plugin。在webpack.config.js的plugin中配置



### 打包html的plugin

index.html是存在于根目录下的。在真实发布的时候，发布的是dist文件夹的内容，但是dist文件夹中没有index.html。所以我们要将index.html打包到dist文件夹中

HtmlWebpackPlugin插件可以自动生成一个index.html文件，将打包的js文件，自动通过script标签插入到body中

**安装**

```bash
npm install html-webpack-plugin --save-dev
```

**配置**

webpack.config.js

先导入安装好的插件

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin')
```

module.exports 下新加属性plugins：{}

```javascript
module.exports = {
  plugins:[
    new HtmlWebpackPlugin({
      template:"index.html"
    })
  ]
}
```

里面的template模板，是要你让它根据哪个模板来生成文件

并且原来的html页面中的引入入口js文件的代码也不需要了，会自动生成，只需要一个根组件的标签





# 

# 

# -----------------------------------

# 

# webapck配置Vue.js(重点)

# 



原来我们使用vue是将源码下载到本地，使用script标签引入，但是这样不符合模块化的思想

、

后续项目中，我们会使用vue开发，而且会以特殊的文件来组织vue的组件

所以，下面学习如何在webpack环境中集成vue.js



**安装:**

因为我们后续在实际项目中也会使用vue，所以是运行时依赖--save

```bash
npm install vue --save
```

**安装完成后，**

在webpack.config.js 进行配置.module.exports 多了一个新属性resolve



这里的配置是为vue更换版本，默认是runtime-only版本，这个版本不会解析template

更换为runtime-compiler，因为有compiler可以解析template

```javascript
module.exports = {
  resolve:{
    alias:{
      "vue$":"vue/dist/vue.esm.js"
    }
  }
}
```

然后就可以在主入口js文件，index.js导入vue使用

```javascript
import Vue from 'vue'

new Vue({  //这里的app是绑定index.html中的标签
  el:"#app",
  data:{
    message:"hello world"
  }
})
```





# vue的封装处理

在src目录下新建一个vue文件夹，存放vue文件，以后的vue代码直接写在vue文件中

模板，组件，样式完全分离

```vue
<template>
  <div>
    <h1 class="title">{{message}}</h1>
  </div>
</template>

<script>

export default{
  name:'App',
  data(){
    return{
      message:"hello world"
    }
  },
  methods:{

  }
}
</script>

<style scoped>
  .title{
    color: red
  }
</style>

```

然后在入口文件index.js使用

使用es6语法导入，在根组件注册使用

template的标签名，就是注册的子组件名

**多个vue文件的组件可以互相导入注册使用，语法一样**

```javascript
//使用vue进行开发
import Vue from 'vue'
import App from "./vue/App.vue"

const app = new Vue({
  el:"#app",
  template:"<App/>",
  components:{
    App
  }
})
```

而根组件只需要在html文件绑定一个标签即可

```html
<div id="app"></div>
```

# vue文件的loader

vue文件无法直接被webpack解析，如css文件也需要loader。

**安装vue-loader，vue-template-compiler**

```bash
npm install vue-loader vue-template-compiler --save-dev
```

在webpack.config.js配置,在module,rules下新增一个属性

```javascript
      {
        test:/\.vue$/,
        use:['vue-loader']
      }
```

如果vue-loader的版本过高，可能需要安装别的插件，可以在package.json修改版本后，**npm install全部重新安装插件**（建议13.0.0）

然后就可以打包运行了

## ------------------------------


































































































































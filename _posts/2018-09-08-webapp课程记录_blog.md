路由就是根据网址的不同返回不同的内容给用户

显示的是当前路由地址的、所对应的内容
<router-view/>

ES6 中键和值如果一样可以省略一部分内容

@代表 src 目录

reset.css 做到各种显示屏下面一样 border.css 做到 1px 的实现

npm install fastclick --save
安装快速点击的模块框

npm install stylus --save
安装快速开发样式的包

npm install stylus-loader --save

1rem =html font-size = 50px

因为设计师给的是 2 倍尺寸的图片，所以 header 量出来是 86px，现实应该写 43px= 0.86rem
因为 font-size 是 50px 所以直接写设计师给的 px 的 0.01 倍 rem 就可以了
就通过 font—size 简化了 rem 的计算

### 问题：为什么要用 rem？

display: flex

### 此处是让 input 框自己去撑开，给了 input 一个 flex:1? why

### 用 webpack 对代码进行简化

样式里面去引用样式要用@符号，样式里面引用 src 目录得在@前面加上~就可以直接引用 src 目录

## 使用 iconfont

### 快捷路径的使用，

build>webpack.base.conf.js 里面的 resolve,将 styles 变成快速路径的名字，因为修改了 dom 所以要重启服务

### 创建 git 分支，每增加一个功能

先线上新建一个 branch

再 git pull

git checkout index-swiper //转换到新的 brach 上面

git status

### 使用轮播功能呢

在 gitHub 上搜索 vue-awesome-swiper

npm install vue-awesome-swiper --save
npm install vue-awesome-swiper@2.6.7 --save

### 首页防抖屏，实现图片宽高比的自适应

也就是让就算图片没有加载出来，也是有东西在那里把界面撑开的
.wrapper
overflow hidden
width 100%
height 0
padding-bottom 26.66%
宽度是 100% 高度会相对于宽度撑开 26.66，保持宽高比,这个是图片的原始比例计算出来的
不能写在 height 里面，因为就不是相对于 wrapper 的宽度，而是父集元素的高度

#### 轮播格式

传入，告诉想要的 style
swiperOption: { pagination: '.swiper-pagination' }
loop: true
支持循环轮播

swiper-pagination 是传递给 swiper 来实现的，这个 class 并不在我们的组件里面，而是由 swiper 决定的，会受到局部组件的限制，swiper 也是我们自己引入进去的

```
.wrapper >>> .swiper-pagination-bullet-active
  background white !important
```

样式穿透，将样式强行传递给子组件 swiper

### 分支合并

在 index-swiper 上 add commit push 之后
git checkout master
git merge 'origin/index-swiper'
git push

### ？

heigth 0 之后内容有多少就撑开多少？

### 图标居中

.icon-img-content
display block
margin 0 auto
height 100%

### 图标轮播效果 加入 swiper 插件

拖上面图标可以动，拖下面图标动不了，因为那个 icons 的高度高于 swiper
swiper-container 自带 overflow hidden

不需要循环的变更，所以用 index 作为 key 值是 OK 的

mixins.styl
用于字多了出现。。。。。

Math.floor(index / 8);
向下取整，index=8 的时候是第 9 个数据，就会出现 1

## 双重数组取循环实现图标分页功能,二维数组

```
computed: {
pages: function() {
const pages = [];
this.iconList.forEach((item, index) => {
const page = Math.floor(index / 8);
if (!pages[page]) {
pages[page] = [];
}
pages[page].push(item);
});
return pages;
}
}
```

## min-width???

### 组件从 data 传值属性一定要加：变成 js 表达式

### Ajax 动态获取数据

使用 vue 的
axios 可以跨平台获取数据
在一个管理所有页面的去发送 ajax 数据请求是最好的，以防所有界面都需要 ajax 数据请求

```
npm install axios --save
```

### 数据接口访问

只有 static 的文件夹可以通过网站直接访问
把数据放到 static/mock/index.json 下面然后在.gitignore
里面忽略这个文件夹，从而这个文件夹就不会被提交到 git
由 webpack-dev-server 提供的服务
上线之前都要改成这种数据格式会比较好，
api/index.json
用代理进行转换
所以用 config/index.js 的 proxyTable 进行转换

### json 数据中

"ret": true,
服务器正确响应了你的请求，最后一个数据不要加逗号

### 首页父子组件传值

定义传值类型`city: String`，string 要大写

传值要点，首先 axios 要接受传值，然后父组件要通过属性的方式把值传给子组件！！！！
swiper 显示的不是第一张图片而是最后一张图片，是因为渲染的时候最开始的 array 是空数组，要使得刚开始就是第一项。要加上`v-if="list.length"`判断一下数组的长度要是空的话，就不显示 swiper

```
<swiper :options="swiperOption" v-if="list.length">
```

但是这样的逻辑属性看起来不是很优雅，所以建立一个 compute 属性
把 this.list.length 放到 computed 函数里面去 return 一下，`v-if="showSwiper"`

### 网页跳转

`<router-link >`进行网页跳转,自带颜色是背景色，所以记得更改颜色
to="/city" 某个已经在 index.js 里面进行定义过的 path 路径，然后这个路径对应的组件就会显示在界面上

把公用的 height 高度也可以放到 varibel.styl 里面从而使得每次更改高度就可以更改所有的高度

vue-cli 打包的时候会自动打包加上产商前缀所以不需要加上厂商前缀

### box-sizing border-box????之后才能写 padding 0 0.1rem？？？

### 伪元素 before after？？？？

## overflow hidden???

### betterScroll 使用

`npm install better-scroll --save`

### 对象循环最外层每一项自带 key 值，所以循环的时候 key 就是 key

### 兄弟组件传值，先传给父组件，父组件再发送给兄弟组件

scrollToElement 只能去到元素

### 为什么这个 let 添加的话 i 会变成字母？会使用的是对象的 key 值，然后再返回的话 key 变成 index

```
for (let i in this.cities) {
letters.push(i);
}
```

### :ref="item"？？？？

### ref???

### 节流？？？？

## vueX 实现页面之间数据传递，数据层框架

`npm install vuex --save`
没有异步操作，可以省略 actions 直接用 mutation，直接用 commit 方法从 dispatch 跳到 mutation

防止用户开启隐身模式

```
let defaultCity = '上海';
try {
  if (localStorage.city) {
    defaultCity = localStorage.city;
  }
} catch (e) {}
```

### try catch????

### 映射

```
 ...mapState(['city'])
```

把 store 的公用数据 city 映射到子组件中

...mapMutations(['changeCity'])
调用了这个就不用`this.$store.commit('changeCity', city);`
去调用 mutations 了

### </keep-alive> 在 router-view 两边加上

加载一次之后就把路由中的东西放在内存之中不用再加载
activated 生命周期函数改变缓存内容,
页面重新被显示 时候就会重新执行
加上一个临时缓冲变量实现首页代码性能最优化

### flex 布局？？

### swiper 自动刷新解决宽度计算的问题

```
 observeParents: true,
        observer: true
```

### 响应式？？？？？

### 全局事件的解绑

因为事件绑定到了 window 上面，
导致对一个组件的事件影响到了其他组件。
加上 deactivated 的生命周期钩子使得在局部组件里面终止 activate

### 递归组件：在组件的自身去调用自身

在传入的数组中加上 children，然后在自己里面去使用自己的组件，然后循环自己的 children 达到递归组件的作用

### 组件 name 值的作用

1. 递归组件用到
2. 在页面上对某个组件调整缓存的时候会用到
3. 在 vue 控制台里面可以看到组件的名字

每次进入从最上面开始展示：

```
scrollBehavior(to, from, savedPosition) {
    return { x: 0, y: 0 };
  }
```

### 前后端联调

在 config>index.js 的 dev 改 proxyTable
target 的地址要换成后端的地址

```
proxyTable: {
      '/api': {
        target: 'http://localhost:8080',
        pathRewrite: {
          '^/api': '/static/mock'
        }
      }
    }
    // 要和后端交互的时候，这个target就要改成后端的地址
      // '/api': {
      //   target: 'http://localhost:5000',
      //   changeOrigin: true
      // }v
```

target 的地址和端口都可以改

### 调试问题：真机测试

命令行输入`ifconfig`，找到`inet 10.10.62.0`,也就是机器在内网的地址，但是因为前端项目是 webpackdev-sever 启动的，它不支持通过 IP 访问，所以要更改默认设置
在 package.json 中的`"dev": "webpack-dev-server`后面加上`--host 0.0.0.0`

### 调试问题：解决安卓手机兼容问题

`npm install babel-polyfill --save`
会判断手机是否支持 promise，如果没有就会自动帮忙添加一些 es6 的特性

### 安卓手机调试问题 Bscroll 默认将点击事件阻止了

chrome 调试点击城市列表，选择城市无问题，但是在安卓手机上无法点击城市。查询资料发现是 better-scroll 导致的加一个 click:true 即可解决此问题。例如

this.scroll = new Bscroll(this.$refs.wrapper, {

      click: true

    })

### 打包上线

`npm run build`， 出现 dist 目录，将 dist 目录里面的东西放到后台的里面去就可以了
要是在后端选取一个文件夹进行运行，就在 config>index.js 的 build 下面的`assetsPublicPath: '/',`进行修改就可以了

### 异步加载

需要加载什么就加载什么的 js

### 箭头函数？？？？

### 异步加载

使用箭头函数在 index.js 了；里面进行组件的 import
在子组件里面也可以用这些方式进行小组件的 import，达到更搞笑的利用
至少 js 文件超过 1MB 的时候才去使用异步组件

### 后续学习

教程的边边角角
vue-router
vuex
服务器渲染可以延迟学习
搞明白之后学习一下 vue 的资源插件

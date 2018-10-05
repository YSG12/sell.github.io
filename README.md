

## 高仿饿了么点餐系统

### 体验地址
<a href="https://stavyan.github.io/vue-sell-stav/dist/index.html" target=_blank>在线演示地址</a>（请使用手机或者chrome开发者手机演示模式预览）

### 移动端演示
扫二维码在手机上查看效果更好

![手机预览](https://stavyan.github.io/vue-sell-stav/static/qrcode)

### 组件

- [x] 购物车
- [x] 购买物品小球飞入动画
- [x] 评价star组件
- [x] 商品添加、删除组件
- [x] 优惠图标组件
- [x] 目录、列表联动滚动
- [x] 评论的是否满意和内容筛选
- [x] 商品列表页面
- [x] 店铺评价页面
- [x] 商家介绍页面
- [x] 优惠活动页面
- [x] 商品详情页面

### 构建

vue有自己的脚手架构建工具vue-cli,使用起来非常方便，使用webpack来集成各种开发便捷工具，比如：

- 代码热更新，修改代码之后网页无刷新改变，对前端开发来说非常的方便
- PostCss，再也不用去管兼容性的问题了，只针对chrome写css代码，会自动编译生成支持多款浏览器的css代码
- Eslint，统一代码风格，规避低级错误，对于有代码洁癖的人来说是绝对的好东西，不过有些地方的代码校验有时候也挺麻烦的-.-
- bable，ES2015出来已经有一段时间了，但是不少浏览器还没有兼容ES6.有了bable，放心使用ES6语法，它会自动转义成ES5语法。
- Stylus，类似于SASS/SCSS，但是可以不写{}和“：”，使用起来还是很方便的
- ...

除此之外，vue-cli已经使用node配置了一套本地服务器和安装命令等，本地运行和打包只需要一个命令就可以搞定，非常的方便

### 开发

vue非常好的融合了react的组件化思想和angular的指令思想。
一个vue的组件将HTML、CSS、JS代码写在一个文件里面，这样既方便编写，也方便管理和修改

### Axios

vue2.x官方推荐的HTTP请求工具是axios。

使用方式都差不多，但需要注意的是：接口返回的res并不直接是返回的数据，而是经过axios本身处理过的json对象。真正的数据在res.data里：

```javascript
axios.get(url).then((res)=>{
  this.data = res.data
})
```

### Vuex

vue提供了一个数据管理工具vuex，有点类似于angular中factory和service，可以进行数据上的通信。
比如存储一些公共变量或者是不同组件间的数据处理等。

这个有一些高级用法在这里不细说，想要了解的可以去官方文档看，有中文版本。

```javascript
const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment(state) {
      state.count++
    }
  }
})
```

### 获取元素节点

vue2.x废除了v-el指令，所有的节点指令修改为ref，然后通过ref来获取元素节点，如

```html
<div ref="test">test</div>
...js code
this.$ref.test
```

### 组件间的通信

1. 如果是和子组件通信，则使用ref就可以实现，如：

```html
<test ref="test"></test>
...js code
this.$ref.test.add() //调用test子组件的add方法
```

2. 使用emit来发送广播

vue2提供了一套广播机制，即一边发送广播，一边接收广播来执行相应操作。使用方法如下：

比如想要给test组件发送一个“相加”广播:

```javascript
export default {
  method:{
  	click(){
  	  Vue.$emit('add',{}) //第二个参数可作为传递数据传送到监听端口，不需要则传空对象
  	}
  }
}
```

3. 那么test组件中就需要监听，在created方法里写

```javascript
export default {
  created(){
   Vue.$on('add',this.add)
  },
  method:{
  	add(){
  	  this.count++
  	}
  }
}
```

### 技术栈
1. vue全家桶
> vue2.x、vuex、vue-router、axios

2. 打包编译工具
> webpack、eslint

3. 开源工具
> better-scroll

### How to use

``` bash
# install dependencies 安装依赖
npm install

# serve with hot reload at localhost:8080 运行项目
npm run dev

# build for production with minification 编译打包
npm run build
```
### 项目截图

<img src="https://static.oschina.net/uploads/space/2017/0207/110250_3uWi_2493500.jpeg" width="40%"/>&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://cloud.githubusercontent.com/assets/20501873/24188896/ff2c5910-0f1d-11e7-80c0-bc28fd84fe80.png" width="40%"/>

### 交流

笔者热爱新技术学习、热衷分享。

- QQ：617946852
- Email：stavyan@qq.com
- WeChat stav_yan

### 最后
> 欢迎进入笔者的私人空间---[斯塔夫部落格](https://stavtop.club)

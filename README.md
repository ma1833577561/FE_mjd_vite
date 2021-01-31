* 开始使用Vite-npm版

```vbscript
npm init vite-app <project-name>
cd <project-name>
npm install
npm run dev
```



*  用Yarn初始化

```vbscript
yarn create vite-app <project-name>
cd <project-name>
yarn
yarn dev
```



*  Vite搭建React环境

```vbscript
npm init vite-app --template react
cd <project-name>
npm install
npm run dev
```



* 如何使用Ts

```html
<script lang="ts">
import HelloWorld from './components/HelloWorld.vue'
const FE_mjd:string = 'FE_mjd'
export default {
  name: 'App',
  components: {
    HelloWorld
  },
  mounted(){
    console.log(FE_mjd)
  }
}
</script>
```



* Vite支持CSS直接引入

```vue
<script>
import './assets/app.css'
</script>
<style>
	body{
        background-color: red !important;/*加!important，为了防止css冲突*/
    }
</style>
```

* 支持CSS直接引入

在assets里，新建一个FEmjd.json文件
```json
{
    "name": "前端mjd",
    "website": "FEmjd"
}
```

使用import进行引入
```vue
<script>
import data from './assets/新建一个FEmjd.json'
    export default {
  name: 'App',
  //...
  mounted(){
    console.log(data.name)
  }
}
</script>

```

* 支持Sass

```vbscript
yarn add -D sass 
```

打开/src目录下的App.vue文件
```vue
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!--加入的代码...start-->
  <h1 class="name">FE_mjd.com</h1>
  <!--加入的代码...end-->
  <HelloWorld msg="Hello Vue 3.0 + Vite" />
</template>
<style lang="scss">
  .name{
    color:green;
  }
</style>
```

* 支持jsx

在src目录中，新建一个App.jsx文件
```jsx
function App() {
    return (
        <h1>JSPang.com</h1>
    )
}
export default App;
```

修改`main.js`中的`import`代码，去掉原来对`App.vue`的引用，加入对`App.jsx`的引用

```js
import { createApp } from 'vue'
import App from './App.jsx'
import './index.css'

createApp(App).mount('#app')
```



再编写一个子组件，然后进行使用 ，比如在`App.jsx`中

```jsx
function App() {
    return (
        <> 
            <h1>JSPang.com</h1>
            <Child />
        </>
    )
}
//引入子组件(<Child/>),注意需要在外边加一层标签
function Child() {
    return (<p>我是技术胖</p>);
}
export default App;
```



** Vite生成的App.vue`这个代码，在VSCode标签中，会有红色波浪线的报错，这个如何解决

```vue
<!--对于强迫症，是不允许VSCode上有红波浪线出现的。其实这个问题只要加一个最外层的<div>标签-->
<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1 class="name">FE_mjd.com</h1>
    <HelloWorld msg="Hello Vue 3.0 + Vite" />
  </div>
</template>
```



* `Vite`配置文件中别名设置


```js
// Vite的配置文件叫做vite.config.js,需要建在项目的根目录下
// 错误别名配置
export default {
    alias: {
        '@': './src'
    }
}
// 正确别名配置
const { resolve } = require('path')
export default {
    alias: {
        '/@/': resolve(__dirname, 'src')
    }
}
```

```vue
<!--App.vue文件中，把引用目录修改一下-->
<script>
// 错误
import HelloWorld from '@/components/HelloWorld.vue'
import '@/assets/app.css'
//正确
import HelloWorld from '/@/components/HelloWorld.vue'
import '/@/assets/app.css'
</script>
```




# first-acquaintance-webpack3-for-46
### 用parcel代替webpack
#### 安装准备及JS代码转换
* [parcel](https://parceljs.org/getting_started.html)
* 先安装
```
npm install -g parcel-bundler
```
* 项目目录下创建一个 package.json 文件：
```
npm init -y
```
* 接下来，创建一个 index.html 和 index.js、module-1.js、module-2.js文件。
* index.html文件内容是
```
<html>
  <body>
    <script src="./index.js"></script>
  </body>
</html>
```
* module-1.js内容是
```
export default function fn(){
    var a=1
    console.log(a)
}

```
* module-2.js内容是
```
export default function fn(){
    var b=2
    console.log(b)
}
```
* index.js内容是
```
import x from './module-1'
import y from './module-2'

x()
y()
let a=1
console.log(a+'hello world')
```
* Parcel 内置了一个当你改变文件时能够自动重新构建应用的开发服务器，而且为了实现快速开发，该开发服务器支持热模块替换。只需要在入口文件指出：
```
parcel index.html
```
* 运行后可以看到
```
$ parcel index.html
Server running at http://localhost:1234
√  Built in 733ms.
```
* 并且在你的目录里面多了一个dist目录，里面有多了三个文件。
1. 46webpack3.e31bb0bc.js
2. 46webpack3.e31bb0bc.js.map
3. index.html
* 可以看到js里面已经把let转换为var，并且也已经加载到index.html里面去了。
* 当你打开网页http://localhost:1234的时候就可以看到，**js已经加载完成并打印出来了**。
#### 引入CSS
* 创建一个style.css，内容为
```
body {
  height: 100px;
  background-color: #ddd;
}

body p {
  height: 50px;
  background-color: blue;
}
```
* 然后再index.js里面增加
```
import './style.css'
```
* 因为之间运行了parcel index.html，就已经监控了，然后就可以看到后台自动更新，并且网页自动更新并加载了style.css代码
#### 引入SCSS并转换为CSS
* 创建一个style.scss，内容为
```
body{
    height:100px;
    background-color:#ddd;
    p{
        height:50px;
        background-color: blue;
    }
}

```
* 然后再index.js里面增加
```
import './style.scss'
```
* 因为之间运行了parcel index.html，就已经监控了，然后就可以看到后台自动去下载能否运行scss的插件，并更新后台，然后网页自动更新并加载了style.scss代码

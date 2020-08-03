## Tree shaking（打包的时候去除不用的代码）

mode:development是不会真正去除，production才会真正忽略不用的代码

#### wepack.config.js  	配置

​	1 tree shaking 只支持es module 的引入  比如import   ad from './dis/index.js'

​	2 在optimization下面配置

   

```javascript
optimization{
	usedExports:true
}
```

#### package.json 下配置

添加sideEffects:false;sideEffects:[去除其他什么都没有导入的模块]！！比如CSS，并没有导出内容，可能会被tree shaking过滤掉，这是可以设置sideEffects:["*.css"]

```json
{

 "name": "less",
 "sideEffects":false,

 "version": "1.0.0",

 "description": "",

 "main": "index.js",

 "dependencies": {

  "webpack-cli": "^3.3.12",

  "webpack": "^4.44.0"

 },

```

## develoment和production模式的区别打包

区别：dev:开发环境source-map比较全，devtool:cheap-module-source-map:打包后不需要压缩，方便调试。

pro:线上环境source-map简洁一些：cheap-source-map:打包后的代码会自动压缩



1,分离出来3个文件：共用的，开发的，生产的。webpack.conmon.js，webpack.dev.js,webpack.prod.js

2,package.json文件要进行修改，开发环境的使用webpack-dev-server;生产环境直接就是webpack;具体配置如下：

​	‘’‘dev’:'webpack-dev-serve --config ./bulid/webpack.dev.js'

​    ‘’‘bulid’:'webpack --config ./bulid/webpack.pord.js'

![image-20200803104140933](C:\Users\qq102\AppData\Roaming\Typora\typora-user-images\image-20200803104140933.png)

3, 把文件进行合并

需要安装weboack-merge包：npm install weback-merge -d

文件的合并：webpack.dev.js文件

引入webpack-merge,webpock.common.js；把自己的内容用const来命名下：用module.exports重新导出，这个时候需要用merge进行合并

![image-20200803104221191](C:\Users\qq102\AppData\Roaming\Typora\typora-user-images\image-20200803104221191.png)

## webpack和code splitting

代码分割和webpack没有任何关系

webpack中实现分割，两种方式：

1同步代码：只需要在weback.common.js中做optimization的配置

```json
optimization{
	splitChunks:{
	chunks:'all'
	}
}
```

2异步代码（import）:异步代码，无需做任何配置，会自动进行代码分割

![image-20200803214848178](C:\Users\qq102\AppData\Roaming\Typora\typora-user-images\image-20200803214848178.png)
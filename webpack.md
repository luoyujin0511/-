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


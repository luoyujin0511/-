## typeScrit的定义

typescript是javaScript的超级，ts会编译成js后才能在浏览器执行

类型概念：js是动态类型

```javascript
var a=123
a='123'
```

ts是静态类型

```typescript
let b:number=123;
b='123'(b是字符串会报错，只能赋值数字)
b=456(456是数字，正确)
```

## typeScript的优势是什么

1代码提示

2错误提示

3代码语义更清晰

## 基础类型和对象类型

#### 基础类型：

number , string, null , undefined,,symbol,boolean,void

#### 对象类型

对象

```typescript
const teacher:{
	name:string;
	age:number;

}

```

数组

```typescript
const number: number[]=[1,2,3]
```

函数两种方式：

![image-20200805231211561](C:\Users\qq102\AppData\Roaming\Typora\typora-user-images\image-20200805231211561.png)

## 类型注解和类型推断

#### 类型注解：

我们来告诉ts变量是什么类型

如：

```typescript
let count : number;
count=123;
```

函数没办法判断是什么类型需要类型注解

```typescript
function getTotal(firsUnmber:number,secondNumber:number){
	return firstNumber+secondNumber:
}
const total =getTotal(1,2)
```



#### 类型推断：

TS会自动的去尝试分析变量的类型，如果TS能够自动分析变量类型，我们就什么也不需要做了，如果TS无法分析变量类型的话，我们就需要使用类型注解

如：

```typescript
let countInference=123;
```

## 函数相关类型

​	

```typescript
function sayHello():viod{
    
}
```

表示的是返回值为空

```typescript
function()：never{
    
}
```

表示函数里面永远都不可能执行完成

```typescript
function add(｛first,second｝:{first:number,second:number}):number{
    return first+second
}
const =total=add({first:1,second:2})
```

解构类型函数
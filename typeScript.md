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

## 数组和元组

数组：

![image-20200806213726827](C:\Users\qq102\AppData\Roaming\Typora\typora-user-images\image-20200806213726827.png)

元组 tuple

```typescript
const teacherInfo : [string,string,number]=['dell','male',18]
```

## lnterface接口

#### 1定义

接口就是开发工程中，ts帮助我们做语法提示的工具，真正在编译成js代码的时候会把ts接口的内容全部剔除掉。

interface和type类似，区别：接口定义对象形式，不可以定义变量形式，type可以，能用接口尽量用接口，

#### 2接口定义

```typescript
interface Person {
	readonly name:string;  //前面添加readonly表示只读，不能赋值。
    age?:number;  //有个？号，表示可以为空，可以不写这个属性
    [propName:string]:any;//表示只要键是字符串，值是任何东西
    say():string;
}
```

#### interface继承

```typescript
interface Person {
	readonly name:string;  //前面添加readonly表示只读，不能赋值。
    age?:number;  //有个？号，表示可以为空，可以不写这个属性
    [propName:string]:any;//表示只要键是字符串，值是任何东西
    say():string;
}
interface Teacher extends person {
    teach():string;
}  //表示teacher继承person里面所有属性，还增加了一个自身属性teach():string;
```

## 类的定义与继承

#### super的用法：

当子类对继承的父类的方法重写后，还想用父类的方法则通过super.fn（）来使用

```typescript
calss Person {

  name='dell';
    getName(){
        return this.name;
    }
}
class Teacher extends Person {
    getTeacherName(){
        return 'Teacher';
    }
    getName(){
        return super.getName()+'lee'
    }
}
const teacher=new Teacher（）；
console.log(teacher.getName)
console.log(teacher.getTeacherName)
//输出结果如下
//delllee
//Teacher
```


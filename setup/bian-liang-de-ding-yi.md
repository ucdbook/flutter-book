## **变量的定义** {#Dartweb前端学习笔记——田艳容-三、变量的定义}

众所周知，JavaScript 是一门弱类型的语言，而 Dart 是强类型的语言。但dart也支持一些弱类型，Dart 中弱类型有`var`, `Object` 以及`dynamic`

大家在学习dart的过程中，可能有疑问：同为弱类型，var, object以及dynamic**有什么区别？**

1. var 初始可定义, 如果有初始值，那么其类型将会被锁定，定义之后不可改变类型
2. Object 动态任意类型，编译阶段检查类型
3. dynamic 动态任意类型，编译阶段不检查类型

```
/*字符串类型*/
var string = 'Hello, World!';
String string = 'Hello, World!';

/*数值类型*/
var number = 5;
num number = 5;
int number = 5;
double doubleNumber = 5.0

/*Map类型*/
var map = {'a': 1}; // {a: 1}
Map map = {'a': 1}; // {a: 1}
Map map = Map();
map['a'] = 1; // {a: 1}

/*List类型*/
var list = [1,1,1]; // [1,1,1]
List<num> list = [1,1,1]; // [1,1,1]
List<num> list = List();
list.add(1);
list.add(1);
list.add(1); // [1,1,1]

/*dynamic类型与Object的区别*/
dynamic i = 9;
int j=i+8;
print(a); // 17

Object i=9;
int j=i+8;
print(j);   //报错，抛出异常
```

## final 与const关键字：

final与const类似于javascript中的const，但dart中的const比final更严谨,请看下面代码

```
/*需要确定的值*/
final d1 = DateTime.now();//正确，运行时有确定的值
const d2 = DateTime.now();//报错，抛出异常; 需要编译时有确定的值
  
/*const的不可变性是可传递的，final不是*/
final List a1 = [11, 22, 33];
a1[1] = 44; //设置成功: [11, 44, 33]
 
const List a2 = [11, 22, 33];
a2[1] = 44; //报错，抛出异常
  
/*值相同时final在内存中重复创建，const会引用相同值*/
final a1 = [11 , 22];
final a2 = [11 , 22];
print(identical(a1, a2));//false
 
const b1 = [11 , 22];
const b2 = [11 , 22];
print(identical(b1, b2));//true
```




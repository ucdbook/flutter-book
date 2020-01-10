## **变量的定义** {#Dartweb前端学习笔记——田艳容-三、变量的定义}

众所周知，JavaScript 是一门弱类型的语言，而 Dart 是强类型的语言。但dart也支持一些弱类型，Dart 中弱类型有`var`, `Object` 以及`dynamic`

大家在学习dart的过程中，可能有疑问：同为弱类型，var, object以及dynamic**有什么区别？**

1. var 初始可定义, 如果有初始值，那么其类型将会被锁定，定义之后不可改变类型
2. Object 动态任意类型，编译阶段检查类型
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




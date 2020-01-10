## **函数的定义** {#Dartweb前端学习笔记——田艳容-七、函数的定义}

声明方式需要用void，有返回的必须用返回值的类型声明

```
// 无返回结果的函数
void fn(String msg) {
    print(msg);
}
 
// 返回字符串
String fn() {
    return 'Hello, World!';
}
```

函数分必传参数与可选参数: 两种定义形式

```
//可选位置参数
//a: 必传参数
//b: 可选参数
String fn(String a, [b]) {
    return a + b;
}
fn('Hello, ', 'World!') //Hello, World!
 
//可选名称参数
String fn({String msg}) {
    return msg;
}
fn(msg: 'Hello, World!'); //Hello, World!
```




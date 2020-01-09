### Dart语言对比Javascript

dart官网\(中文\)[https://dart.cn/tools/webdev](https://dart.cn/tools/webdev)

总的来说，Dart语言与Javascript还是很像的。如果写过typescript的人，因该更容易上手。

A. 每个应用都有一个 main\(\) 顶层函数

```
main() {
    print('Hello, World!');
}
```

B. 变量可以声明数据类型, 但大多数变量也可以用final、var来声明

```
var string = 'Hello, World!';
String string = 'Hello, World!';

var number = 5;
num number = 5;
int number = 5;
double doubleNumber = 5.0

var map = {'a': 1}; //{'a': 1}
Map map = {'a': 1}; //{'a': 1}
Map map = Map(); 
map.add('a', 1); //{'a': 1}


var list = [1,1,1]; //[1,1,1]
List<num> list = [1,1,1]; //[1,1,1]
List<num> list = List();
list.add(1);
list.add(1);
list.add(1); //[1,1,1]
```

C. 函数的定义\(声明方式需要用void，有返回的必须用返回值的类型声明\)

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

D. 函数的可选参数: 两种形式

```
//可选位置参数
String fn(String msg, [msgB]) {
    return msg + msgB;
}
fn('Hello, ', 'World!') //Hello, World!

//可选名称参数
String fn({String msg}) {
    return msg;
}
fn(
    msg: 'Hello, World!'
); //Hello, World!
```




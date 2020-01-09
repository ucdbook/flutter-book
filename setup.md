### Dart语言对比Javascript

dart官网\(中文\)[https://dart.cn/tools/webdev](https://dart.cn/tools/webdev)

总的来说，Dart语法与Javascript还是很像的。Dart语法比javascript更严谨一些。如果写过typescript的人，因该更容易上手。

**每个应用都有一个 main\(\) 顶层函数**

```
//test.dart
main() {
    print('Hello, World!');
}

...

//在终端执行dart test.dart将自动进入main函数
```

**导入其它dart文件**

```
// 导入核心库
import 'dart:math';

// 从外部 Package 中导入库
import 'package:test/test.dart';

// 导入文件
import 'path/to/my_other_file.dart';
```

**变量可以声明数据类型, 但大多数变量也可以用final、var来声明**

```
var string = 'Hello, World!';
String string = 'Hello, World!';

var number = 5;
num number = 5;
int number = 5;
double doubleNumber = 5.0

var map = {'a': 1}; // {a: 1}
Map map = {'a': 1}; // {a: 1}
Map map = Map(); 
map['a'] = 1; // {a: 1}


var list = [1,1,1]; // [1,1,1]
List<num> list = [1,1,1]; // [1,1,1]
List<num> list = List();
list.add(1);
list.add(1);
list.add(1); // [1,1,1]
```

**Map的操作**

```
Map user = {'name': 'XiaoHong', 'age': 23};
print(user['name']);             // XiaoHong

user.addAll({'adress': '杭州'});
print(user);                     // {name: XiaoHong, age: 23, adress: 杭州}
print(user.length); // 3
print(user.keys.toList());       //[name, age, adress]
print(user.values.toList());     //[XiaoHong, 23, 杭州]

user.forEach((key, value) {
  print('key=$key value=$value');// key=name value=XiaoHong
                                 // key=age value=23
                                 // key=adress value=杭州

});

user.remove('name');
print(user);                    // {age: 23, adress: 杭州}

user.clear();
print(user);                    // {}
print(user.isEmpty);            // true

user['name'] = 'WangHong';
print(user);                    //{name: WangHong}
```

**List的操作**

```

```

**函数的定义**

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

**类的定义**

```
class MyClass {  
   <constructors> // 构建函数
   <fields> // 字段是类中声明的任何变量，字段表示与对象有关的数据。
   <functions> // 函数表示对象的方法。
   <getters/setters> //允许程序初始化和检索类字段的值,默认的getter/setter与每个类相关联。
                     //但是可以通过显式定义setter/getter来覆盖默认值 
}
```

```
//例子:
void main() {
  MyClass myClass = new MyClass(
    count: 3
  );
  myClass.chageCount('add');
  print(myClass.currCount); // 4
  myClass.chageCount('add');
  print(myClass.currCount); // 0
  myClass.chageCount('add');
  print(myClass.currCount); // 1
  myClass
  ..chageCount('add')
  ..chageCount('add');  //使用联级运算符
  print(myClass.currCount); // 3
}
class MyClass {
  //num currCount = 0;
  //私有变量(实例化中无法访问)
  num _count;

  void set currCount(num count) {
    if(count>= 5) {
      this._count = 0;
    } else {
      this._count = count;
    }
  }

  num get currCount {
    return _count;
  }

  //构建函数
  MyClass({count}){
    currCount = count;
  }

  //类的方法
  void chageCount(String type) {
    switch(type) {
      case 'add':
        currCount++;
        break;
      case 'remove':
        currCount--;
        break;
    }
  }
}
```




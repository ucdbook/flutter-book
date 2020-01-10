## **类的定义** {#Dartweb前端学习笔记——田艳容-八、类的定义}

### 如何定义一个类及私有方法、属性的定义

```
class MyClass {
    <constructors> // 构建函数
    <fields> // 字段是类中声明的任何变量，字段表示与对象有关的数据。
    <functions> // 函数表示对象的方法。
    <getters/setters>     //允许程序初始化和检索类字段的值,默认的getter/setter与每个类相关联。
                        //但是可以通过显式定义setter/getter来覆盖默认值
}
```

例如：

```
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
    ..chageCount('add');  //联级运算符
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




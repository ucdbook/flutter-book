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

### 关系连接 {#Dartweb前端学习笔记——田艳容-关系连接}

#### **extends: 类的继承与方法重写** {#Dartweb前端学习笔记——田艳容-extends:类的继承与方法重写}

```
void main() {
    Child c = new Child();
    c.m1(12);
}
class Parent {
    void m1(int a){ print("value of a ${a}");}
}
class Child extends Parent {
    @override
    void m1(int b) {
        print("value of b ${b}");
    }
}
```

#### **with: 组合多个抽象类或普通类，并结合**mixin & on关链字限制用于哪个子类的用法:  {#Dartweb前端学习笔记——田艳容-with:组合多个抽象类或普通类，并结合mixin&on关链字限制用于哪个子类的用法:}

```
/*抽象类(抽象类不能于用实例化): 人*/
abstract class Person {
 
  void setState(fn) {
    fn();
    report();
  }
 
  void report() {
 
  }
}
 
/*mixin on关键字的用法：限定了 DrawFunc 这种能力只能够用在 Person 字类上，并在 DrawFunc 中可以访问 Person 的内容*/
mixin DrawFunc on Person {
  num age = 22;
 
  void draw() {
    setState(() {
      age = age + 5;
    });
  }
}
 
/*mixin on关键字的用法：限定了 SingFunc 这种能力只能够用在 DrawFunc 字类上，并在 SingFunc 中可以访问 DrawFunc 的内容*/
mixin SingFunc on DrawFunc {
 
  void sing() {
    setState(() {
      age = age + 1;
    });
  }
}
 
/*继承Person、DrawFunc、SingFunc*/
class Teacher extends Person with DrawFunc, SingFunc {
 
  String workType = '毕业时年龄：';
 
  //教书
  void teach() {
    setState(() {
      age = age + 3;
    });
  }
 
  @override
  void report() {
    print('${workType}workingHours=$age');
  }
 
  //初始化: Teacher做过画画、喝歌、教书等工作
  void initState() {
    report();
 
    workType = '画画后年龄：';
    draw();
 
    workType = '喝歌后年龄：';
    sing();
 
    workType = '教书后年龄：';
    teach();
  }
}
  
main() {
    Teacher teacher = Teacher();
    Teacher().initState();
}
  
/* 输出内容 */
// 毕业时年龄：workingHours=22
// 画画后年龄：workingHours=27
// 喝歌后年龄：workingHours=28
// 教书后年龄：workingHours=31
```

#### **implements: 限制被装饰子类必须包含装饰类的所有属性和方法** {#Dartweb前端学习笔记——田艳容-implements:限制被装饰子类必须包含装饰类的所有属性和方法}

```
class A {
 
  void getA() {
    print('A-getA');
  }
 
  void getB() {
    print('A-getB');
  }
 
}
 
/*B类必须包含A类的所有方法和属性*/
class B implements A {
 
  getA() {
    print('B-getA');
  }
 
  getB() {
    print('B-getB');
  }
 
  getC() {
    print('B-getC');
  }
 
}
```

### **类的总结：** {#Dartweb前端学习笔记——田艳容-类的总结：}

分为普通类与抽象类，其实抽象类不能用于实例化

1. 分为普通类与抽象类，其实抽象类不能用于实例化

2. 子类关联其它普通类或抽象类，可以通过extends、with、implements关链字做关联操作
3. 这些关联在一起的类，它们碰到名字相同的方法或属性，优先级为（前面的将复盖后面）：
   子类 &gt; with\(with后面的 &gt; 前面的\) &gt; extends；（关联的implements类的方法一定不会调用）。
4. extends 用于继承普通类或抽象类可见的方法和属性（不能继承私有方法）
5. with是把多个普通类集合到当前子类
6. `mixin`：定义了抽象类, 与abstract类似，但它可以与on关键字组合起来一块用，限制`mixin`只能在那个类的子类上使用，而`mixin`可以调用那个类的方法。




## **类型判断与bool值判断** {#Dartweb前端学习笔记——田艳容-四、类型判断与bool值判断}

```
/*类型的判断*/
var a = 123;
print(a is dynamic);  // true
assert(a is Object);  // true
  
/*if语句的判断*/
List list = [1,1,1];
if(list.length) {   //报错，抛出异常; 在dart中不会自动转换bool值。
    print(list);
}
if(list.length > 1) {    //正确
    print(list);
}
```




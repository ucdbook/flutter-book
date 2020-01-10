## **List的操作** {#Dartweb前端学习笔记——田艳容-六、List的操作}

```
List<String> list = ['a', 'b'];
print(list[0]); // a
 
/*增加*/
list.add('c');
print(list); // [a, b, c]
print(list.first); // a
print(list.last); // c
print(list.reversed.toList()); // [c, b, a]
 
list.addAll(['d', 'e']);
print(list); // [a, b, c, d, e]
 
list.insert(1, '-');
print(list); // [a, -, b, c, d, e]
list.insertAll(0, ['w', 'w']);
print(list); // [w, w, a, -, b, c, d, e]
 
 
/*删除*/
list.remove('w');
print(list); // [w, a, -, b, c, d, e]
list.removeAt(0);
print(list); // [a, -, b, c, d, e]
list.removeLast();
print(list); // [a, -, b, c, d]
list.removeRange(1, 2);
print(list); // [a, b, c, d]
 
 
/*更新*/
list[0] = 'update';
print(list); // [update, b, c, d]
list.replaceRange(1, 3, ['update1', 'update2']);
print(list); // [update, update1, update2, d]
 
 
/*遍利*/
list.forEach((item) {
    print(item);
});
```

与javascript对比，增、删的方式有一些小变化。


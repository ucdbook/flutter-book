## **Map的操作** {#Dartweb前端学习笔记——田艳容-五、Map的操作}

```
Map user = {'name': 'XiaoHong', 'age': 23};
print(user['name']); // XiaoHong

/*增加*/
user.addAll({'adress': '杭州'});
print(user); // {name: XiaoHong, age: 23, adress: 杭州}
print(user.length); // 3
print(user.keys.toList()); //[name, age, adress]
print(user.values.toList()); //[XiaoHong, 23, 杭州]

/*遍利*/
user.forEach((key, value) {
    print('key=$key value=$value'); // key=name value=XiaoHong
                                    // key=age value=23
                                    // key=adress value=杭州
});

/*删除*/
user.remove('name');
print(user); // {age: 23, adress: 杭州}

user.clear();
print(user); // {}
print(user.isEmpty); // true

/*更新*/
user['name'] = 'WangHong';
print(user); //{name: WangHong}
```

与javascript对比，键值必须引号括起来、取、增、删的方式有一些小变化。


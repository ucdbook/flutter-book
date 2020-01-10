## **JSON的转换** {#Dartweb前端学习笔记——田艳容-九、JSON的转换}

```
import 'dart:convert' as convert;
  
List list = [{'a': 1}];
String listString = convert.jsonEncode(list);
print(listString); // [{"a":1}] String类型
  
String aaString = '[{"a": 1}]';
List aa = convert.jsonDecode(aaString);
print(aa);  //[{a: 1}] List类型
```




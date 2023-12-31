# 顶层const和底层const
**《C++Primer》** 2.4.3节中讲述了顶层const和底层const。
![](./image.assets/Snipaste_2023-09-27_15-38-24.png)

在对象拷贝时，顶层const可以忽略，而底层const在**拷贝**和**被拷贝**的对象之间必须保持一致。
  
- 下面列举了一些顶层const和底层const：
``` C++
const int *p = new int(10);     // 底层const
int *const pp = new int(20);   // 顶层const
const int a = 10;               // 顶层const
const int & ra = a;             // 底层const（引用本身具有顶层const属性）
```

- 考虑如下代码:
```C++
const int a = 10;   // 顶层const
int *p = &a;        // ❌报错
```
  
虽然 `a` 此时是顶层const，但是对 `a` 取地址后，对于地址而言，修饰 `a` 的const就变为了底层const。
  

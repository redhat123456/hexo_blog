---
title: '[技术干货]竞赛中C++常用函数（打ACM和CCSP的同学快看）'
author: Tanger
date: 2020-07-10 09:59:44
tags:
  - 技术干货
  - 常用算法
  - ACM
categories:
  - 技术干货
  - 算法入门
---

# 竞赛中 C++常用函数（打 ACM 和 CCSP 的同学快看）

## C 与 C++的区别

虽然同为 C 大家族的成员，但 C++和 C 用起来确实有较大差别。例如，C++中有许多内置函数库可以直接调用，而 C 语言的大多数函数需要自己定义。在 C++中，我们可以尽情地使用函数库，极大地方便了竞赛编程。

下面给大家总结一些竞赛中常用的 C++函数，希望对初学者有所帮助。

---

## 基本函数篇

### 1. 排序函数 `sort`

`sort()` 是 C++中用于对指定区间内所有元素进行排序的函数（默认升序）。区间使用迭代器或指针表示，比如对于数组 `a[n]`，想要对它排序，可以写：

```cpp
sort(a, a + n); // 对数组a进行升序排序
```

如果想要降序排序，可以自定义比较函数：

```cpp
#include <bits/stdc++.h>
using namespace std;

// 自定义比较函数，实现降序排序
bool cmp(int a, int b) {
    return a > b;
}

int main() {
    int n = 5;
    int a[] = {3, 1, 4, 5, 2};
    sort(a, a + n, cmp); // 从大到小排序
    for (int i = 0; i < n; i++)
        cout << a[i] << " ";
    return 0;
}
```

字符串排序：

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    vector<string> strs = {"apple", "banana", "cherry"};
    sort(strs.begin(), strs.end()); // 升序排序
    sort(strs.begin(), strs.end(), greater<string>()); // 降序排序
    return 0;
}
```

### 2. 快速求最大值与最小值 `max` 和 `min`

```cpp
int a = 10, b = 20;
cout << max(a, b) << endl; // 输出20
cout << min(a, b) << endl; // 输出10
```

### 3.求绝对值 `abs`

```cpp
int x = -5;
cout << abs(x) << endl; // 输出5
```

对于浮点数用 `fabs`：

```cpp
#include <cmath>
double y = -3.14;
cout << fabs(y) << endl; // 输出3.14
```

### 4. 字符串转整数 `stoi` 和整数转字符串 `to_string`

```cpp
string s = "12345";
int num = stoi(s); // 转成整数12345

int x = 6789;
string str = to_string(x); // 转成字符串"6789"
```

### 5. 数学常用函数

```cpp
#include <cmath>
cout << sqrt(16) << endl;     // 开平方，输出4
cout << pow(2, 10) << endl;   // 2的10次方，输出1024
cout << ceil(3.14) << endl;   // 向上取整，输出4
cout << floor(3.14) << endl;  // 向下取整，输出3
```

### 6. 判断字符类型

```cpp
char c = 'A';
if (isdigit(c)) cout << "数字" << endl;
if (isalpha(c)) cout << "字母" << endl;
if (islower(c)) cout << "小写字母" << endl;
if (isupper(c)) cout << "大写字母" << endl;
```

### 7. 数组初始化

```cpp
int a[100];
memset(a, 0, sizeof(a));   // 将数组a所有元素初始化为0
memset(a, -1, sizeof(a));  // 将数组a所有元素初始化为-1（注意字节赋值）
```

### 8. 常用 STL 容器

- vector

```cpp
vector<int> v;
v.push_back(1);
v.push_back(2);
cout << v.size() << endl;  // 输出2
```

- set（自动排序且不重复）

```cpp
set<int> s;
s.insert(3);
s.insert(1);
s.insert(3); // 插入重复元素无效
for(auto x : s)
    cout << x << " "; // 输出：1 3
```

- map（键值对）

```cpp
map<string, int> mp;
mp["apple"] = 3;
mp["banana"] = 5;
cout << mp["apple"] << endl; // 输出3
```

### 9. 常用位运算技巧

- 判断奇偶

```cpp
if (x & 1) cout << "奇数" << endl;
else cout << "偶数" << endl;
```

- 取反

```cpp
int y = ~x;
```

- 左移右移

```cpp
int z = x << 1; // 左移1位，相当于乘2
int w = x >> 1; // 右移1位，相当于除2（向下取整）
```

### 10. 快速读写优化（竞赛中常用）

```cpp
ios::sync_with_stdio(false);
cin.tie(nullptr);
```

放在 main 函数开头，可以加快 cin 和 cout 的速度，避免超时。

## 总结

以上是竞赛中比较常用的 C++基础函数和技巧，掌握它们能帮助你快速写出高效、简洁的代码。如果你想了解更高级的函数和数据结构，也欢迎留言告诉我！

> 欢迎收藏转发，助力你的 ACM 和 CCSP 之路！

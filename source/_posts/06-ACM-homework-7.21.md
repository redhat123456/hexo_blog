---
title: 桂林电子科技大学 ACM 暑假课 | 7 月 21 日 ACM 作业题解
date: 2020-07-15 09:57:14
tags:
  - 作业题解
  - ACM 算法
categories:
  - 算法入门
---

# 桂林电子科技大学暑假课 ACM 作业题解合集

本文整理了桂电暑假 ACM 训练营 7 月 21 日作业的 10 道典型题目及参考代码，并附带简明题解说明，供学习和复习使用。

---

## 1. A 简单数学题：判断数字各位是否全不相同

**题目描述：**  
给定一个数字 `n`，判断它的每一位数字是否都不相同。

**输入：**  
一个数字 `n`，满足 `1 < n < 1000000`

**输出：**  
若各位数字均不相同，输出 `YES`，否则 `NO`。

**参考代码（C）：**

```c
#include<stdio.h>
#include<stdbool.h>

int main() {
    char A[10];
    bool used[300] = {false};
    scanf("%s", A);
    for (int i = 0; A[i] != '\0'; i++) {
        if (used[A[i]]) {
            printf("NO");
            return 0;
        }
        used[A[i]] = true;
    }
    printf("YES");
    return 0;
}
```

**题解**

- 使用数组 `A[10]` 存放输入的数字字符，最多 10 位，足够。

- 用布尔数组 `result` 标记每个字符是否出现过，出现重复即输出`NO`。

- 也可以用计数变量统计每个数字出现次数，出现超过一次即输出 `NO`。

## 2.B 二进制转换

**题目描述**

将给定数字 n 转换为二进制表示。

**输入**
一个数字 n，满足 1 < n < 10^5。

**输出**
输出数字 n 的二进制表示。

**参考程序**

```C
#include <stdio.h>

int main() {
    int num[10001], i = 0, n;
    scanf("%d", &n);
    while (n > 0) {
        num[i++] = n % 2;
        n /= 2;
    }
    while (i--)
        printf("%d", num[i]);
    return 0;
}

```

**题解**

- 通过取余操作不断除以 2，将结果倒序存储，最后正序输出即可。

## 3.C 经典字符串问题 — 判断回文串

**题目描述**
给定一个字符串，判断它是否为回文串（正反相同）。

**输入**

- 第一行一个数字 t，表示测试组数，0 < t < 100。

- 接下来每组两行：

  - 第一行为字符串长度 n (1 < n < 1000)

  - 第二行为长度为 n 的字符串。

**输出**

每组数据输出 `YES`（回文）或 `NO`（非回文）。

**参考程序**

```C
#include <stdio.h>
#include <string.h>

int main() {
    int n, t, i, isPalindrome;
    char str[1001];
    scanf("%d", &t);
    while (t--) {
        scanf("%d", &n);
        scanf("%s", str);
        isPalindrome = 1;
        for (i = 0; i < n; i++) {
            if (str[i] != str[n - i - 1]) {
                isPalindrome = 0;
                break;
            }
        }
        printf(isPalindrome ? "YES\n" : "NO\n");
    }
    return 0;
}
```

**题解**

- 字符串回文判断，比较对应位置字符是否相等。
- 也可用整形数反转法判断数字是否回文（参考代码略）。

## 4.D 排序

**题目描述**
给定长度为 n 的序列，对其从小到大排序后输出。

**输入**

- 第一行为 n，1 < n < 1000

- 第二行 n 个整数。

**输出**
排序后的序列，空格分隔。

样例
输入：

```text
10
2 5 7 8 10 1 6 11 20 35
```

输出：

```text
1 2 5 6 7 8 10 11 20 35
```

**参考程序**

```C
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];
    sort(a.begin(), a.end());
    for (int i = 0; i < n; i++) cout << a[i] << " ";
    return 0;
}
```

**题解**

- C++的 sort 函数使用方便。
- 若需要从大到小排序，可以传入自定义比较函数。

## 5.E 改作文

---
title: ACM 算法入门 · 递归篇：从简单调用到巧妙解题
date: 2020-07-12 09:57:14
tags:
  - 递归
  - ACM算法
categories:
  - 算法入门
---

# ACM 算法入门 · 递归篇：从简单调用到巧妙解题

## 什么是递归？

> 递归（Recursion）是一种程序调用自身的编程技巧，常用于将复杂问题分解为规模更小的同类问题。  
> 它是一种 **“以小见大”** 的思想，用有限的代码描述无限的过程。

递归在程序设计语言中被广泛应用，尤其在算法题中非常常见。其核心在于：

- **边界条件**：定义递归终止的情形；
- **递归调用**：将问题逐步缩小并调用自身；
- **返回过程**：逐层返回解，最终合并结果。

举个例子：**阶乘的递归定义**

```text
fac(1) = 1
fac(n) = n * fac(n-1)
```

## 递归三步走（以阶乘为例）

### Step 1：边界条件（终止递归的出口）

我们先考虑一个简单的问题：6! =6 × 5 × 4 × 3 × 2 × 1。

在编写阶乘函数时，我们可以有两种实现思路：

- **从 1 乘到 n**（正序递归）

- **从 n 乘到 1**（逆序递归）

不论哪种方式，核心都在于**设定边界条件**，也就是：**什么时候停止递归？**

我们这里采用第二种方式 —— **从 n 递减到 1**：

当 `n == 1` 时，就不再继续向下递归，而是直接返回 `1`，这就是我们设定的递归终止条件（边界）：

```python
def fac(i):
  if(i==1):    #边界条件
    return 1
```

这意味着，**当问题被缩小到最简单的情况（n=1）时，递归不再继续，而是开始回传答案。**

### Step 2：递归调用（函数调用自身）

在确定了边界后，我们就可以让函数调用自身，把大问题逐步“压小”：

```python
def fac(i):
    if i == 1:
        return 1
    return fac(i - 1) * i
```

这时，函数每次都会将问题规模减小为 `fac(i-1)`，直到 `i == 1` 为止。

### Step 3：返回过程（从最小问题逐层回传）

递归调用本质上是**函数栈**，每次压栈是“前进”，每次 return 是“回退”。

举个例子：`fac(6)` 实际调用流程如下：

```text
fac(6)
→ return fac(5) * 6
→ → return fac(4) * 5
→ → → return fac(3) * 4
→ → → → return fac(2) * 3
→ → → → → return fac(1) * 2
→ → → → → → return 1
最终返回值：1 * 2 * 3 * 4 * 5 * 6 = 720

```

![recursion.jpg](https://s2.loli.net/2025/07/06/BuCyzem6ORcAEbL.jpg)

## 构成递归的必要条件

- 1、子问题必须与原问题结构相同，且规模更小；

- 2、必须有终止条件，否则将无限调用；

- 3、问题最终需能归结为基本情形求解。

以经典的**斐波那契数列**为例：

```text
Fib(0) = 1
Fib(1) = 1
Fib(n) = Fib(n-1) + Fib(n-2)  （n > 1）
```

虽然写法简单，但由于重复计算多，效率低，因此在实际编程中经常结合**记忆化搜索**或**动态规划**来优化。

## 生活中的递归现象

递归不仅仅是代码技巧，也出现在生活和艺术中，例如：

- **德罗斯特效应**：一个图像中包含缩小版的自己，一层套一层；

- **镜中蜡烛**：两面镜子之间放置蜡烛，可以看到无限反射；

- **搬箱子问题**：你要搬 100 个箱子，先搬一个，再解决“搬 99 个箱子”的问题……

这类递归式的思维方式，正是递归定义的日常化体现。

## 实战演练

### 递归的经典应用：斐波那契数列

> 斐波那契数列（Fibonacci Sequence）是递归最经典的应用之一。  
> 它的定义是：一个数等于前两个数之和。

```python
def fib(n):
    if n <= 1:
        return n
    return fib(n - 1) + fib(n - 2)

n = int(input("请输入一个正整数 n："))
print(f"第 {n} 个斐波那契数是：{fib(n)}")
```

> 注意：这种方式虽然直观，但性能较差，时间复杂度是指数级（约为 O(2ⁿ)），不适合计算较大的 n。

输出示例（输入 10）：

```text
第 10 个斐波那契数是：55
```

#### 算法题：卖鸭子

一个人赶着鸭子去每个村庄卖，每经过一个村子卖去所赶鸭子的一半又一只。这样他经过了七个村子后还剩两只鸭子，问他出发时共赶多少只鸭子？经过每个村子卖出多少只鸭子

递归终止的条件是当达到第 7 个村庄时递归停止，设经过的村庄数为 n 则有剩余的鸭子为总数为每次剩余的鸭子数位 sum = sum-(sum/2+1)
算法构造：当 n=7 时 sum = 2;当 0<n<7 时 sum =2\*m+2;

源代码：

```C
#include <iostream.h>
class Questionone{
public:
    int answer(int n, int sum){
        if(n>0){
            sum = 2*sum+2;
            if(n-1>0){
                cout<<"第"<<n-1<<"个村庄"<<"卖出"<<2*sum+2-sum<<endl;
            }
            n--;
            return answer(n,sum);

        }else{
            return sum;
        }
    }
};
void main(){
    int SUM = 2;
    int  N =  7;
    Questionone question;
    cout<<"总数："<<question.answer(N,SUM)<<endl;
}
```

### 经典算法题：角谷定理

题目：
输入一个自然数，若为偶数，则把它除以 2，若为奇数，则把它乘以 3 加 1。经过如此有限次运算后，总可以得到自然数值 1。求经过多少次可得到自然数 1。

算法分析：
递归的终止条件是最后值为 1；设输入的值为 n 先进项判断，若 n = 1 则输出 n;
若 n 不为 1；则对他进行偶数判断，若为偶数除 2，若为奇数则乘 3 加 1；然后在进行偶数判断，直到 n = 1 为止；
算法构造
n=1 时 输出 n；n!=1 时 偶数判断 偶数 n = n/2;若是奇数 n = 3\*n+1

源代码：

```C
#include<iostream.h>
class questiontwo{
    public:
        int answer(int sum){
            if(sum == 1){
                cout<<" "<<sum;
                return sum;
            }else{
                if((sum%2) == 1){
                    sum = 3*sum+1;
                    cout<<" "<<sum;
                    return answer(sum);
                }else{
                    sum = sum/2;
                    cout<<" "<<sum;
                    return answer(sum);
                }
            }
        }
};
void main(){
    int c ;
    cout<<"请输入一个数"<<endl;
    cin>>c;
    questiontwo question2;
    question2.answer(c);
}
```

### 经典算法题：电话号码

题目：
电话号码对应的字符组合：在电话或者手机上，一个数字对应着字母 ABC，7 对应着 PQRS。那么数字串 27 所对应的字符可能组合就有 3\*4 种（如 AP,BR 等）。现在输入一个 3 到 11 位长的电话号码，请打印出这个电话号码对应的字符的所有可能组合和组合数。

题目分析：
根据题意可知：2 对应的是 ABC 3 对应的是 DEF 4 对应的是 GHI 5 对应的 JKL 6 对应的是 MNO 7 对应的是 PQRS 8 对应的是 TUV 9 对应的是 WXYZ

源代码：

```C
public class questionthree {
    /**
    *
    * @param number      电话号码
    * @param answer    辅助数组
    * @param index  电话位数中对应的第几位循环
    * @param n  电话位数
    */
    public static void Answer(int []number, int []answer,int
    index,int n){
        char[][] word ={{},{},{'A','B','c'},{'D','E','F'},{'G',
            'H','I'},{'J','K','L'},{'M','N','O'},{'P','Q','R','s'},
            {'T','U','V'},{'W','X','Y','Z'}};
        int []sum = {0,0,3,3,3,3,3,4,3,4};
        if(index == n){
            for(int i = 0; i<n; i++){
                System.out.print(word[number[i]][answer[i]]);
            }
            System.out.println(";");
            return ;
        }
        for(answer[index] = 0; answer[index] < sum [number[index]]; answer[index]++){
            Answer(number,answer,index+1,n);
        }
    }
    public static void main(String[] args){
        int[] number = {2,3,4,5,6,7,8,9};
        int[] answer = new int[number.length];
        Answer(number, answer, 0, number.length);

    }
}
```

### 经典算法题：柿子分配

题目：
日本著名数学游戏专家中村义作教授提出这样一个问题：父亲将 2520 个桔子分给六个儿子。分完 后父亲说：“老大将分给你的桔子的 1/8 给老二；老二拿到后连同原先的桔子分 1/7 给老三；老三拿到后连同原先的桔子分 1/6 给老四；老四拿到后连同原先的桔子分 1/5 给老五；老五拿到后连同原先的桔子分 1/4 给老六；老六拿到后连同原先的桔子分 1/3 给老大”。结果大家手中的桔子正好一 样多。问六兄弟原来手中各有多少桔子？

题目分析：
解决此问题主要使用递归运算。由题目可以看出原来手中的加上得到的满足关系式：StartNum = 420 * (n -2)/(n - 1)  分给下一个人的橘子数：GiveNum = AfterGetNum / n;   下一个人的橘子数：nextStartNum = 420*(n-1)/(n-2) - GiveNum;   下一个人加上之前得到的橘子的总数：afterGetNum = nextStartNum + GiveNum;   以此使用递归算法可以算出各个孩子原来手中的橘子数。

源代码：

```C
public class questionfour {
    /**
    *
    * @param n  表示第几个儿子
    * @param befor  表示为分配之前就的桔子数
    * @param After    表示分配之后的桔子数
    * @param m        分配的比例
    * @return
    */
    public int answer(int n,int befornum, int afternum,int m ){
        if(n>6){
            return 0;
        }else{
            System.out.println("老"+n+"原有的桔子数"+befornum);
            //分给下一个人的桔子数
            int givenum = afternum/m;
            //下一个人的桔子数
            int nextBeforenum = 420*(m-1)/(m-2)-givenum;
            //下一人加上之前的桔子数的总数
            int afterGetnum = nextBeforenum+givenum;
            return answer(n+1,nextBeforenum,afterGetnum,m-1);
        }
    }
    public static void main(String[] args){
        questionfour question4 = new questionfour();
        question4.answer(1, 240, 240, 8);
    }
```

## 总结

递归是一种将**大问题分解为小问题**、逐层求解再合并结果的强大方法。掌握递归不仅是解题利器，更能帮助你建立更抽象、更系统的问题解决能力。

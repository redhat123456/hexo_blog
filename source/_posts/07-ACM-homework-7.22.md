---
title: 桂林电子科技大学 ACM 暑假课 | 7 月 22 日 ACM 作业题解
author: Tanger
date: 2020-07-22 08:43:21
tags:
  - 作业题解
  - ACM 算法
categories:
  - 算法入门
---

## A: 讲故事

**题目描述：**

一天，天上掉下来了一个可爱的小妹妹，小妹妹天天缠着你给她讲故事。并且让你在 N 天内给她讲 K(K ≤ N)个不同小故事。你把你知道的所有 K 个故事从 1 到 K 进行编号。她每天会要求你讲某一个小故事，例如第 i 天她会要求你给他讲第 ai 个小故事。

由于小妹妹有间歇性失忆，所以她可能会在一些天内要求你讲你已经讲过的故事。如果你每天都按照她的要求来的话，可能会出现无法在 N 天内讲完 K 个故事的情况(小妹妹可能没有要求过讲某个故事)

你为了完成任务可能在某些情况下，不得不拒绝她的要求，给她讲其他的小故事。但是你在第 i 天拒绝了小妹妹的请求的话，小妹妹对你的好感度就会下降 b

如何在降低最小好感度的情况下在 N 天内讲完 K 给小故事。请输出最少降低的好感度。

**输入：**

- 第一行两个正整数，N K (1≤ K ≤N ≤ 10^5) N 为总天数，K 为需要讲述的故事个数

- 第二行 N 个正整数 a1 a2 …… an (1 ≤ ai ≤ k) 第 n 天要求的故事序号

- 第三行 N 个正整数 b1 b2 …… bn(1 ≤ bi ≤ 10^9) 第 i 天拒绝要求降低的好感度

**输出：**

一行，**满足条件**的前提下最少降低的好感度。

**样例输入：**

```text
8 7
1 1 3 1 5 3 7 1
5 7 4 8 1 3 5 2
```

**样例输出：**

```text
10
```

**提示：**

- 对样例一，最佳的方案是在 1, 6, 8 天把故事改为 2, 4, 6 号，降低的好感度为 a1 + a6 + a8 = 5 + 3 + 2 = 10

- 对样例二，不需要做调整

**参考程序：**

```C
#include<cstdio>
#include<cstring>
#include<algorithm>
using namespace std;
#define ll long long
struct data_p{int a;ll b;}num[100005];
int n,k,maxl[100005],now=0;
ll ans;
bool cmp(data_p x,data_p y){return x.b<y.b;}
int main()
{
    scanf("%d%d",&n,&k);
    for(int i=1;i<=n;i++)
    {
        scanf("%d",&num[i].a);
    }
    for(int i=1;i<=n;i++)
    {
        scanf("%d",&num[i].b);

        if(num[ maxl[ num[i].a ] ].b<num[i].b)
        maxl[num[i].a]=i;
    }

    for(int i=1;i<=k;i++)
    {
        if(!maxl[i])continue;
        num[maxl[i]].b=1000000000;
        now++;
    }

    sort(num+1,num+n+1,cmp);

    for(int i=1;i<=k-now;i++)
    {
        ans+=num[i].b;
    }
    printf("%lld",ans);
    return 0;
}
```

**题解：**贪心问题求最优解，先排序让降低好感度最小的排在前面，先对重复且降低好感度最小的故事提出来，然后再根据要调整的天数来依此相加。

## B: 数学题

**题目描述：**

今天，你向你的心上人表白了，可是 TA 说：

我这里有一个长度为 n(2 ≤ n ≤ 30)的数列，数列的第 i 项是 2i。现在保证数列长度 n 是一个偶数，将数列平均分成两份，如果你能得出两份的最小差值，我就答应你。

看着自己的心上人，你光速的写了一个程序，算出了最小差值。

**输入：**

- 第一行 T (T≤100) 表示 (~~你心上人的个数~~) 有 T 组数据

- 接下来的 T 行每一行有一个 数组长度 n (2 ≤ n ≤ 30)且保证 n 是偶数

**输出：**

对于每一个测试数据都输出最小差值

**样例输入：**

```text
2
2
4
```

**样例输出：**

```text
2
6
```

**提示：**

用笔算

**参考程序：**

```C
#include<cstdio>
#include<iostream>
#include<math.h>
using namespace std;
long long sum1,sum2;
int main(){
    int t,n,i,step;
    cin>>t;
    while(t--){
        cin>>n;
        if(n%2!=0)
        continue;
        else{
        sum1=0,sum2=0,step=1;
        for(i=1;i<=n-1;i++){
            step=step*2;
            sum1=sum1+step;
            }
            step=1;
        for(i=1;i<=(n/2)-1;i++){
            step=step*2;
            sum2=sum2+step;
        }
        cout<<pow(2,n)+2*sum2-sum1<<endl;}
    }
    return 0;
}
```

**题解：**

<img src="https://img.alicdn.com/imgextra/i4/0/O1CN01ZzlH9b1kCpWyEAy3S_!!0-rate.jpg_400x400.jpg" style="width: 100%;" />

## C: 数的划分

**题目描述：**

将整数 n 分成 k 份，且每份不能为 0，问有多少种不同的分法。注：当 n=7，k=3 时，下面三种分法被视为是相同的

```text
1 1 5
1 5 1
5 1 1
```

**输入：**

一行两个整数 n，k

**输出：**

一行一个整数，即不同的分法数

**样例输入：**

```text
7 3
```

**样例输出：**

```text
4
```

**提示：**

对于样例的四种分法：

```text
1 1 5
1 2 4
1 3 3
2 2 3
```

0<=n<=200，2<=k<=6

**参考程序：**

```C
#include<iostream>//(深搜)
using namespace std;
int n,k,ans=0;
void dfs(int past,int cnt,int num)
{
    if(cnt==1)
    {
        ans++;
        return;
    }
    for(int i=past;i<=num/cnt;i++)
    dfs(i,cnt-1,num-i);
}
int main()
{
    cin>>n>>k;
    dfs(1,k,n);
    cout<<ans;
    return 0;
}
```

**题解：**

也就是递归+搜索，其中 past 代表当前分出来的数，cnt 代表是剩下还可以分几次，num 代表分完 past 之后
剩下的数。其实思想是很简单的，只要能理解，用笔写一写就可以知道了，反正懂得都懂。

## D: 扩散

**题目描述：**

一个点每过一个单位时间就会向四个方向扩散一个距离，如图。

![](https://img.alicdn.com/imgextra/i2/0/O1CN016YZY6n1kCpWtycyUL_!!0-rate.jpg_400x400.jpg)

两个点 a、b 连通，记作 e(a,b),当且仅当 a、b 的扩散区域有公共部分。连通块的定义是块内的任意两个点 u、v 都必定存在路径 e(u,a0),e(a0,a1),…,e(ak,v)。给定平面上的 n 给点，问最早什么时刻它们形成一个连通块。

**输入：**

第一行一个数 n，以下 n 行，每行一个点坐标 X[i] Y[i]。

**输出：**

一个数，表示最早的时刻所有点形成连通块。

**样例输入：**

```text
2
0 0
5 5
```

**样例输出：**

```text
5
```

**提示：**

1≤N≤50; 1≤X[i],Y[i]≤10^9

**参考程序：**

```C
#include<bits/stdc++.h>
using namespace std;
const int N=100;
int n,dis[N][N],anss;
struct node{
    int x,y;
}a[N];
int main()
{
    scanf("%d",&n);
    for (int i=1;i<=n;i++)
    scanf("%d%d",&a[i].x,&a[i].y);
    for (int i=1;i<=n;i++)
    for (int j=1;j<=n;j++)
        dis[i][j]=abs(a[i].x-a[j].x)+abs(a[i].y-a[j].y);
    for (int k=1;k<=n;k++)
    for (int i=1;i<=n;i++)
        for (int j=1;j<=n;j++)
        dis[i][j]=min(dis[i][j],max(dis[i][k],dis[k][j]));
    for (int i=1;i<=n;i++)
    for (int j=1;j<=n;j++)
        anss=max(anss,dis[i][j]);
    printf("%d\n",(anss+1)/2);
    return 0;
}
```

**题解：**

先来科普一下曼哈顿距离：**d(i,j)=|xi-xj|+|yi-yj|**，也就是直线距离

我们假设有两个点 A，B，他们的坐标分别为(X1,Y1),(X2,Y2).那么现在我们要这两个点扩散，要多长时间？
假设 X1< X2,且 Y1< Y2，那么它们想要尽量靠拢就要向对方的方向扩散。那么 A 点每扩散一次，他们之间的距离-1，
同理 B 点每扩散一次，距离-1。

说明：
每次扩散 A、B 的曼哈顿距离-2. 1.如果曼哈顿距离（设其为 dis）为奇数，那最后一次距离只差 1。所以需要 dis/2+1 的时间，也就是（dis+1）/2;

2,如果曼哈顿距离为偶数，那正好 dis/2 的时间后他们会正好相遇。而（dis+1）/2 后对结果没有影响（因为是下取整）

假设有三个点 ABC，其中 A 离原点最近，C 离原点最远，假设 AB 我们用了 t1 秒，BC 我们用了 t2 秒，不考虑 B，AC 用了 t3 秒
，那么就会有 min(t1，t2)< t3,所以我们只需枚举每两个节点，用 ans 更新最大值即可，找到最大值就是答案了。(最远的两个点都扩散完了，
其他点肯定早他妈扩散完了)

# luogu P5736 【深基7.例2】质数筛



# 【深基7.例2】质数筛

## 题目描述

输入 $n$ 个不大于 $10^5$ 的正整数。要求全部储存在数组中，去除掉不是质数的数字，依次输出剩余的质数。

## 输入格式

第一行输入一个正整数 $n$，表示整数个数。

第二行输入 $n$ 个正整数 $a_i$，以空格隔开。

## 输出格式

输出一行，依次输出 $a_i$ 中剩余的质数，以空格隔开。

## 样例 #1

### 样例输入 #1

```
5
3 4 5 6 7
```

### 样例输出 #1

```
3 5 7
```

## 提示

数据保证，$1\le n\le100$，$1 \leq a_i \leq 10^5$。



```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<algorithm>
#include<cstdio>
#include<math.h>
#include <cstring>
using namespace std;



bool isprime(int n)
{
	if (n == 1 || n == 4)return false;
	if (n == 2 || n == 3 )return true;
	if (n % 6 != 1 && n % 6 != 5)return false;
	for (int i = 5; i * i <= n; i++)
	{
		if (n % i == 0)return false;

	}
	return true;
}

int main()
{
	int a[100], n,num,count=0,prime[100];
	cin >> n;
	for (int i = 0; i < n; i++)
	{
		cin >> num;
		if (isprime(num))prime[count++]=num;
	}
	for (int i = 0; i < count; i++)
	{
		if (i == 0)cout << prime[i];
		else cout << " " << prime[i];
	}
	return 0;
}
```


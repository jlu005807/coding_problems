# luogu B3939 [GESP样题 四级] 绝对素数



# [GESP样题 四级] 绝对素数

## 题目描述

如果一个两位数是素数，且它的数字位置经过对换后仍为素数，则称为绝对素数，例如 $13$。给定两个正整数 $A, B$，请求出大于等于 $A$、小于等于 $B$ 的所有绝对素数。

## 输入格式

输入 $1$ 行，包含两个正整数 $A$ 和 $B$。保证 $10<A<B<100$。

## 输出格式

若干行，每行一个绝对素数，从小到大输出。

## 样例 #1

### 样例输入 #1

```
11 20
```

### 样例输出 #1

```
11
13
17
```





```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<vector>
#include<regex>
#include<algorithm>
#include<cstdio>
#include<math.h>
#include <cstring>
using namespace std;

bool isprime(int n)
{
	if (n == 0 || n == 1 || n == 4)return false;
	if (n == 2 || n == 3 || n == 5)return true;
	if (n % 6 != 1 && n % 6 != 5)return false;
	for (int i = 5; i * i <= n; i++)
		if (n % i == 0)return false;
	return true;
}


int main()
{
	int n, m;
	cin >> n >> m;
	for (int i = n; i <= m; i++)
	{
		int v = i % 10 * 10 + i / 10;
		if (isprime(i) && isprime(v))cout << i << endl;
	}
	return 0;
}
```


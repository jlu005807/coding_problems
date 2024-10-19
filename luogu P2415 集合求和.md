# luogu P2415 集合求和



# 集合求和

## 题目描述

给定一个集合 $s$（集合元素数量 $\le 30$），求出此集合所有子集元素之和。

## 输入格式

集合中的元素（元素 $\le 1000$）

## 输出格式

$s$ 所有子集元素之和。

## 样例 #1

### 样例输入 #1

```
2 3
```

### 样例输出 #1

```
10
```

## 提示

**【样例解释】**

子集为：$\varnothing, \{ 2 \}, \{ 3 \}, \{ 2, 3 \}$，和为 $2 + 3 + 2 + 3 = 10$。

----

**【数据范围】**

对于 $100 \%$ 的数据，$1 \le \lvert s \rvert \le 30$，$1 \le s_i \le 1000$，$s$ 所有子集元素之和 $\le {10}^{18}$。



```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<algorithm>
#include<cstdio>
#include<math.h>
#include <cstring>
using namespace std;


int main()
{
	int v[31], n = 0;
	long long add = 0;
	while (cin >> v[n]) {
		add += v[n];
		n++;
	};
	add = add*pow(2,n-1);
	cout << add;
}
```


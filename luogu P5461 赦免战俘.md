# luogu P5461 赦免战俘



# 赦免战俘

## 题目背景

借助反作弊系统，一些在月赛有抄袭作弊行为的选手被抓出来了！

## 题目描述

现有 $2^n\times 2^n (n\le10)$ 名作弊者站成一个正方形方阵等候 kkksc03 的发落。kkksc03 决定赦免一些作弊者。他将正方形矩阵均分为 4 个更小的正方形矩阵，每个更小的矩阵的边长是原矩阵的一半。其中左上角那一个矩阵的所有作弊者都将得到赦免，剩下 3 个小矩阵中，每一个矩阵继续分为 4 个更小的矩阵，然后通过同样的方式赦免作弊者……直到矩阵无法再分下去为止。所有没有被赦免的作弊者都将被处以棕名处罚。

给出 $n$，请输出每名作弊者的命运，其中 0 代表被赦免，1 代表不被赦免。

## 输入格式

一个整数 $n$。

## 输出格式

$2^n \times 2^n$ 的 01 矩阵，代表每个人是否被赦免。数字之间有一个空格。

## 样例 #1

### 样例输入 #1

```
3
```

### 样例输出 #1

```
0 0 0 0 0 0 0 1
0 0 0 0 0 0 1 1
0 0 0 0 0 1 0 1
0 0 0 0 1 1 1 1
0 0 0 1 0 0 0 1
0 0 1 1 0 0 1 1
0 1 0 1 0 1 0 1
1 1 1 1 1 1 1 1
```





```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<algorithm>
#include<cstdio>
#include<math.h>
#include <cstring>
using namespace std;
int num[1030][1030];

void f(int x, int m, int n)
{
	if (x == 2) {
		num[m][n] = 0;
		return;	
	}
	for (int i = m; i <= m+x / 2-1; i++)
		for (int j = n; j <= n+x / 2-1; j++)num[i][j] = 0;
	f(x / 2, m + x / 2, n);
	f(x / 2, m + x / 2, n + x / 2);
	f(x / 2, m, n + x / 2);
}




int main()
{
	int n,k;
	cin >> n;
	k = pow(2, n);
	for (int i = 1; i <= k; i++)
		for (int j = 1; j <= k; j++)
			num[i][j] = 1;
	f(k, 1, 1);

	for (int i = 1; i <= k; i++) {
		for (int j = 1; j < k; j++)cout << num[i][j] << " ";
		cout << num[i][k] << endl;
	}

}
```


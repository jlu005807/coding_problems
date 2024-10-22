# luogu P1205 [USACO1.2] 方块转换 Transformations



# [USACO1.2] 方块转换 Transformations

## 题目描述

一块 $n \times n$ 正方形的黑白瓦片的图案要被转换成新的正方形图案。写一个程序来找出将原始图案按照以下列转换方法转换成新图案的最小方式：

- 转 $90\degree$：图案按顺时针转 $90\degree$。

- 转 $180\degree$：图案按顺时针转 $180\degree$。

- 转 $270\degree$：图案按顺时针转 $270\degree$。

- 反射：图案在水平方向翻转（以中央铅垂线为中心形成原图案的镜像）。

- 组合：图案在水平方向翻转，然后再按照 $1 \sim 3$ 之间的一种再次转换。

- 不改变：原图案不改变。

- 无效转换：无法用以上方法得到新图案。

如果有多种可用的转换方法，请选择序号最小的那个。

只使用上述 $7$ 个中的一个步骤来完成这次转换。

## 输入格式

第一行一个正整数 $n$。   

然后 $n$ 行，每行 $n$ 个字符，全部为 `@` 或 `-`，表示初始的正方形。

接下来 $n$ 行，每行 $n$ 个字符，全部为 `@` 或 `-`，表示最终的正方形。

## 输出格式

单独的一行包括 $1 \sim 7$ 之间的一个数字（在上文已描述）表明需要将转换前的正方形变为转换后的正方形的转换方法。

## 样例 #1

### 样例输入 #1

```
3
@-@
---
@@-
@-@
@--
--@
```

### 样例输出 #1

```
1
```

## 提示

【数据范围】  
对于 $100\%$ 的数据，$1\le n \le 10$。

题目翻译来自 NOCOW。

USACO Training Section 1.2



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

string pre[15], ending[15],v[11],m[11];
int n;

bool issame(string str[])
{
	for (int i = 0; i < n; i++)
		if (str[i] != ending[i]) {
			return false;
		}
	return true;
}

void work1(string str[])
{
	for(int i=0;i<n;i++)
		for (int j = 0; j < n; j++)
		{
			v[j][n - i - 1] = str[i][j];
		}		
}

void work4(string str[])
{
	for(int i=0;i<n;i++)
		for (int j = 0; j < n; j++)
		{
			v[i][n-1-j] = str[i][j];
		}
	/*for (int i = 0; i < n; i++)cout << v[i] << endl;
	system("pause");*/
}

bool work5()
{
	work4(pre);
	for (int i = 0; i < n; i++)m[i] = v[i];
	work1(m);
	if (issame(v))return true;
	else {
		for (int i = 0; i < n; i++)m[i] = v[i];
		work1(m);
	}
	if (issame(v))return true;
	else {
		for (int i = 0; i < n; i++)m[i] = v[i];
		work1(m);
	}
	return issame(v);
}


int main()
{
	cin >> n;
	for (int i = 0; i < n; i++)cin >> pre[i],v[i]=m[i]=pre[i];
	for (int i = 0; i < n; i++)cin >> ending[i];
	work1(pre);
	if (issame(v)) {
		cout << 1;
		return 0;
	}
	else {
		for (int i = 0; i < n; i++)m[i] = v[i];
		work1(m);
	}
	if (issame(v))
	{
		cout << 2;
		return 0;
	}
	else
	{
		for (int i = 0; i < n; i++)m[i] = v[i];
		work1(m);
	}
	if (issame(v)) {
		cout << 3;
		return 0;
	}
	else
	{
		work4(pre);
	}
	if (issame(v)) {
		cout << 4;
		return 0;
	}
	else if (work5()) {
		cout << 5;
		return 0;
	}
	else if (issame(pre)) {
		cout << 6;
		return 0;
	}
	else cout << 7;
	return 0;
}
```


# 洛谷 P1601 A+B Problem（高精



# A+B Problem（高精）

## 题目描述

高精度加法，相当于 a+b problem，**不用考虑负数**。

## 输入格式

分两行输入。$a,b \leq 10^{500}$。

## 输出格式

输出只有一行，代表 $a+b$ 的值。

## 样例 #1

### 样例输入 #1

```
1
1
```

### 样例输出 #1

```
2
```

## 样例 #2

### 样例输入 #2

```
1001
9099
```

### 样例输出 #2

```
10100
```

## 提示

$20\%$ 的测试数据，$0\le a,b \le10^9$；

$40\%$ 的测试数据，$0\le a,b \le10^{18}$。



```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<vector>
#include<algorithm>
#include<cstdio>
#include<math.h>
#include <cstring>
using namespace std;
//vector<int> c;
vector<int> add(vector<int> a, vector<int> b)
{
	if (a.size() > b.size())return add(b, a);
	vector<int> c;

	int t = 0,n;
	for (int i = 0; i < a.size(); i++)
	{
		n = t / 10;
		t = a[i] + b[i] + n;
		c.push_back(t % 10);
	}
	for (int i = a.size(); i < b.size(); i++) {
		n = t / 10;
		t =b[i] + n;
		c.push_back(t % 10);
	}
	if (t >= 10)c.push_back(t / 10);
	return c;
}

int main()
{
	string m, n;
	vector<int>a, b;
	vector<int> c;
	cin >> m >> n;
	for (int i = m.size() - 1; i >= 0; i--)a.push_back(m[i]-'0');
	for (int i = n.size() - 1; i >= 0; i--)b.push_back(n[i]-'0');
	c = add(a, b);
	for (int i = c.size()-1; i >= 0; i--)cout << c[i];


}
```


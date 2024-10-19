# 洛谷 P1303 A*B Problem

# A*B Problem

## 题目背景

高精度乘法模板题。

## 题目描述

给出两个非负整数，求它们的乘积。

## 输入格式

输入共两行，每行一个非负整数。

## 输出格式

输出一个非负整数表示乘积。

## 样例 #1

### 样例输入 #1

```
1 
2
```

### 样例输出 #1

```
2
```

## 提示

每个非负整数不超过 $10^{2000}$。



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

bool cmp(vector<int> a, vector<int> b)
{
	if (a.size() != b.size())return a.size() > b.size();
	for (int i = a.size() - 1; i >= 0; i--) {
		if (a[i] != b[i])return a[i] > b[i];
	}
	return true;
}


vector<int> add(vector<int> a, vector<int> b)
{
	if (a.size() < b.size())return add(b, a);
	vector<int> c;

	int t = 0,n;
	for (int i = 0; i < b.size(); i++)
	{
		n = t / 10;
		t = a[i] + b[i] + n;
		c.push_back(t % 10);
	}
	for (int i = b.size(); i < a.size(); i++) {
		n = t / 10;
		t =a[i] + n;
		c.push_back(t % 10);
	}
	if (t >= 10)c.push_back(t / 10);
	return c;
}


vector<int> sub(vector<int> a, vector<int> b)
{
	int t = 0;
	vector<int> c;
	for (int i = 0; i < a.size(); i++)
	{
		t = a[i] - t;
		if (i < b.size())t -= b[i];
		c.push_back((t + 10) % 10);
		if (t < 0)t = 1;
		else t = 0;
	}
	while (c.size() > 1 && c.back() == 0)c.pop_back();
	return c;

}

vector<int> mul(vector<int> a, vector<int> b)
{
	if (a.size() < b.size())return mul(b, a);

	vector<int>c,v;
	int t = 0;
	for (int i = 0; i < b.size(); i++)
	{
		v.clear();
		for (int j = 0; j < i; j++)v.push_back(0);
		for (int j = 0; j < a.size(); j++)
		{
			if (b[i] == 0) {
				v.push_back(b[i]);
				break;
			}
			t = a[j] * b[i]+t/10;
			v.push_back(t % 10);
		}
		if (t >= 10)v.push_back(t / 10);
		if (i == 0)c = v;
		else c = add(v, c);
	}
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
	//减法
	/*if (cmp(a, b)) {
		vector<int>c = sub(a, b);
		for (int i = c.size() - 1; i >= 0; i--)cout << c[i];
	}
	else
	{
		vector<int>c = sub(b, a);
		cout << "-";
		for (int i = c.size() - 1; i >= 0; i--)cout << c[i];
	}*/
	c = mul(a, b);
	for (int i = c.size() - 1; i >= 0; i--)cout << c[i];
}
```


# luogu B3849 [GESP样题 三级] 进制转换





# [GESP样题 三级] 进制转换

## 题目描述

小美刚刚学习了十六进制，她觉得很有趣，想到是不是还有更大的进制呢？在十六进制中，用 `A` 表示 $10$、`F` 表示 $15$。如果扩展到用 `Z` 表示 $35$，岂不是可以表示 $36$ 进制数了嘛！

所以，你需要帮助她写一个程序，完成十进制转 $R$ 进制（$2\le R\le 36$）的工作。

## 输入格式

输入两行，第一行包含一个正整数 $N$，第二行包含一个正整数 $R$，保证 $1\le N\le 10^6$。

## 输出格式

输出一行，为 $N$ 的 $R$ 进制表示。

## 样例 #1

### 样例输入 #1

```
123
25
```

### 样例输出 #1

```
4N
```





```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<vector>
#include<algorithm>
#include<cstdio>
#include<math.h>
#include <cstring>
using namespace std;

char b[26];
int main()
{
	for (int i = 0; i < 26; i++)b[i] = (char)'A' + i;
	int num,v,n=0,a[100];
	cin >> num>>v;
	if (num < v) {
		cout << 0;
	}
	while (num >0)
	{
		a[n++] = num % v;
		num /= v;
	}
	for (int i = n-1; i >=0; i--)
	{
		if (a[i] < 10)cout << a[i];
		else cout << b[a[i]-10];
	}
	return 0;
}
```


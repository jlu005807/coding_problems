# P1217 [USACO1.5] 回文质数 Prime Palindromes

# [USACO1.5] 回文质数 Prime Palindromes

## 题目描述

因为 $151$ 既是一个质数又是一个回文数（从左到右和从右到左是看一样的），所以 $151$ 是回文质数。

写一个程序来找出范围 $[a,b] (5 \le a < b \le 100,000,000)$（一亿）间的所有回文质数。

## 输入格式

第一行输入两个正整数 $a$ 和 $b$。

## 输出格式

输出一个回文质数的列表，一行一个。

## 样例 #1

### 样例输入 #1

```
5 500
```

### 样例输出 #1

```
5
7
11
101
131
151
181
191
313
353
373
383
```

## 提示

Hint 1: Generate the palindromes and see if they are prime.

提示 1: 找出所有的回文数再判断它们是不是质数（素数）.


Hint 2: Generate palindromes by combining digits properly. You might need more than one of the loops like below.

提示 2: 要产生正确的回文数，你可能需要几个像下面这样的循环。


题目翻译来自NOCOW。

USACO Training Section 1.5


产生长度为 $5$ 的回文数：

```cpp
for (d1 = 1; d1 <= 9; d1+=2) {    // 只有奇数才会是素数
     for (d2 = 0; d2 <= 9; d2++) {
         for (d3 = 0; d3 <= 9; d3++) {
           palindrome = 10000*d1 + 1000*d2 +100*d3 + 10*d2 + d1;//(处理回文数...)
         }
     }
 }

```



```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<iostream>
#include<algorithm>
#include<stdio.h>
#include<math.h>
#include <string>


using namespace std;
bool isprime(int x) {
	if (x == 1 || x == 4)return false;
	if (x == 2 || x == 3)return true;
	if (x % 6 != 1 && x % 6 != 5)return false;
	for (int i = 5; i * i <= x; i++) {
		if (x % i == 0)return false;
	}
	return true;
}

int main() {
	long long a, b, p;
	cin >> a >> b;
	long a1, a2, a3, a4, a5;
	for (a1 = 1; a1 <= 9; a1 += 2) {
		if (isprime(a1) && (a1 >= a && a1 <= b))cout << a1 << endl;
	}
	if (a <= 11 && b >= 11)cout << 11 << endl;
	if(b>100)
	for (a1 = 1; a1 <= 9; a1 += 2)
		for (a2 = 0; a2 <= 9; a2++)
		{
			p = 100 * a1 + 10 * a2 + a1;
			if (isprime(p) && (p >= a && p <= b))cout << p << endl;
		}
	if(b>10000)
	  for (a1 = 1; a1 <= 9; a1 += 2)
		for (a2 = 0; a2 <= 9; a2++)
			for (a3 = 0; a3 <= 9; a3++) {
				p = 10000 * a1 + 1000 * a2 + 100 * a3 + 10 * a2 + a1;
				if (isprime(p) && (p >= a && p <= b))cout << p << endl;
			}
	if(b>1000000)
	for (a1 = 1; a1 <= 9; a1 += 2)
		for (a2 = 0; a2 <= 9; a2++)
			for (a3 = 0; a3 <= 9; a3++)
				for (a4 = 0; a4 <= 9; a4++) {
					p = 1000000 * a1 + 100000 * a2 + 10000 * a3 + 1000 * a4 + 100 * a3 + 10 * a2 + a1;
					if (isprime(p) && (p >= a && p <= b))cout << p << endl;
				}
	if(b>100000000)
	for (a1 = 1; a1 <= 9; a1 += 2)
		for (a2 = 0; a2 <= 9; a2++)
			for (a3 = 0; a3 <= 9; a3++)
				for (a4 = 0; a4 <= 9; a4++)
					for (a5 = 0; a5 <= 9; a5++) {
						p = 100000000 * a1 + 10000000 * a2 + 1000000 * a3 + 100000 * a4 + 10000 * a5 + 1000 * a4 + 100 * a3 + 10 * a2 + a1;
						if (isprime(p) && (p >= a && p <= b))cout << p << endl;
					}
}
```


# luogu P5723 【深基4.例13】质数口袋



# 【深基4.例13】质数口袋

## 题目描述

小 A 有一个质数口袋，里面可以装各个质数。他从 $2$ 开始，依次判断各个自然数是不是质数，如果是质数就会把这个数字装入口袋。

口袋的负载量就是口袋里的所有数字之和。

但是口袋的承重量有限，装的质数的和不能超过 $L$。给出 $L$，请问口袋里能装下几个质数？将这些质数从小往大输出，然后输出最多能装下的质数的个数，数字之间用换行隔开。

## 输入格式

一行一个正整数 $L$。

## 输出格式

将这些质数从小往大输出，然后输出最多能装下的质数个数，所有数字之间有一空行。

## 样例 #1

### 样例输入 #1

```
100
```

### 样例输出 #1

```
2
3
5
7
11
13
17
19
23
9
```

## 样例 #2

### 样例输入 #2

```
5
```

### 样例输出 #2

```
2
3
2
```

## 样例 #3

### 样例输入 #3

```
11
```

### 样例输出 #3

```
2
3
5
3
```

## 提示

数据保证，$1 \le L \le {10}^5$。



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
	if (x % 6 != 1 &&x % 6 != 5)return false;
	for (int i = 5; i * i <= x; i++) {
		if (x % i == 0)return false;
	}
	return true;
}

int main() {
	int l,num=0,sum=0;
	cin >> l;
	for (int i = 2;; i++) {
		if (isprime(i)) {
			if (sum + i <= l) {
				sum += i;
			}
			else break;
			num++;
			cout << i << endl;
		}
	}
	cout << num;
	return 0;
}
```


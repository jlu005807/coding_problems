# luogu P5707 【深基2.例12】上学迟到



# 【深基2.例12】上学迟到

## 题目描述

学校和 yyy 的家之间的距离为 *s* 米，而 yyy 以 *v* 米每分钟的速度匀速走向学校。

在上学的路上，yyy 还要额外花费 $10$ 分钟的时间进行垃圾分类。

学校要求必须在上午 $\textrm{8:00}$  到达，请计算在不迟到的前提下，yyy 最晚能什么时候出门。

由于路途遥远，yyy 可能不得不提前一点出发，但是提前的时间不会超过一天。

## 输入格式

一行两个正整数 $s,v$，分别代表路程和速度。

## 输出格式

输出一个 $24$ 小时制下的时间，代表 yyy 最晚的出发时间。

输出格式为 $\texttt{HH:MM}$，分别代表该时间的时和分。必须输出两位，不足前面补 $0$。

## 样例 #1

### 样例输入 #1

```
100 99
```

### 样例输出 #1

```
07:48
```

## 提示

对于 $100\%$ 的数据，$1 \le s,v \le 10^4$。



```cpp
#define _CRT_SECURE_NO_WARNINGS
#include<cctype>
#include<iostream>
#include<math.h>
#include<stdio.h>
using namespace std;

int main() {
	int  time;
	double s, v;
	cin >> s >> v;
	time = ceil(s / v) + 10;
	if (time <= 60)printf("07:%02d",60-time);
	else if (time < 60 * 8) {
		int v = (int)60 * 8 - time;
		printf("%02d:%02d", v / 60, v % 60);
	}
	else {
		int k = (int)60 * (8 + 24) - time;
		printf("%02d:%02d", k / 60, k % 60);
	}


}
```


# luogu B2139 区间内的真素数



# 区间内的真素数

## 题目描述

找出正整数 $M$ 和 $N$ 之间（$N$ 不小于 $M$）的所有真素数。

真素数的定义：如果一个正整数 $P$ 为素数，且其反序也为素数，那么 $P$ 就为真素数。

例如，$11$，$13$ 均为真素数，因为 $11$ 的反序还是为 $11$，$13$ 的反序为 $31$ 也为素数。

## 输入格式

输入两个数 $M$ 和 $N$，空格间隔。

## 输出格式

按从小到大输出 $M$ 和 $N$ 之间（包括 $M$ 和 $N$）的真素数，逗号间隔。如果之间没有真素数，则输出 `No`。

## 样例 #1

### 样例输入 #1

```
10 35
```

### 样例输出 #1

```
11,13,17,31
```

## 提示

$1 \le M \le N \le 100000$



```python
def is_prime(n):
    if n<2 or n==4:
        return False
    if n==2 or n==3 or n==5:
        return True
    if n%6!=1 and n%6!=5:
        return False
    for i in range(5, int(n**0.5)+1, 6):
        if n%i==0 or n%(i+2)==0:
            return False
    return True

m,n=input().split()
m=int(m)
n=int(n)
ans=""
for i in range(m,n+1):
    j=str(i)
    j=j[::-1]
    j=int(j)
    if is_prime(i) and is_prime(j):
        ans+=str(i)+","
if ans=="":
    print("No")
    exit()
ans=ans[:-1]
print(ans)
```




# luogu B2141 确定进制



# 确定进制

## 题目描述

$6\ \times 9=42$ 对于十进制来说是错误的，但是对于 $13$ 进制来说是正确的。即 $6_{(13)}\ \times 9_{(13)}=42_{(13)}$，而 $42_{(13)}=4\ \times 13^1+2\ \times 13^0=54_{(10)}$。

你的任务是写一段程序读入三个整数 $p,q$ 和 $r$，然后确定一个进制 $B(2 \le B \le 16)$ 使得 $p\ \times q=r$。如果 $B$ 有很多选择，则输出最小的一个。

例如：$p=11,q=11,r=121$，则有 $11_{(3)}\ \times 11_{(3)}=121_{(3)}$，因为 $11_{(3)}=1\ \times 3^1+1\ \times 3^0=4_{(10)}$ 和 $121_{(3)}=1\ \times 3^2+2\ \times 3^1+1\ \times 3^0=16_{(10)}$。对于进制 $10,$ 有 $11_{(10)}\ \times 11_{(10)}=121_{(10)}$。这种情况下，应该输出 $3$。如果没有合适的进制，则输出 $0$。

## 输入格式

一行，包含三个整数 $p,q,r$，相邻两个整数之间用单个空格隔开。

## 输出格式

一个整数：即使得 $p \times q=r$ 成立的最小的 $B$。如果没有合适的 $B$，则输出 $0$。

## 样例 #1

### 样例输入 #1

```
6 9 42
```

### 样例输出 #1

```
13
```

## 提示

$p,q,r$ 的所有位都是数字，并且 $1 \le p,q,r \le 10^6$。



```python
def change_to_ten(num,key):
    num=str(num)
    num=num[::-1]
    ans=0
    for i in range(len(num)):
        if int(num[i])>=key:
            return 9999
        ans+=int(num[i])*(key**i)
    return ans

p,q,r=input().split()
p=int(p)
q=int(q)
r=int(r)

for i in range(2,17):
    if change_to_ten(p,i)*change_to_ten(q,i)==change_to_ten(r,i):
        print(i)
        exit()
print("0")
```


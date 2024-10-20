# luogu B2143 进制转换



# 进制转换

## 题目描述

用递归算法将一个十进制整数 $X$（$1 \le X \le 10^9$）转换成任意进制数 $M$（$2\le M\le16$，$M$ 为整数）。

## 输入格式

一行两个数，第一个十进制整数 $X$，第二个为进制 $M$。

## 输出格式

输出结果。

## 样例 #1

### 样例输入 #1

```
31 16
```

### 样例输出 #1

```
1F
```

## 提示

**样例解释**。

将十进制 $31$ 转化为十六进制数。



```python
num=["0","1","2","3","4","5","6","7","8","9","A","B","C","D","E","F"]
def changejinzhi(n,key):
    ans=""
    while n>0:
        v=n%key
        n//=key
        ans+=num[v]
    return ans[::-1]

n,key=input().split()
n=int(n)
key=int(key)
ans=changejinzhi(n,key)
print(ans)
```


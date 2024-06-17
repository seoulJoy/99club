# 이항계수1

https://www.acmicpc.net/problem/11050

# 코드

## 내 코드

```
def factorial(x):
    if x == 0 or x == 1:
        return 1
    result = 1
    for i in range(2, x + 1):
        result *= i
    return result

def getResult(n, k):
    a = factorial(n)
    b = factorial(n-k)
    c = factorial(k)
    try:
        print (a//(b*c))
    except ZeroDivisionError:
        print(0)

n, k = map(int, input().split())
getResult(n, k)
```

## 다른 풀이

재귀 함수를 사용하여 더 직관적으로 풀 수 있다.
깊이가 깊어질 경우 스택 오버플로우가 발생 할 수 있으므로 주의.

```
import sys

def bino_coef(n, k):
    if k == 0 or n == k:
        return 1
    return bino_coef(n-1, k) + bino_coef(n-1, k-1)

input = sys.stdin.readline
print(bino_coef(*map(int, input().strip().split())))
```

# 회고

for문으로 반복 계산(팩토리얼 등)하는 풀이는 재귀 함수를 사용하는 것도 한번 고려해보자!

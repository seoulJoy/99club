# 다리놓기

https://www.acmicpc.net/problem/1010

# 코드

## 조합론

이항계수1(https://github.com/xxyoonxx/99club/blob/main/TIL16.md) 풀이에 크기 비교 로직만 추가

```
def factorial(x):
    if x == 0 :
        x = 1
    for _ in range(1, x):
        x *= _
    return x

def getResult(n,k):
    if k>n:
        n, k = k, n
    x = factorial(n)
    y = factorial(k)
    z = factorial(n-k)
    try:
        return x // (z * y)
    except ZeroDivisionError:
        return 1

for _ in range(int(input())):
    x,y = map(int, input().split())
    print(getResult(x,y))
```

## 동적 프로그래밍(Dynamic Programming)

```
def dp_b (n,m) :
    dp = [[1]*(m+1) for _ in range(m+1)]
    for i in range(2,m+1):
        dp[1][i]=i
    for i in range(2,n+1):
        for j in range(i+1,m+1):
            dp[i][j] = dp[i-1][j-1] + dp[i][j-1]
    return dp[n][m]

for _ in range(int(input())):
    west, east =  map(int, input().split())
    print(dp_b(west,east))
```

# References

[[백준][1010] - 다리놓기 python - GoS](https://night-knight.tistory.com/entry/%EB%B0%B1%EC%A4%801010-%EB%8B%A4%EB%A6%AC%EB%86%93%EA%B8%B0-python
)

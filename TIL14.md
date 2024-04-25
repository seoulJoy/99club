# 골드바흐 파티션

https://www.acmicpc.net/problem/17103

## 코드

### 1트 - 시간초과

```jsx
import sys
input = sys.stdin.readline

t = int(input())

def isPrime(x):
    arr_isPrime = [False,False] + [True] * x
    arr_prime = []
    for i in range(2,x):
        if arr_isPrime[i]:
            arr_prime.append(i)
        for j in range(i * 2, x, i):
            if j % i == 0:
                arr_isPrime[j] = False
    return arr_prime

for _ in range(t):
    n = int(input())
    arr = isPrime(n)
    cnt = 0
    for i in arr[:]:
        if (n-i) in arr[:]:
            arr.remove(i)
            if i != n-i:
                arr.remove(n-i)
            cnt += 1
    print(cnt)
```

### 2트 - 시간초과

```jsx
import sys
input = sys.stdin.readline

t = int(input())

arr_isPrime = [False,False] + [True] * 1000000
arr_prime = []
for i in range(2,1000000):
    if arr_isPrime[i]:
        arr_prime.append(i)
    for j in range(i * 2, 1000000, i):
        if j % i == 0:
            arr_isPrime[j] = False

for _ in range(t):
    n = int(input())
    arr = arr_prime[0:n+1]
    cnt = 0
    for i in arr[:]:
        if (n-i) in arr[:]:
            arr.remove(i)
            if i != n-i:
                arr.remove(n-i)
            cnt += 1
    print(cnt)
```

### 3트 - 통과

```jsx
import sys
input = sys.stdin.readline

t = int(input())

arr_isPrime = [False,False] + [True] * 1000000
for i in range(2,1000000):
    if arr_isPrime[i]:
        for j in range(i * 2, 1000000, i):
            if j % i == 0:
                arr_isPrime[j] = False

for _ in range(t):
    n = int(input())
    arr = arr_isPrime[0:n+1]
    cnt = 0
    for i in range(2, n//2+1):
        if arr[i] and arr[n-i]:
            cnt+=1
    print(cnt)
```

불필요한 변수를 모두 삭제하고 range의 end index도 나누기로 대폭 줄였더니 통과

### 모범코드

- 정수론 + 모두 메서드화

```python
import sys
input = sys.stdin.readline

def sosu():
    x = 999998
    xl = [0,0]+[1]*x
    for i in range(2,int(x**0.5)+1):
        if xl[i]:
            for j in range(i+i,x+1,i):
                xl[j] = 0
    return xl

def sum_sosu(m,l):
    res = 0
    for i in range(2,m//2+1):
        if l[i] == 1:
            if l[m - i] == 1:
                res += 1
    return res

l = sosu()
n = int(input())
for i in range(n):
    m = int(input())
    ans = sum_sosu(m,l)
    print(ans)
```

# 재귀를 이용한 풀이

## 1. 피보나치 수5

https://www.acmicpc.net/problem/10870

# 코드

## 내 코드

```python
def get_fibonacci(x):
    if x == 0 : return 0
    if x == 1 or x==2 : return 1
    x = get_fibonacci(x-1) + get_fibonacci(x-2)
    return x

print(get_fibonacci(int(input())))
```

## 모범 코드

```python
def fibo(n):
    if n <= 1:
        return n
    return fibo(n-1) + fibo(n-2)	# 앞 두 수의 합

n = int(input())
print(fibo(n))
```

# 회고

이 조건식이 너무 쓸데가 없었다..
그냥 n으로 묶어버리면 되는걸..

```python
    if x == 0 : return 0
    if x == 1 or x==2 : return 1
```

컴퓨터를 십분 활용해서 쉽게쉽게 풀어보자!!

# References

[https://velog.io/@hrzo1617/백준-10870-파이썬-피보나치-수-5](https://velog.io/@hrzo1617/%EB%B0%B1%EC%A4%80-10870-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98-%EC%88%98-5)

## 2. 재귀의 귀재

https://www.acmicpc.net/problem/25501

# 코드

```
x = 0
def recursion(s, l, r):
    global x
    x += 1
    if l >= r:
        return print(1, x)
    elif s[l] != s[r]: return print(0, x)
    else: return recursion(s, l+1, r-1)

def isPalindrome(s):
    return recursion(s, 0, len(s)-1)

for _ in range(int(input())):
    isPalindrome(input())
    x = 0
```

그냥 재귀함수 구경용 문제인 것 같다.

# 회고

생각해보니 recursion에서 return마다 나오는 print를 제거하고 이 부분에다가 써도 됐었는데..

```
for _ in range(int(input())):
    print(isPalindrome(input()))
```

반복, 공통부분은 무조건 짧게!

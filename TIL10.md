# 기사단원의 무기

https://school.programmers.co.kr/learn/courses/30/lessons/136798

## 사전지식

### 약수 구하기

1. O(N)

- 약수를 알고자 하는 수(N)를 1부터 N까지 나누어 떨어지는 값을 찾는다

```python
def getMyDivisor(n):

    divisorsList = []

    for i in range(1, n + 1):
        if (n % i == 0) :
            divisorsList.append(i)

    return divisorsList
```

2. O(√ N)

- N의 제곱근을 구한 후 1부터 제곱근까지 나누어 떨어지는 값을 찾는다
  - N = A*B 일 때, A==B일 경우가 있으므로 이를 따로 검사해주어야 한다.

```python
def getMyDivisor(n):

    divisorsList = []

    for i in range(1, int(n**(1/2)) + 1):
        if (n % i == 0):
            divisorsList.append(i) 
            if ( (i**2) != n) : 
                divisorsList.append(n // i)

    divisorsList.sort()
    
    return divisorsList
```

## 코드

### 내 코드

```python
def solution(number, limit, power):
    answer = 1
    for i in range(2, number+1):
        cnt = 0
        half = i ** (1/2)
        for j in range(1, int(half)+1):
            if i % j == 0:
                cnt += 1
        cnt *= 2
        if int(half) == half:
            cnt -= 1
        if cnt > limit:
            cnt = power
        answer += cnt
    return answer
```

### 모범 코드

```python
def solution(number, limit, power):
    divisor_num = []
    for i in range(1, number+1):
        cnt = 0
        for j in range(1, int(i**0.5) +1 ):
            if (i == j**2):
                cnt +=1
            elif (i%j == 0):
                cnt +=2
        divisor_num.append(cnt)
    res = [i if i <= limit else power for i in divisor_num ]
    return sum(res)
```

- 제곱근이 약수를 구하고자 하는 숫자의 제곱과 같으면 1을 더하고, 그렇지 않으면 2를 더함
- limit 변수 검사를 list안에서 수행
  - `res = [i if i <= limit else power for i in divisor_num ]`: divisor_num의 요소인 i를 넣되, i가 limit보다 작거나 같아야하며, i가 limit보다 크면 power를 i로 설정

# 회고
모범 코드와 비슷하게 푼 것 같다. 아직도 약수와 소수 구하는 공식이 약간 헷갈리는데 양치기로 풀다 보면 감이 익을 듯..
for문과 조건절을 함께 쓰는 파이썬 문법에도 이제 익숙해 질 때가 된 것 같다.
꾸준히 풀어보자

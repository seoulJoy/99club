# 사전지식

## 피보나치 수

모든 항이 바로 앞 두 항의 합인 수열
첫번째 항, 두번째 항은 0(혹은 1), 1로 고정이다.
0, 1, 2, 3, 5, 8, 13...
n = n-2 + n-1

# 문제

[프로그래머스 - 멀리뛰기](https://school.programmers.co.kr/learn/courses/30/lessons/12914)

## 코드

```python
def solution(n):
    a, b = 0, 1
    for i in range(n):
        a, b = b, a+b
    return b%1234567
```

## 회고

냅다 문제 해결방법을 생각하는 것보다는 최소 1~5번째까지는 손으로 풀어보는 것이 좋을 것 같다.
보통 문제에서 자주 사용되는 패턴이 정해져있는 듯.

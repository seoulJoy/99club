# 내 답안

## 오답

```python
def solution(prices):
    answer = []
    for i in range(len(prices)):
        n = 0
        for j in range(i+1, len(prices)):
        # 다음 요소가 기준 요소보다 클 때 cnt가 카운트 되지 않음.
        # 기준요소가 클 때에도 cnt후 append 및 cnt 초기화가 되어야 함
            if prices[i] <= prices[j]:
                n += 1
        answer.append(n)
    return answer
```

## 오답

```python
def solution(prices):
    answer = []
    for i in range(len(prices)):
        cnt = 0
        for j in range(i+1, len(prices)):
            cnt += 1
            # 이전 요소가 다음 요소보다 클 때에만 append가 됨
            if prices[i] > prices[j]:
                answer.append(cnt)
                break
    answer.append(0)
    return answer
```

## 정답

```python
def solution(prices):
    answer = []
    for i in range(len(prices)):
        cnt = 0
        for j in range(i+1, len(prices)): # 1~2
            cnt += 1
            if prices[i] > prices[j]:
                break
        answer.append(cnt)
    return answer
```

# 모범 답안

## Brute Force

```python
def solution(prices):
    answer =[0] * len(prices)
    for i in range(len(prices)):
        for j in range(i+1, len(prices)):
            if prices[i] <= prices[j]:
                answer[i]+=1
            else:
                answer[i]+=1
                break
    return answer
```

## Queue

```python
from collections import deque

def solution(prices):
    answer = []
    prices_q = deque(prices)
    
    while prices_q:
        price = prices_q.popleft()
        time = 0
        for q in prices_q:
            time += 1
            if price > q:
                break
        answer.append(time)
    return answer
```

## Stack

```python
def solution(prices):
    length = len(prices)
    answer = [ i for i in range (length - 1, -1, -1)]

    stack = [0]
    for i in range (1, length):
        while stack and prices[stack[-1]] > prices[i]:
            j = stack.pop()
            answer[j] = i - j
        stack.append(i)
    return answer
```

### 접근 방법

1. 바로 옆(다음) 요소가 현재 요소보다 작을 때, 몇 개를 거쳐왔는 지 계산해야함
1-1. answer의 맨 마지막 값은 0으로 고정
2. 다음 요소가 현재보다 작을 때, 여태껏 지나온 요소도 계산이 되어야 함
2-1. 리스트를 따로 선언하여 몇 개 요소를 거쳐왔는지 계산
- 참고용 덧글

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/c0897b1f-0bb0-44e4-9c89-cfeb309ac3e7/fdb8e9aa-5607-4bba-bbd5-fd584e216bbf/Untitled.png)

```
stack = 현재 값보다 작은 값이 나오는 인덱스 계산용

case1.
    prices = [1,2,3,2,3]
    length = 5
    answer = [4,3,2,1,0]
    stack = [0]

    for i in range (1,5): # 마지막 값은 항상 0이므로 length-1까지만
    1.
        while stack and prices[stack[-1]] > prices[i]:
            # prices[0] > prices[1] 1 > 2이므로 pass
        stack.append(1) # stack = [0,1]
    2.
        while stack and prices[1] > prices[2]: # 2 > 3이므로 pass
        stack.append(2) # stack = [0,1,2]
    3.
        while stack and prices[2] > prices[3]: # 3 > 2이므로 수행
            j = stack.pop() # j = 2, stack = [0,1]
            answer[j] = i - j # answer[2] = 3 - 2 / answer = [4,3,1,1,0]
        stack.append(3) # stack = [0,1,3]
    4.
        while stack and price[3] > prices[4]: # 2 > 3이므로 pass
        stack.append(4) # stack = [0,1,3,4]

# return [4,3,1,1,0]

case2.
    prices = [2,6,1,1]
    length = 4
    answer = [3,2,1,0]
    stack = [0]

    for i in range (1,4): # 마지막 값은 항상 0이므로 length-1까지만
    1.
        while stack and prices[0] > prices[1]: # 2 > 6 이므로 pass
        stack.append(1) # stack = [0,1]
    2.
        while stack and prices[1] > prices[2]: # 6 > 1 이므로 수행
            j = stack.pop() # j = 1, stack = [0]
            answer[j] = i - j # answer[1] = 2 - 1 / answer = [3,1,1,0]
        # 아직 while문 실행중이므로 stack.append는 돌지 않음
    3.
        while stack and prices[1] > prices[3]: # 6 > 1 이므로 수행
            j = stack.pop() # j = 1, stack = []
            answer[j] = i - j # answer[0] = 3 - 1 / answer = [2,1,1,0]
        # 아직 while문 실행중이므로 stack.append는 돌지 않음

# return [2,1,1,0]

```

# References

[Programmers | 주식가격 - Python](https://velog.io/@soo5717/프로그래머스-주식가격-Python#21-주식가격)

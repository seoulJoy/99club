# 프로세스

https://school.programmers.co.kr/learn/courses/30/lessons/42587

## 내 코드

```python
def solution(priorities, location):
    answer = 0
    while True:
        if max(priorities) > priorities[0]:
            priorities.append(priorities.pop(0))
            if location == 0:
                location = len(priorities)-1
            else:
                location -= 1
        elif max(priorities) == priorities[0]:
            answer += 1
            if location==0:
                break
            else:
                priorities.pop(0)
                location -= 1
    return answer
```

## 모범 코드

```python
def solution(priorities, location):
    queue =  [(i,p) for i,p in enumerate(priorities)]
    answer = 0
    while True:
        cur = queue.pop(0)
        if any(cur[1] < q[1] for q in queue):
            queue.append(cur)
        else:
            answer += 1
            if cur[0] == location:
                return answer
```

- `enumerate()` : 인덱스와 원소로 이루어진 튜플을 생성해줌
- `any()` : 하나라도 True면 True. or
    - `all()` : 모두 Ture여야 True. and

```python
# priorities = [1,1,9,1,1,1]
queue = [(0, 1), (1, 1), (2, 9), (3, 1), (4, 1), (5, 1)]

# cur = queue.pop(0)
cur = (0,1)
queue = [(1, 1), (2, 9), (3, 1), (4, 1), (5, 1)] # queue[0]을 pop

if any(cur[1] < q[1] for q in queue):
'''
cur[1] = 1 # 튜플의 두번째 요소를 가리킴
if any(cur[1] < q[1] for q in queue):
# 튜플의 두번째 요소(pop한 value)와 for을 이용해 모든 queue의 요소 비교
# queue 요소 중 하나라도 cur보다 크다면 cur를 queue의 뒤로 보냄
'''

else: # queue에서 cur가 가장 큰 값이라면 해당값의 return이 이루어지므로 answer += 1
if cur[0] == location: # cur의 첫번째요소(인덱스)가 location과 같다면 answer 반환
```

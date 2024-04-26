# 도키도키 간식 드리미

https://www.acmicpc.net/problem/12789

# 코드

- python기본 list 사용 - 31120KB, 40ms

```python
import sys
input = sys.stdin.readline

n = int(input())
queue = list(map(int, input().split()))
stack=[]
cnt = 1

while queue:
    if queue[0]==cnt:
        queue.pop(0)
        cnt += 1
    else:
        stack.append(queue[0])
        queue.pop(0)
    while stack and stack[-1]==cnt:
        stack.pop(-1)
        cnt+=1
if stack:
    print("Sad")
else:
    print("Nice")
```

- deque 라이브러리 사용 - 34008KB, 72ms

```python
import sys
from collections import deque
input = sys.stdin.readline

n = int(input())
queue = deque(list(map(int, input().split())))
stack=deque([])
cnt = 1

while queue:
    if queue[0]==cnt:
        queue.popleft()
        cnt += 1
    else:
        stack.append(queue[0])
        queue.popleft()
    while stack and stack[-1]==cnt:
        stack.pop()
        cnt+=1
if stack:
    print("Sad")
else:
    print("Nice")
```

기본 python list형이 더 빠른 것을 확인 할 수 있다.(왤까..)

# 풀이

문제에 힌트가 들어있다.

```
1. 큐
현재 1열로 줄을 서있고, 맨 앞의 사람만 이동이 가능
2. 스택
이 라인과 대기열의 맨 앞 사람 사이에는 한 사람씩 1열이 들어갈 수 있는 공간이 있다.
현재 대기열의 사람들은 이 공간으로 올 수 있지만 반대는 불가능하다. 
```

 아래와 같이 접근했다.

```
1. 다음 순번을 세는 변수 선언(cnt)
2. 큐에서 가장 앞 값(pop)과 cnt 비교
	2-1. 같으면 큐에서 pop. cnt 1증가
	2-2. 다르면 큐에서 pop, 스택으로 push.
	2-3. 스택에 가장 최근에 넣은 값(index:-1)이 다음 순번이라면 pop후 cnt 1증가
		2-3-1. 가장 최근값이 다음순번이 아니라면 다시 2-1로 돌아가서 검사
					큐는 2-1에서 pop했으므로 다음 인덱스가 가장 맨 앞으로 나와서 기다리게 됨
```

큐나 스택의 가장 앞 값만 비교하면 되므로 모든 원소를 순회하는 for문을 사용하지 않아도 된다.

# References

[[ 파이썬(python) ] 백준 12789 - 도키도키 간식드리미](https://ywtechit.tistory.com/194)

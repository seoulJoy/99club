## 코드

```python
import sys
from collections import deque

input = sys.stdin.readline

n = int(input())
paper = deque(list(map(int, input().split())))
index = deque([i for i in range(1, n + 1)])
poped = []

while paper:
    num = paper.popleft()
    poped.append(index.popleft())
    if num > 0:
        paper.rotate(-(num-1))
        index.rotate(-(num-1))
    else:
        paper.rotate(-num)
        index.rotate(-num)
print(*poped)
```

Rotate는 index를 그대로 둔 채 큐 안의 값만 회전시킨다. `rotate(음수)` 는 왼쪽으로, `rotate(양수)`는 오른쪽으로 값만큼 회전시키므로, 다른 포인터를 사용할 필요 없이 쉽게 값을 구할 수 있다.

# References

[[Python] 백준 2346 풍선 터뜨리기 (Deque)](https://velog.io/@hygge/Python-백준-2346-풍선-터뜨리기-deque)

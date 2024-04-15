# 뒤에 있는 큰 수 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/154539

나보다 뒤에 있는 수 중에 큰 수가 있다면 그 수를 return하고, 없다면 -1 반환

## 모범 코드

```python
def solution(numbers):
    stack = []
    answer = [-1] * len(numbers)

    for i in range(len(numbers)):
            while stack and numbers[stack[-1]] < numbers[i]:
                answer[stack.pop()] = numbers[i]
            stack.append(i)
    
    return answer
```

1. 검사할 index를 차례로 stack에 넣음
2. stack에 들어간 index와 numbers의 숫자 비교. 여기서 i는 다음 index를 가르키게 됨
  2-1. 뒤에 값이 작으면 stack에 그 뒷 index를 넣음
  2-2. 뒤에 큰 값이 나오면 해당 수를 검사중인 index에 넣음

### 출처
https://aiday.tistory.com/86

# 회고

솔직히 이해가 아직도 잘 안된다..
이전에도 비슷한 문제 풀었던 적 있었는데 그때도 풀지 못했고 지금도 감도 잡지 못하였다..
stack을 포인터처럼 이용해서 index를 처리하는 것이 핵심 같다.
잘 연구해보자

.
# 햄버거 만들기

https://school.programmers.co.kr/learn/courses/30/lessons/133502?language=python3

요소에서 일정한 순서가 존재하는지 찾아야 하므로 Stack을 사용하는 것 까지는 이해가 됐으나, 햄버거가 1-2-3-1로 1이 중복으로 들어가 있는 상태였다. 우선 배열을 문자열로 바꿔서 1231(햄버거)를 삭제하는 방향으로 진행해보았다.

## 문자열치환(틀린 코드)

```python
hamburger = str(1231)
ingredient = "".join(map(str,ingredient))
cnt = 0
while hamburger in ingredient:
        cnt += 1
        ingredient = ingredient.lstrip('1231')
        #ingredient.replace('1231',"")
print(cnt)
```

### 진행하면서 마주했던 문제

1. 주석처리한 ingredient.replace('1231',"")처럼 코드를 작성할 경우 replace가 ingredient에 적용되지 않으므로, 반드시 변수를 선언해서 replace를 실행해야 한다.
2. replace나 lstrip은 원하는 문자열을 하나씩 지워주지 않는다.. 즉, 12311231이 주어지면 한 큐에 0이 된다는 것

## 브루트포스(틀린 코드)

```python
order = 1
answer = 0
for i in ingredient:
    if order == i:
        order += 1
    elif order == 4 and i == 1:
        answer += 1
        order = 1
print(answer)
```

순서대로가 아닌, ingredient에 1,2,3,1만 포함되어있으면 카운트를 해버리므로 틀린 코드

## stack 사용

```python
def solution(ingredient):
    s = []
    cnt = 0
    for i in ingredient:
        s.append(i)
        if s[-4:] == [1, 2, 3, 1]:
            cnt += 1
            for _ in range(4):
                s.pop()
    return cnt
# 출처: https://chan-lab.tistory.com/33 [은공지능 공작소:티스토리]
```

- ingredient 요소를 하나씩 stack에 쌓음
  - stack요소를 4개씩 잘라서 비교해서 햄버거가 완성되면 count를 더하고 해당 요소들을 pop

```python
s = [1, 2, 3, 4, 5]
print(s[3:]) # 4번째 요소(3번째 인덱스)부터 끝까지 count. [4, 5]
print(s[-3:]) # 끝에서 3번째 요소부터 끝까지 count. [3, 4, 5]
```

## 회고

아직 슬라이싱의 사용법과 스택, 힙에 대한 개념이 부족 한 것 같다.
스택, 힙은 언제나 응용이 너무 안되서 비슷한 류의 문제를 최대한 많이 풀어보는 것이 중요할 듯..

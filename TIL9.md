# 둘만의 암호

https://school.programmers.co.kr/learn/courses/30/lessons/155652?language=python3

## 내 코드

```python
def solution(s, skip, index):
    alphabet = "abcdefghijklmnopqrstuvwxyz"
    answer = ""
    for i in skip:
        alphabet = alphabet.replace(i, "")
    for i in s:
        idx = alphabet.index(i)
        try:
            answer += alphabet[idx+index]
        except:
            new_idx = (index+idx)%len(alphabet)
            answer += alphabet[new_idx]
    return answer
```

## 모범 코드

```python
def solution(s, skip, index):
    alpha = "abcdefghijklmnopqrstuvwxyz"
    answer = ""
    for i in list(skip):
        alpha = alpha.replace(i,"")

    for a in s:
        answer += alpha[(alpha.find(a) + index) % len(alpha)]
    return answer
```

## 회고

except가 필요가 따로 없었구나..
하지만 다음에도 비슷한 경우가 나오면 그 때도 try except를 쓸 것 같다..

# JadenCase 문자열 만들기

https://school.programmers.co.kr/learn/courses/30/lessons/12951

## 내 코드

```python
def solution(s):
    s = list(s)
    for i in range(len(s)):
        if (i==0 and s[i]!=" ") or (i>=1 and s[i-1]==" "):
            if s[i].isalpha():
                s[i]=s[i].upper()
        else:
            s[i]=s[i].lower()
    s = "".join(s)
    return s
```

## 모범 코드

```python
def solution(s):
    return " ".join([word[0].upper() + word[1:].lower() if word else word for word in s.split(" ")])
```

1. 문자열 s를 공백으로 쪼개서 변수 word로 for문을 돌린다
  Abc()Def->["Abc","Def"]

  1-1. 공백이 중복될 경우 아래처럼 문자열이 생성되므로 처리가 필요
    Abc()()Def->["Abc"," ","Def"]
    
2-1. word가 빈칸이 아니라면 answer에 word[0].upper() + word[1:].lower() 삽입

2-2. word가 빈칸이라면 answer에 word 그대로 삽입

### 출처
[https://jaehwaseo.tistory.com/17](프로그래머스 JadenCase 문자열 만들기 파이썬(python) - 입맛대로)
[https://shoark7.github.io/programming/python/about-list-comprehension-python]([Python] list comprehension에 대한 즐거운 이해 - sunghwan park)

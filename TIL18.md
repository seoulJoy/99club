# 영단어 암기는 괴로워

https://www.acmicpc.net/problem/20920

# 코드

## 내 코드

메모리 68280KB / 시간 376ms

```python
import sys
input = sys.stdin.readline

def sort_key(item):
    return (-item[1][1], -item[1][0], item[0])

n,m = map(int,input().split())
word_dict = {}
for _ in range(n):
    word = input().rstrip()
    if len(word) >= m:
        if word not in word_dict:
            arr = [len(word),1]
        else:
            arr = [len(word),word_dict[word][1]+1]
        word_dict[word] = arr
sorted_keys = [key for key, _ in sorted(word_dict.items(), key=sort_key)]
print('\n'.join(sorted_keys))
```

- `sorted_keys = [key for key, _ in sorted(word_dict.items(), key=sort_key)]`
  - `sorted(word_dict.items(), key=sort_key)`: 딕셔너리의 모든 값(word_dict.items())을 sort_key순으로 정렬 
    - `word_dict.items()`: 딕셔너리의 모든값을 (키, 값)쌍으로 반환 ex)[('appearance', [10, 1]), ('append', [6, 1]), ('attendance', [10, 1]), ('swift', [5, 3]), ('mouse', [5, 2]), ('wallet', [6, 1])]
    - sort_key의 `(-item[1][1], -item[1][0], item[0])`:
      1) 두번째 요소([10,1])의 두번째 값(1)을 내림차순 정렬
      2) 두번째 요소([10,1])의 첫번째 값(1)을 내림차순 정렬
      3) 첫번째 요소(appearance)를 오름차순으로 정렬
  - sorted에서 반환된 값은 튜플형식이므로 value를 _에 넣고 명시한 key만 sorted_keys에 삽입

### 챗GPT 개선판

메모리 59740KB / 시간 348 ms

```python
import sys

input = sys.stdin.readline

def sort_key(item):
    return (-item[1], -len(item[0]), item[0])

n, m = map(int, input().split())
word_dict = {}

for _ in range(n):
    word = input().rstrip()
    if len(word) >= m:
        if word not in word_dict:
            word_dict[word] = 1
        else:
            word_dict[word] += 1

sorted_words = sorted(word_dict.items(), key=sort_key)

for word, _ in sorted_words:
    print(word)
```

단어 길이를 굳이 넣지 않아도 key값으로 한번에 구해서 정렬 기준으로 쓸 수 있기 때문에 단순한 {키:값}형태의 딕셔너리가 성립한다.

## 모범코드

```python
import sys
n, m = map(int, input().split())
note = dict()
for _ in range(n):
    s = sys.stdin.readline().strip()
    if len(s) >= m:
        if s in note:
            note[s] += 1
        else:
            note[s] = 1
note = sorted(note.items(), key=lambda x: (-x[1],-len(x[0]),x[0]))
for i in note:
    print(i[0])
```

람다식을 사용해서 더 가독성있게 정리된 코드

# 회고

입력을 받음과 동시에 단어 길이를 검사 한 것과 정렬 관련 코드를 함수화 한 것이 시간을 줄이는데 도움이 된 것 같다.
딕셔너리를 어느 상황에서 써야하는지 약간 알 듯 말 듯
정렬은 아직도 익숙치 않아서 찾아보면서 풀어나갔다..
다음에는 겁먹지말고 람다식도 써보자

# References

https://minchul-son.tistory.com/235

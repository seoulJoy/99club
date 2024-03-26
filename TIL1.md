# 99클럽 코테 스터디 1일차 TIL enumerate

[https://school.programmers.co.kr/learn/courses/30/lessons/178871?language=python3](https://school.programmers.co.kr/learn/courses/30/lessons/178871?language=python3)

# 코드

```python
def solution(players, callings):
    player_dict = {player: idx for idx, player in enumerate(players)}

    for call in callings:
        idx = player_dict[call]

        players[idx], players[idx-1] = players[idx-1], players[idx]

        player_dict[players[idx]] = idx
        player_dict[players[idx-1]] = idx-1

    return players
```

# enumerate

- 리스트의 원소에 순서값(index)를 부여해주는 함수

 ## 사용법

- 기본

```python
# for문의 in 뒷부분을 enumerate()로 감싸서 사용
for i in enumerate(['A','B','C','D']):
  print(i)
'''
출력값
(0, 'A')
(1, 'B')
(2, 'C')
'''
```

- dictionary화

```python
arr = [C,B,A,B,C,C]
dict = {char:idx for idx,char in enumerate(arr)}
'''
# 출력값
{C: 5, B: 3, A: 2}
'''
```

[https://ctkim.tistory.com/entry/python-enumerate-function](https://ctkim.tistory.com/entry/python-enumerate-function)

list 요소 별 개수를 count해서 dictionary화 할 때, 요소의 인덱스와 함께 묶어서 새로운 자료형을 만들 때 주로 사용한다.

# 회고

파이썬 이전에 자바를 배울 때도 개념으로만 짚고 넘어가고 한번도 사용해보지 않아 생소했다.
잘 숙지해두었다가 list와 인덱스를 함께 이용할 때 유용하게 사용해야겠다.

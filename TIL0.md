# 99클럽 코테 스터디 0일차 TIL 딕셔너리&해시

# 딕셔너리/해시

- Key에 Value를 저장하는 구조(키-값 쌍 구조)
- 고정된 요소의 갯수를 셀 때 이용

https://jyj98020.tistory.com/47

# 오늘의 학습 키워드

## 딕셔너리/해시

- 임의 길이의 데이터를 고정 길이 데이터로 매핑하는 함수
    - key: 원래 데이터
    - hash value: 매핑 후 데이터 값
    - hashing: 매핑하는 과정
- Key에 Value를 저장하는 구조(키-값 쌍 구조)

https://jyj98020.tistory.com/47

https://amazelimi.tistory.com/entry/Python-해시Hash란-무엇인가feat-Dictionary-자료구조

# 공부 한 내용 정리

코딩 테스트에서는 고정된 요소의 갯수를 셀 때 주로 이용하는 것 같다.

다른 자료구조보다 월등히 빠르므로 key값이 많지 않을 때 적극적으로 이용해야 될 것 같다.

# 회고

- 어떤 문제가 있었고, 나는 어떤 시도를 했는지
    
    우선 문제가 길어서 이해 하는데 시간을 많이 썼다.
    
    무작정 입/출력을 분석하다가 문제를 다시 읽어보느라 시간이 지체되었다.
    
    `문제 훑어보기 > 입/출력 분석 > 문제 정독`  순으로 해결하는 것이 나에게 제일 맞는 것 같다. 
    
- 어떻게 해결했는지
    
    입출력을 꼼꼼히 분석해서 코드를 짜기 전 수학문제처럼 풀어보고, 그 과정에서 반복되는 풀이방법을 코드화 했다.
    
- 무엇을 새롭게 알았는지
    
    `dictionary.keys()` : 딕셔너리의 key값만 리스트화해서 return
    
    `dictionary.values()`: 딕셔너리의 value값만 리스트화해서 return
    
    `dictionary.items()`: 딕셔너리의 key, value를 튜플 형태로 return
    
    `list.sort()` : list 자체를 sort해서 반환(원본 list 순서가 바뀜)
    
    `sorted(list)`: sort한 list 반환(원본 list 순서가 바뀌지 않음)
    
- 내일 학습할 것은 무엇인지
    
    점점 lambda식에 대한 거부감을 줄일 것이다.

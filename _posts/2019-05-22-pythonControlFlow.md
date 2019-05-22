---
layout: post
title:  "python 데이터 구조"
date:   2019-05-22 09:10:00 +0800
categories: python
tag: python, controlFlow
comment: true
---
* content
{:toc}
지난 시간에 이어서 이번엔 python의 제어문 대하여 알아보겠습니다. [유다시티 파이썬 강좌](https://www.udacity.com/course/introduction-to-python--ud1110)에서 계정을 만들고 'start free course'를 눌러주세요.

# If statement
```
if season == 'spring':
    print('plant the garden!')
elif season == 'summer':
    print('water the garden!')
elif season == 'fall':
    print('harvest the garden!')
elif season == 'winter':
    print('stay indoors!')
else:
    print('unrecognized season')
```

파이썬의 if문은 `if, elif, else:`를 사용합니다. 주의할 점은 보통 다른 언어에서 코드블럭은 중괄호를 이용하는데 파이썬에서는 들여쓰기를 이용해서 코드블럭을 만듭니다. 탭이나 스페이스를 이용해도 되지만 파이썬 공식 가이드에서는 4스페이스를 사용하라고 하고, 파이썬3에서는 탭과 스페이스를 섞어서 쓰면 안됀다고 합니다.

# 제어문에 boolean표현하기

파이썬에서 논리연산자는 `and, or, not`이라고 했었죠? 논리연산자를 사용할때 주의할 점이 있습니다.

1. 좌우에 boolean값을 사용해라
```
# Bad example
if weather == "snow" or "rain":
    print("Wear boots!")
```
파이썬 컴파일 오류는 없지만 or 오른쪽에 boolean값이 아니라서 적절한 표현이 아닙니다.

2. `== True`, `== false`같은 것은 쓰지 말라

```
# Bad example
if is_cold == True:
    print("The weather is cold!")
```
`is_cold`가 boolean값이라면 굳이 비교할 필요가 없습니다.
```
# Good example
if is_cold:
    print("The weather is cold!")
```

## truth value

c언어에서 0이 거짓을 의미하고 나머지 수가 참을 의미하죠? 파이썬에서도 기본적으로 거짓을 의미하는 값들이 있습니다.
- `None` and `False`
- `0`, `0.0`, `0j`, `Decimal(0)`, `Fraction(0,1)`
- `""`, `()`, `[]`, `set()`, `range(0)`
```
errors = 3
if errors:
    print("You have {} errors to fix!".format(errors))
else:
    print("No errors to fix!")
```
여기서 변수 `errors`는 참을 의미합니다.

# For Loops
For문의 용법은 두가지가 있습니다. 어떤 데이터구조의 원소를 하나하나 참조할때 사용하기도 하고 그냥 뭔가 반복적으로 실행 할때 사용하기도 합니다. 비슷하게 들리지만 조금 다릅니다. 자세히 볼까요?
```
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']
for city in cities:
    print(city)
print("Done!")
```
`for in`을 사용해서 list의 원소 하나하나 참조 하고있습니다. 이것은 string, list, tuple, dictionary등 모두 가능합니다.

```
for i in range(3):
    print("Hello!")
```
뭔가 그냥 반복적으로 실행 하는 방법입니다. 이떄 range함수를 사용해서 print문을 세번 반복합니다.

## range(start = 0, stop, step = 1)

range함수는 세 매개변수가 있습니다. 그러나 첫번째와 세번째는 선택사항입니다. 그러니까 start 부터 stop까지 step만큼 증가한다는 거죠

- `range(4)` -> `0,1,2,3`
- `range(2,6)` -> `2,3,4,5`
- `range(1,10,2)` -> `1,3,5,7,9`

## 리스트 만들기

두가지 방법이 있습니다.
```
# Creating a new list
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']
capitalized_cities = []

for city in cities:
    capitalized_cities.append(city.title())
```
```
cities = ['new york city', 'mountain view', 'chicago', 'los angeles']

for index in range(len(cities)):
    cities[index] = cities[index].title()
```
# Dictionary만들기

```
book_title =  ['great', 'expectations','the', 'adventures', 'of', 'sherlock','holmes','the','great','gasby','hamlet','adventures','of','huckleberry','fin']
```
이런 리스트로 dictaionary를 만들어 봅시다

## `[ ]`인덱싱 이용
1. empty dictionary만들기
```
word_counter = {}
```
2. 리스트를 반복해서 dictionary에 추가하기 그런데 같은 키값은 중복제외 하기위해 if문을 사용합니다.
```
for word in book_title:
    if word not in word_counter:
        word_counter[word] = 1
    else:
        word_counter[word] += 1
```

## `get`메소드 이용
이건 더 간단합니다.
```
for word in book_title:
    word_counter[word] = word_counter.get(word, 0) + 1
```
get메소드의 두번째 인자 0은 word에 해당하는 키가 없을 때 기본적으로 0을 리턴해달라는 뜻입니다.

# Dictionary순회 하기

```
cast = {
           "Jerry Seinfeld": "Jerry Seinfeld",
           "Julia Louis-Dreyfus": "Elaine Benes",
           "Jason Alexander": "George Costanza",
           "Michael Richards": "Cosmo Kramer"
       }
for key in cast:
  print(key)
```
그냥 똑같습니다. 그런데 키만 이용해서 순회하는 방법이 있고 키, 값모두 이용해서 순회하는 방법도 있습니다.
```
for key, value in cast.items():
    print("Actor: {}    Role: {}".format(key, value))
```

# while문
```
card_deck = [4, 11, 8, 5, 13, 2, 8, 10]
hand = []

# adds the last element of the card_deck list to the hand list
# until the values in hand add up to 17 or more
while sum(hand)  < 17:
    hand.append(card_deck.pop())
```
## break, continue
파이썬에서도 break와 continue문을 사용할 수 있습니다.

# zip, Enumerate

## zip

iterable한 자료형을 합해서 새로운 튜플을 반환합니다.`list(zip(['a', 'b', 'c'], [1, 2, 3]))` 의 결과는 `[('a', 1), ('b', 2), ('c', 3)]`이지요

반대로 `upzip`할 수도 있습니다.
```
some_list = [('a', 1), ('b', 2), ('c', 3)]
letters, nums = zip(*some_list)
```

## Enumerable
list의 색인과 값을 포함하는 튜플의 반복자를 반환하는 함수 입니다.

```
letters = ['a', 'b', 'c', 'd', 'e']
for i, letter in enumerate(letters):
    print(i, letter)
```
```
0 a
1 b
2 c
3 d
4 e
```
# List축약

```
capitalized_cities = []
for city in cities:
    capitalized_cities.append(city.title())
```
위아래 표현은 같은 거라고 합니다. 신기하네요
```
capitalized_cities = [city.title() for city in cities]
```
축약은 대괄호 안에 표현해야합니다. 결과 `city.title()`이 맨 앞에 오고 뒤에 `cities`의 각 원소를 순회하는 변수 `city`가 있네요 for문 안에 if문도 사용할 수 있다고 합니다.

```
squares = [x**2 for x in range(9) if x % 2 == 0]
```
그러면 결과는 `[0, 4, 16, 36, 64]`가 되지요 else문을 쓸때는 주의할 점이 있습니다.
```
squares = [x**2 for x in range(9) if x % 2 == 0 else x + 3]
```
이렇게 쓰면 오류고 if문 전체를 앞으로 빼야 합니다.
```
squares = [x**2 if x % 2 == 0 else x + 3 for x in range(9)]
```
> 참고 : https://www.udacity.com/course/introduction-to-python--ud1110

작성자 : 이석원

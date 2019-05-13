---
layout: post
title:  "python 데이터 구조"
date:   2019-05-12 08:02:00 +0800
categories: python
tag: python, datastructure
comment: true
---
* content
{:toc}

지난 시간에 이어서 이번엔 python의 데이터 구조에 대하여 알아보겠습니다. [유다시티 파이썬 강좌](https://www.udacity.com/course/introduction-to-python--ud1110)에서 계정을 만들고 'start free course'를 눌러주세요. 데이터 구조는 다양한 종류의 데이터를 구성하고 그룹화 하는 컨테이너 입니다. 심지어 컨테이너가 컨테이너를 구성할 수도 있습니다.

## Lists

리스트는 파이선에서 가장 기초적인 데이터구조입니다. 리스트는 대괄호를 이용해서 만듭니다. 리스트의 원소는 어떤 자료형이 섞여있건 상관 없습니다.

```
list_of_random_things = [1, 3.4, 'a string', True]
```
이렇게 네개의 원소를 가지고 있는 리스를 참조할 때 첫번째 원소의 인덱스는 0입니다. 사용법은 배열과 비슷하지만 자료형이 섞일 수 있다는 특징이 있네요
```
>>> list_of_random_things[0]
1
```
더 특이한 점은 **음수의 인덱스를 이용해서 원소를 참조 할 수 있다** 는 것입니다. -1은 맨뒤 원소, -2은 맨뒤에서 두번쨰 원소가 되는 거죠.
```
>>> list_of_random_things[-1]
True
>>> list_of_random_things[-2]
a string
```
### Slice와 Dice

slice는 인덱스를 이용해서 원소 단 하나만을 가져오지 않고, 한번에 여러개의 원소를 가져올 수 있습니다. 기억할 점은 **':'의 왼쪽값에서 부터 ':'의 오른쪽 직전 까지의 원소를 뽑아온다** 는 것입니다.

```
>>> list_of_random_things = [1, 3.4, 'a string', True]
>>> list_of_random_things[1:2]
[3.4]
```

무조건 리스트의 맨처음부터 원소를 뽑고싶을때는 ':'왼쪽을 기입하지 않습니다.
```
>>> list_of_random_things[:2]
[1, 3.4]
```
반대의 경우도 같습니다.
```
>>> list_of_random_things[1:]
[3.4, 'a string', True]
```
이러한 인덱싱 방식은 **string에서도 정확하게 똑같이** 동작합니다!!

### `in` or `not in`?

리스트에 특정한 원소가 있나 없나 확인 하고 싶을때는 **boolean** 타입을 반환하는 `in`과 `not in`를 사용합니다.이것 역시 **string 에서도 정확하게 똑같이** 동작합니다.

```
>>> 'this' in 'this is a string'
True
>>> 'in' in 'this is a string'
True
>>> 'isa' in 'this is a string'
False
>>> 5 not in [1, 2, 3, 4, 6]
True
>>> 5 in [1, 2, 3, 4, 6]
False
```
### Mutability 와 Order

둘다 `slice`, `dice`, `in`연산이 가능한데 그럼 무슨 차이가 있는 걸까요?
1. string은 같은 타입을 나열한 것이고 lists는 다른 타입을 나열할 수 있습니다.
2. lists는 만들어 지고 나서 원소를 다시 수정할 수 있습니다. string은 한번 만들어 지면 그걸로 끝입니다.

2번에 대해 더 자세히 알아보겠습니다. my_list의 0번째 원소 1을 'one'으로 바꿨습니다.
```
>>> my_lst = [1, 2, 3, 4, 5]
>>> my_lst[0] = 'one'
>>> print(my_lst)
['one', 2, 3, 4, 5]
```
그러나 greeting의 0번째 원소 'H'를 'M'으로 바꿀 수는 없습니다.
```
>>> greeting = "Hello there"
>>> greeting[0] = 'M'
```
lists와 같이 나중에 수정할 수 있는 것을 **mutable** 이라고 하고 그렇지 않은 것을 **immutable** 이라고 합니다.

**Order** 는 원소의 위치에 따라 원소에 접급할 수 있는 것을 말합니다. string과 lists는 모두 order입니다.

### Quiz

#### 첫번째
`days_in_month` list 가 주어져 있을 때 8월은 몇일이나 있나요?

```
month = 8
days_in_month = [31,28,31,30,31,30,31,31,30,31,30,31]

# use list indexing to determine the number of days in month


print(num_days)
```

#### 두번째

slicing 표기법을 이용해서 가장 최근의 날짜 세개만 골라보세요 slicing에서도 음수를 이용한 표현이 가능합니다
```
eclipse_dates = ['June 21, 2001', 'December 4, 2002', 'November 23, 2003',
                 'March 29, 2006', 'August 1, 2008', 'July 22, 2009',
                 'July 11, 2010', 'November 13, 2012', 'March 20, 2015',
                 'March 9, 2016']


# TODO: Modify this line so it prints the last three elements of the list
print(eclipse_dates)
```

#### 세번째

string과 list를 수정하려고 합니다. 수정결과가 어떻게 될까요?
```
sentence1 = "I wish to register a complaint."
sentence2 = ["I", "wish", "to", "register", "a", "complaint", "."]
```

1. `sentence2[6]="!"`
2. `sentence2[0]= "Our Majesty"`
3. `sentence1[30]="!"`
4. `sentence2[0:2] = ["We", "want"]`

## List methods

### list의 유용한 함수 첫번째
1. `len()` list의 원소의 개수를 알려줍니다.
2. `max()` 가장큰 원소를 알려줍니다. 숫자로 이루어져 있을 때는 가장 큰 수를, 문자열로 이루어져 있을 때는 알파벳에서 가장 큰 원소를 알려주고 여러 자료형이 섞여있다면 사용할 수 없습니다.
3. `min()` 가장 작은 원소를 알려주는데, `max()`와 반대라고 생각하면 됩니다.
4. `sorted()` list를 복제하여 오름차순으로 정렬한 list를 반환합니다. 원래의 list는 정렬하지 않고 그대로 남습니다.

### list의 유용한 함수 두번째

#### `join`

list의 모든 원소들 사이사이에 separator를 넣어서 새로운 문자열을 만들어주는 함수 입니다. 이 함수를 사용하기 위해서 list의 원소는 string이어야 합니다. 다른게 섞여있으면 오류가 납니다.

```
new_str = "\n".join(["fore", "aft", "starboard", "port"])
print(new_str)
```
실행하면
```
fore
aft
starboard
port
```
이 경우 separator로 "\n"를 이용했습니다.

#### `append`

`append`는 list의 맨 뒤에 원소를 추가해 주는 함수 입니다.

```
letters = ['a', 'b', 'c', 'd']
letters.append('z')
print(letters)
```
실행 하면
```
['a', 'b', 'c', 'd', 'z']
```
### Quiz

#### 첫번째
다음 코드들의 실행결과는 무엇일까요?
```
a = [1, 5, 8]
b = [2, 6, 9, 10]
c = [100, 200]

print(max([len(a), len(b), len(c)]))
print(min([len(a), len(b), len(c)]))
```
```
names = ["Carol", "Albert", "Ben", "Donna"]
print(" & ".join(sorted(names)))
```
```
names = ["Carol", "Albert", "Ben", "Donna"]
names.append("Eugenia")
print(sorted(names))
```
#### 두번째

자료형과 데이터구조에 대해 옳은 것은 어떤 것인가요?
1. 데이터구조는 다른 자료형을 포함할 수 있는 컨테이너.
2. 데이터구조는 오직 한 종류의 자료형만 다룬다.
3. list는 데이터구조의 한 예다.
4. 모든 자료형은 데이터 구조다.
5. 모든 자료구조는 자료형이다.

#### 세번째

list의 속성들을 고르세요
1. Mutable
2. Immutable
3. Ordered
4. Unordered

#### 네번째

list의 인덱싱과 slicing을 테스트하는 문제입니다.

문제상황에 알맞은 list `arr`의 indexing 표기를 하세요.
1. list의 첫번째 원소
2. list의 네번째 원소
3. list의 마지막 원소
4. list의 마지막에서 두번째 원소

다음 결과물이 나오도록 `arr = ['a', 'b', 'c', 'd', 'e', 'f', 'g']`를 slicing하세요
1. `['c', 'd', 'e', 'f']`
2. `['a', 'b', 'c']`
3. `['e', 'f', 'g']`

## Tuples

튜플은 **immutable, order** 는 속성을 가지고 있습니다.
```
location = (13.4125, 103.866667)
print("Latitude:", location[0])
print("Longitude:", location[1])
```
mutable한 list와 비슷하지만 분명히 다름니다. 튜플은 immutable하기 수정할 수 없습니다. 다음과 같이 튜플을 만들고 이용할 수 있습니다. **pack, unpack** 한다고 합니다. 즉 괄호는 옵션이라 사용하든 안하든 같습니다.

```
dimensions = 52, 40, 100
length, width, height = dimensions
print("The dimensions are {} x {} x {}".format(length, width, height))
```
튜플은 자료들이 강한 연관이 있을 때 유용하게 쓰입니다.

### Quiz

#### 첫번째

알맞은 답을 쓰세요
1. Tuple - order인가요 unorder인가요?
2. Tuple - mutable인가요 immutalbe인가요? 뭔가요?
3. List - order인가요 unorder인가요?
4. List - mutable인가요 immutalbe인가요? 뭔가요?

#### 두번째
실행결과가 무엇인가요?
```
tuple_a = 1, 2
tuple_b = (1, 2)

print(tuple_a == tuple_b)
print(tuple_a[1])
```

## sets

set은 **mutable, Unordered** 합니다.
set은 진짜 집합과 같습니다. 집합에서 같은 원소가 없죠? list에서 set으로 변환 할때 set도 중복된 원소는 알아서 지워줍니다.
```
numbers = [1, 2, 6, 3, 1, 1, 6]
unique_nums = set(numbers)
print(unique_nums)
```
실행결과는
```
{1, 2, 3, 6}
```

set은 `in`연산자를 사용할 수있고, `pop`, `add`메소드를 지원합니다. 특이하게도 pop메소드를 호출하면 랜덤한(?!)원소가 지워집니다. set은 unorder이기 때문에 마지막 원소가 없다고 합니다.
```
fruit = {"apple", "banana", "orange", "grapefruit"}  # define a set

print("watermelon" in fruit)  # check for element

fruit.add("watermelon")  # add an element
print(fruit)

print(fruit.pop())  # remove a random element
print(fruit)
```
실행결과는
```
False
{'grapefruit', 'orange', 'watermelon', 'banana', 'apple'}
grapefruit
{'orange', 'watermelon', 'banana', 'apple'}
```
### Quiz

실행 결과는 무엇일까요?
```
a = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
b = set(a)
print(len(a) - len(b))
```

다음 코드를 실행 했을 때 숫자 5는 set`b`의 원소인가요?

```
a = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
b = set(a)
b.add(5)
b.pop()
```
1. 네
2. 아니오
3. 어쩌면요?
4. 이거 에러입니다.

## Dictionaries

dictionary는 키에 따라 값을 매핑하는 **mutable** 한 데이터 구조입니다.
```
elements = {"hydrogen":1, "helium":2, "carbon":6}
```
dictionary의 키는 immutalbe한 것이면 어떤 것이든 가능합니다. string뿐만 아니라 integer와 tuple도 가능합니다. 심지어 한 dictaionary 안에 각 키의 type이 달라도 가능합니다. 키를 이용해서 값을 참조 할때는 대괄호를 하용합니다.
```
print(elements["helium"])  # print the value mapped to "helium"
elements["lithium"] = 3  # insert "lithium" with a value of 3 into the dictionary
```
list와 set에서 사용했던 것처럼 `in`키워드도 사용가능합니다. 또 get이라는 메소드도 사용가능한데 대괄호를 사용할때랑 다르게 존재하지 않는 키를 조회하면 None을 반환합니다.
```
print("carbon" in elements)
print(elements.get("dilithium"))
```
실행결과
```
True
None
```
보통 컴파일 에러를 피하기 위해서 대괄호를 사용하는 것 보다 `get`을 이용하는 것이 더 좋다고 합니다. `None`자체를 프로그래밍에 이용할 수 있기 때문이죠!
```
>>> elements.get('dilithium')
None
>>> elements['dilithium']
KeyError: 'dilithium'
>>> elements.get('kryptonite', 'There\'s no such element!')
"There's no such element!"
```
### Identity Operators

- `is` 왼쪽과 오른쪽이 같은지 확인하는 연산자입니다.
- `is not` 왼쪽과 오른쪽이 다른지 확인하는 연산자 입니다.

```
n = elements.get("dilithium")
print(n is None)
print(n is not None)
```
실행하면
```
True
False
```

### Quiz

#### 첫번째

다음 데이터를 가지고 있는 dictionary를 정의하세요

|Keys|values|
|---|---|
|Shanghai|17.8|
|Istanbul|13.3|
|Karachi|13.0|
|Mumbai|12.5|

#### 두번째

딕셔너리의 키로 쓸수있는 자료형은 무엇인지 골라보세요

1. str
2. list
3. int
4. float

#### 세번째

대괄호로 딕셔너리를 참조할때 존재하지 않는 키값을 참조하면 무슨일이 일어나나요?
1. `None`값을 리턴한다.
2. 참조하려는 키값을 딕셔너리에 자동으로 추가하며 그 값은 디폴트인 `None`이 된다.
3. `KeyError`가 발생한다.
4. 파이썬이 알아서 인터넷을 검색해서 해결해 준다.(채신기술ㄷㄷ)

#### 네번째 Equality vs. Identity : `==` vs. `is`
다음 코드의 실행결과는 무엇일 까요?

```
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a == b)
print(a is b)
print(a == c)
print(a is c)
```

1. `True, True, True, True`
2. `True, False, True, False`
3. `True, True, True, False`
4. `True, True, False, False`

#### 다섯째

```
animals = {'dogs': [20, 10, 15, 8, 32, 15],
          'cats': [3,4,2,8,2,4],
          'rabbits': [2, 3, 3],
          'fish': [0.3, 0.5, 0.8, 0.3, 1]}
```
코드를 보고 다음 질문에 답하세요

1. 키의 자료형은 무엇인가요?
2. 값의 자료형은 무엇인가요?
3. `anmals['dogs']`?
4. `animals['dogs'][3]`?
5. `animals[3]`?
6. `animals['fish']`?

## Data Structure 최종점검

### Data structure 종합 문제

#### 첫번째
다음중 tuple에 대하여 옳은 것만을 모두 고르세요
1. Mutalbe이다.
2. Ordered 데이터 구조다.
3. list와 같이 slicing과 indexing이 모두 가능하다.
4. 중괄호를 이용해서 선언한다.

#### 두번째
다음중 set에 대하여 옳은 것만을 모두 고르세요
1. Mutalbe이다.
2. Ordered 데이터 구조다.
3. list와 같이 slicing과 indexing이 모두 가능하다.
4. 중복된 원소는 가질수 없다.

#### 세번째
set은 오직 중괄호만을 이용해서 만들수 있다.
1. 참이다.
2. 거짓이다.

#### 네번째
다음중 dictionary에 대하여 옳은 것만을 모두 고르세요
1. Mutalbe이다.
2. Ordered 데이터 구조다.
3. key를 이용하여 인덱스 참조가 가능하다.
4. dictionary의 모든 키는 유일하다.
5. 어떤 자료형이든 키로 사용될수 있따.

### DataStructure 혼합하기

데이터 구조 안에 데이터 구조를 넣을 수 있습니다.

```
elements = {"hydrogen": {"number": 1,
                         "weight": 1.00794,
                         "symbol": "H"},
              "helium": {"number": 2,
                         "weight": 4.002602,
                         "symbol": "He"}}
```
이런 딕셔너리를 참조할땐 이렇게 합니다.
```
helium = elements["helium"]  # get the helium dictionary
hydrogen_weight = elements["hydrogen"]["weight"]  # get hydrogen's weight
```
그리고 뭔가 추가 하고싶다?
```
oxygen = {"number":8,"weight":15.999,"symbol":"O"}  # create a new oxygen dictionary
elements["oxygen"] = oxygen  # assign 'oxygen' as a key to the elements dictionary
print('elements = ', elements)
```
그러면 실행결과는
```
elements =  {"hydrogen": {"number": 1,
                          "weight": 1.00794,
                          "symbol": 'H'},
               "helium": {"number": 2,
                          "weight": 4.002602,
                          "symbol": "He"},
               "oxygen": {"number": 8,
                          "weight": 15.999,
                          "symbol": "O"}}
```
### Quiz

#### 첫번째
```
elements = {'hydrogen': {'number': 1, 'weight': 1.00794, 'symbol': 'H'},
            'helium': {'number': 2, 'weight': 4.002602, 'symbol': 'He'}}
```
다음과 같은 결과가 나오도록 딕셔너리에 원소를 추가하세요
```
>>> print(elements['hydrogen']['is_noble_gas'])
False
>>> print(elements['helium']['is_noble_gas'])
True
```
#### 두번째
리스트의 특성에 대하여 올바른 것을 모두 고르세요
1. 데이터를 삽입할때 순서는 중요하지 않다.
2. 첫번쨰 데이터의 인덱스번호는 0이다.
3. 정렬가능하다.
4. `.append`를 이용해서 데이터를 추가할 수 있다.
5. `.add`를 이용해서 데이터를 추가할 수 있다.

#### 세번째

set의 특성에 대하여 올바른 것을 모두 고르세요
1. 순서가 정해져 있다.
2. 중복된 값을 저장할 수 있다.
3. mutable이다.
4. `.add`를 이용해서 원소를 추가한다.
5. 정렬가능하다.

#### 다섯번째
dictionary의 특성에 대하여 올바른 것을 모두 고르세요
1. 원소가 두 부분으로 이루어져 있다.
2. `.append`를 이용해서 원소를 추가한다.
3. 순서가 정해져 있다.
4. 정렬가능하다.
5. 원소로 또다른 dictionary를 사용할 수 있다.

#### 여섯번째

```
verse = "if you can keep your head when all about you are losing theirs and blaming it on you   if you can trust yourself when all men doubt you     but make allowance for their doubting too   if you can wait and not be tired by waiting      or being lied about  don’t deal in lies   or being hated  don’t give way to hating      and yet don’t look too good  nor talk too wise"
print(verse, '\n')

# verse의 각 단어를 원소로하는 list를 만들어보세요
verse_list =
print(verse_list, '\n')

# list를 set으로 변환 하세요
verse_set =
print(verse_set, '\n')

# 각 단어들의 개수를 구해보세요
num_unique =
print(num_unique, '\n')
```

#### 일곱번째

```
verse_dict =  {'if': 3, 'you': 6, 'can': 3, 'keep': 1, 'your': 1, 'head': 1, 'when': 2, 'all': 2, 'about': 2, 'are': 1, 'losing': 1, 'theirs': 1, 'and': 3, 'blaming': 1, 'it': 1, 'on': 1, 'trust': 1, 'yourself': 1, 'men': 1, 'doubt': 1, 'but': 1, 'make': 1, 'allowance': 1, 'for': 1, 'their': 1, 'doubting': 1, 'too': 3, 'wait': 1, 'not': 1, 'be': 1, 'tired': 1, 'by': 1, 'waiting': 1, 'or': 2, 'being': 2, 'lied': 1, 'don\'t': 3, 'deal': 1, 'in': 1, 'lies': 1, 'hated': 1, 'give': 1, 'way': 1, 'to': 1, 'hating': 1, 'yet': 1, 'look': 1, 'good': 1, 'nor': 1, 'talk': 1, 'wise': 1}
print(verse_dict, '\n')

# 각 유일한 키들의 개수를 구하세요
num_keys =
print(num_keys)

# 'breathe'가 딕셔너리의 키로 있는지 확인해 보세요
contains_breathe =
print(contains_breathe)

# 딕셔너리를 키를 정렬해서 list로 만들어 보세요
sorted_keys =

# 정렬된 키 리스트의 첫번째 원소는 뭔가요
print()

# 키 리스트의 가장 큰 값은 뭔가요
print()
```
#### 여덟번째

일곱번째 문제와 이어집니다. `verse_dict`에 관하여 옳바른 답을 써주세요
1. 유일한 단어들은 얼마나 되나요?
2. 'breathe'가 들어있나요?
3. 첫번쨰 키는 무엇인가요?
4. `verse_dict`의 키를 list로 정렬했을 때 첫번째 원소는 무엇인가요?
5. `verse_dict`의 가장 큰 값은 무엇인가요?

### 정리

|Data structure|Ordered|Mutable|Constructor|Example|
|--------------|-------|-------|-----------|-------|
|List|Yes|Yes|`[]`or`list()`|`[5.7, 4, 'yes', 5.7]`|
|Tuple|Yes|No|`()`or`tuple()`|`(5.7, 4, 'yes', 5.7)`|
|Set|No|Yes|`{}` * or`set()`|`{5.7, 4, 'yes'}`|
|Dictionary|No|No**|`{ }`or`dict()`|`{'Jun': 75, 'Jul': 89}`|

\* 중괄호를 비워놓으면 빈 set이 아니라 딕셔너리가 만들어집니다. 그래서 빈set을 만들려면 `set()`을 이용하세요.

** 딕셔너리 자체는 mutalbe이지만 키들은 반드시 immutalbe이어야 합니다.

> 참고 : https://www.udacity.com/course/introduction-to-python--ud1110

작성자 : 이석원

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

튜플은 immutable, order라는 속성을 가지고 있습니다.
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

set은 mutable, Unordered합니다.
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

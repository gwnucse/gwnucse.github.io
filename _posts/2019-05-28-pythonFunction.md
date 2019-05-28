---
layout: post
title:  "python 함수"
date:   2019-05-28 09:20:00 +0800
categories: python
tag: python, function
comment: true
---
* content
{:toc}

# 함수 정의 하기

정의와 호출
```
def cylinder_volume(height, radius):
    pi = 3.14159
    return height * pi * radius ** 2

cylinder_volume(10, 3)
```
## Function Header

함수 정의의 첫 줄을 살펴 볼까요?
1. 함수는 항상 `def`키워드로 시작합니다. **함수를 정의한다** 라는 뜻이죠
2. 그 다음 **함수 이름** 이 따라 옵니다.
3. 그 다음 **매개변수** 를 받을 소괄호가 옵니다.
4. 마지막은 항상 `:` 으로 끝납니다.

## Function Body

1. **body** 는 함수의 header 이후 들여씁니다.
2. 매개변수도 사용할 수 있고, 새로운 변수도 만들어서 쓸 수 있습니다. 하지만 함수 안에서만 써야 합니다.
3. `return`문을 이용해서 값을 반환 합니다. `return`이 없으면 `None`값을 반환합니다.

## Default Arguments

```
def cylinder_volume(height, radius=5):
    pi = 3.14159
    return height * pi * radius ** 2
```
`radius`는 매개변수가 없으면 기본적으로 5가 할당 되어있습니다.

또 함수의 매개변수는 **position** 으로 할당할 수도 있고, **name** 으로 직접 할당할 수도 있습니다.
```
cylinder_volume(10, 7)  # pass in arguments by position
cylinder_volume(height=10, radius=7)  # pass in arguments by name
```

# Documentation

함수는 프로그램을 여러 조각으로 쪼개서 코드를 작성하기 쉽고, 읽기 쉽게 만듭니다. 함수안에 주석으로 함수가 어떤 기능을 하는지 사용법은 어떤지 적어 놓는 것을 *Documentation strings* 줄여서 *docstrings* 라고 합니다.
```
def population_density(population, land_area):
    """Calculate the population density of an area. """
    return population / land_area
```
docstrings는 큰따옴표 세개를 연속해서 사용합니다. 첫줄에 설명을 쓰고 그걸로 충분하면 끝이지만 내용을 더 쓸수도 있습니다.
```
def population_density(population, land_area):
    """Calculate the population density of an area.

    INPUT:
    population: int. The population of that area
    land_area: int or float. This function is unit-agnostic, if you pass in values in terms
    of square km or square miles the function will return a density in those units.

    OUTPUT:
    population_density: population / land_area. The population density of a particular area.
    """
    return population / land_area
```

# Lambda Expressions

Lambda Expressions는 무명함수를 만듭니다. 무명합수는 이름이 없는 함수를 말하는데 함수를 빠르게 만들어서 사용하고 두번다시 사용하지 않을때 유용하게 쓰입니다.
```
def multiply(x, y):
    return x * y
```
```
multiply = lambda x, y: x * y
```
위아래 함수는 같은 의미 입니다. 그렇기 때문에 둘다 아래와 같이 사용할 수 있습니다.
```
multiply(4, 7)
```
## 람다 함수 만들기

1. `lambda`키워드를 씁니다.
2. 그 다음 매개변수를 씁니다. 여러개를 쓸땐 반점을 이용합니다. 그리고 `:`으로 마칩니다.
3. return 할 값을 `:`뒤에 적습니다.

> 참고 : https://www.udacity.com/course/introduction-to-python--ud1110

작성자 : 이석원

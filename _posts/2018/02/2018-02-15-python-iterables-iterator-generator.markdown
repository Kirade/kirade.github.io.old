---
layout: "post"
title: "[Python] Iterables, Iterator, Generator"
date: "2018-02-15 16:57"
category: Python
tags: Python Syntax
---

## Background
파이썬에서 사용되는 `Generator`를 사용하면 리스트에 비교하여 어떤 상황에서 더 효율적으로 작동하는 코드를 작성할 수 있다. 예를들면 1부터 1,000,000까지 숫자를 하나씩 출력하려고 할 때, 리스트 객체를 이용하면 1부터 1,000,000만 까지의 숫자들이 포함된 리스트를 만들어 for문을 순회하며 내용을 출력할 수 있다. 하지만 이런 방법은 메모리에 100만개의 데이터를 가지고있어야 하므로 메모리 사용성 측면에서 보았을 떄는 비효율적일 수 있다. 반면, 제너레이터는 이런 상황에서 좋은 대안이 될 수 있다.

---
## Study
제너레이터를 이해하기 위해서는 3가지 키워드에 대한 이해가 뒷받침되어야 한다.

1. `iterable`
2. `iterator`
3. `yield`

### iterable
영어 단어의 뜻 그대로 '순회할 수 있는것들'이라고 이해할 수 있다. 파이썬에서는 '객체의 멤버를 한번에 하나씩 반환할 수 있는 객체'라고 정의하고 있다. 예를들면 `list`, `str`, `tuple`, `dict`와 같은 것들이 포함된다.

이런 특징을 가진 객체들은 주로 for구문과 같이 순회를 하는 구문에서 자주 사용된다. 이런 구문에 사용되기 위해서는 객체가 `iter()`라는 빌트인 메서드를 통해 `iterator`라는 형태의 객체가 되어야하는데 이는 이어 설명하겠다. 추가하자면 for 구문에서는 이런 작업을 내부적으로 수행해 주기 때문에 iterable한 객체를 따로 변환하지 않고 넣어도 잘 동작한다.

### iterator
앞서 설명한 iterable한 객체들을 빌트인 메서드인 `iter()`를 통해 호출하게 되면 비로호 순회가능한 객체인 iterator 객체가 된다.

```python
# iter 메서드
iter(object[. sentinel])
```

 `iter()`메서드가 정상적으로 작동하기 위해서는 객체 내에 iteration 프로토콜인 `__iter__` 메서드가 정의되거나 sequence 프로토콜인 `__getitem__`메서드가 정의되어 있어야 한다. 또한, sentinel 인자가 주어진 경우 객체는 반드시 callable이어야 하며, 순회를 할 때, `__next__`메서드를 호출하면서 값을 반환한다. 순회중, sentinel에서 주어진 값과 같은 값이 반환될 경우 `StopIteration`예외를 발생시킨다.

for 구문은 iterable한 객체를 받아서 `StopIteration`예외가 발생하기 전까지 순회를 돌고 종료하는 것을 내부적으로 구현하고 있다.

간단한 구현을 직접 해보았다.
```python
class SampleIterables():
    def __init__(self):
        self.size = 5
        self.inventory = list()

    def __iter__(self):
        self.index = 0
        return self

    def __next__(self):
        self.index += 1
        if self.index < self.size:
            return self.inventory[self.index]
        else:
            raise StopIteration

sample = SampleIterables()
sample.inventory = [1,2,3,4,5]
print(sample.__iter__())
print(sample.__next__())
print(sample.__next__())
print(sample.__next__())
print(sample.__next__())

# 결과
<__main__.SampleIterables object at 0x10809a7f0>
2
3
4
5
```

### yield
앞에서 iterable, iterator에 대한 이해가 되었다면 generator를알아볼 준비가 되었다.

generator의 구현은 함수의 형태로 구현된다. yield는 generator를 구현하는 함수 안에서 사용되는 키워드이다. 이 키워드를 통해 함수가 generator라는 것을 나타내고 객체가 호출될 때마다 return 과 같이 값을 반환한다.

python2에서는 `xrange()`, python3에서는 `range()`가 generator이다.

다음은 generator의 구현 예시이다.
```python
def foo_generator(n):
    num = 0
    while num < n:
      yield num
      num += 1

gen_obj = foo_generator(1000)

print(type(gen_obj))
print(gen_obj)
print(sum(gen_obj))

# 결과
<class 'generator'>
<generator object foo_generator at 0x10805ff10>
499500
```

마지막으로 generator는 list comprehension으로도 나타낼 수 있다. 일반적인 리스트를 만들 때 대괄호를 사용한다면, generator는 소괄호를 사용하여 나타낸다.

```python
simple_list = [x**2 for x in range(5)]

simple_generator = (x**2 for x in range(50))
```
---
## Reference
* [iter() - Python](https://docs.python.org/3/library/functions.html#iter)
* [iterable - Python](https://docs.python.org/3/glossary.html)
* [generator - Python Wiki](https://wiki.python.org/moin/Generators)

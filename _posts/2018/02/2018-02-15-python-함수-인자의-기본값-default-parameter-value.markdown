---
layout: "post"
title: "[Python] 함수 인자의 기본값 (Default Parameter Value)"
date: "2018-02-15 00:21"
category: Python
tag: Python
---

## Background
파이썬에서 함수를 정의할 때, 기본값을 정해줄 수 있다. 하지만 기본값으로 정해준 인자들이 새로 초기화 되어 함수에서 사용되지 않고 공유되는 현상이 발생하는 경우가 있다.

## Study

### 문제

파이썬에서는 정의에 따라 immutable한 객체들(Numbers, Strings, Tuples, None)은 변화하지 않습니다. 반면 mutable한 객체들(dictionaries, lists, class)은 변화합니다. 이러한 특징 때문에 여러 상황에서 혼란이 발생할 여지가 있습니다.

이러한 특징 때문에 함수 안의 인자의 기본값을 정의할 때, immutable객체를 정의할 때와, mutable한 객체를 정의할 때 동작이 다르게 나타납니다.

일반적인 경우에 프로그래머는 함수 인자의 기본값을 정의할 때, 함수 내에서 함수가 호출될 때마다 인자를 받지 않았을 때, 인자를 기본값으로 초기화 시키려는 의도를 가지고 있습니다.

따라서 다음과 같은 코드를 실행하였을때는 의도와 맞는 결과를 출력합니다. 여기서는 immutable 객체 중 하나인 Number 객체를 기본값으로 주었습니다.
```python
def sample_immutable(param=3):
    param += 1
    print(param)

sample_immutable()
sample_immutable(2)
sample_immutable()

# 결과
4
3
4
```

반면, immutable 객체인 클래스를 기본값으로 지정하였을 때에는 프로그래머의 의도와 다른 출력이 표시됩니다.
```python

import datetime
import time

def sample_mutable(param=datetime.datetime.now()):
    print(param)

sample_mutable()
time.sleep(2)
sample_mutable()

# 결과
2018-02-15 00:37:37.293205
2018-02-15 00:37:37.293205
```

중간에 2초를 쉬었음에도 불구하고 함수가 출력한 시간은 이전에 기본값으로 정의되었던 값을 그대로 유지하고 있습니다. 왜나하면 이전에 정의된 기본값이 mutable 객체였기 때문입니다.

### 해결방법
immutable 객체를 기본값으로 지정하였을 때에는 문제가 없어보였지만, mutable 객체를 지정하였을 경우 최초에 호출된 기본값을 참조하는 문제가 발생하였습니다.

이를 해결하기 위해서는 파이썬 공식문서에서는 mutable 객체의 경우 기본값을 `None`으로 두고, 함수 내에서 `None`여부를 검사하여 기본값을 정의하는 방식을 취하는 방식을 취하라고 권고합니다.

이런 방식으로 코딩을하면 정상적으로 작동하는 것을 알 수 있습니다.
```python
import datetime
import time

def sample_solution(param=None):
  if param is None:
    param = datetime.datetime.now()
  print(param)

sample_solution()
time.sleep(2)
sample_solution()

# 결과
2018-02-15 00:46:54.477672
2018-02-15 00:46:56.480266
```

### Memoization
위와 같은 mutable 객체 기본값은 함수 내에서의 caching을 구현할 경우 유용하게 사용될 수 있습니다.

다음은 공식문서에서 제시한 활용 예제 입니다. `_cache`라는 mutable 객체 기본값을 활용하여 함수가 수행될 때마다 앞 두 가지 인자에 대한 수행결과를 가지고 있는지 검사합니다. 이 과정을 통해 이미 수행되었던 경우라면 연산없이 빠르게 결과값을 만들어 낼 수 있습니다.
```python

def expensive(arg1, arg2, _cache={}):
    if (arg1, arg2) in _cache:
        return _cache[(arg1, arg2)]

    # Calculate the value
    result = ... expensive computation ...
    _cache[(arg1, arg2)] = result           # Store result in the cache
    return result
```


## Reference
* [Python3 docs](https://docs.python.org/3/faq/programming.html?highlight=default%20parameter#why-are-default-values-shared-between-objects)

---
layout: "post"
title: "[Python] with와 context manager 알아보기"
date: "2018-01-28 22:40"
category: Python
tags: Python
---

## Background
장고를 공부하던 중에 모델부분에서 기능들의 구현을 살펴보다 with .. as 구문을 활용하여 데이터베이스에 연결과 종료에 사용하는 것을 보았습니다. 이 구문에 대해 제대로 알고있지 않은것 같아 한 번 더 찾아보고 정리합니다.

---
## Study

일반적으로 다음과 같은 방식으로 코딩을 한다면 반드시 `finally`구문 안에 있는 내용은 예외의 발생여부와 상관없이 반드시 실행된다는 것이 보장된다. 이런 구조의 방식은 코딩하는데 자주 사용됩니다.

```python
try:
  do_somthing
except:
  excpetion
finally:
  do_otherthing
```

예를 들면, 파일 처리와 데이터베이스 연결과 같은 경우에는 C언어에서 포인터를 사용하고 free 명령어를 통해 메모리 영역을 풀어주듯 파일과 데이터베이스의 연결의 종료를 선언해 주어야 합니다.

이런 처리들을 파이썬 2.5가 나오는 시점에 도입된 `with`구문을 이용하면 간결하게 만들어 낼 수 있습니다. 먼저, `with` 구문을 사용하기 위해서는 `context manager`에 대한 이해가 필요합니다.

`context manager`는 다음 두개의 메서드를 정의하고 있어야합니다.
* `__enter__(self)`
* `__exit__(self, type, value, traceback)`

각 이름에 걸맞게 `__enter__()`는 `with`구문이 시작되는 시점에 자동으로 실행되고, 반대로 `__exit__()`는 마치는 시점에 호출되게 됩니다.

```Python
class TestContextManager():

  def __enter__(self):
    # Do something when entering

  def __exit__(self, type, value, traceback):
    # Do something when quitting
```

이렇게 `context manager`를 정의하게 되면 비로소, `with`구문을 사용하여 간결하게 코딩을 할 수 있습니다. 일반적으로 사용되는 파일, 데이터베이스 연결은 `context manager`로 정의되어 있어 `with`구문의 사용이 별다른 처리없이 사용가능 합니다.

```Python
## 파일
with open("test.txt") as f:
    data = f.read()
    # do something

## 데이터베이스
connection = MySQLdb.connect(...)
with connection as cursor:
    cursor.execute('...')
    # do something

```



---
## Reference
* [when to close cursors using MySQLdb - stack overflow](https://stackoverflow.com/questions/5669878/when-to-close-cursors-using-mysqldb)
* [Python with 구문과 context manager 이해하기](https://cjh5414.github.io/python-with/)

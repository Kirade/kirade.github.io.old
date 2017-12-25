---
layout: "post"
title: "[Java] 자바 알고리즘 BigInteger"
date: "2017-12-22 21:45"
tags: Java Algorithm
category: Algorithm
---

## Background
일반적으로 Java에서 사용되는 기본 자료형으로는 그 자료형의 크기의 한계로 인해 더 큰 수를 표현하지 못하는 경우가 있습니다. 그런 경우 Java에서는 BigInteger와 같은 자료형으로 더 큰 수를 표현합니다.

---
## Study
기본자료형은 각각
`Int -> -2^31 ~ 2^31-1`
`Long -> -2^63 ~ 2^63-1`
의 범위를 표현 할 수 있도록 만들어 졌습니다.

BigInteger는 `a+b`와 같은 연산이 정의되지 않았기 때문에, `a.add(b)`와 같이 연산을 수행해야 합니다.
```Java
import java.math.*;

~

BigInteger a = new Biginteger("10000");
BigInteger b = new Biginteger("1000");
BigInteger c = a.add(b);

# result = 10000
System.out.println(a);

```

### 메서드
* `add()`
* `subtract()`
* `multiply()`
* `divide()`
* `remainder()`
* `gcd()`
* `negate()`
* `pow()`
* `equals()`

### 입력
BigInteger에 사용자 인풋으로 입력하기 위해서는, Scanner클래스에 `nextBigInteger()`를 사용합니다.

### BigDecimal
정수가 아닌 실수를 처리하기 위한 클래스로 정의되어 있다.

---
## Reference
[백준 온라인강의](https://code.plus/lecture/10)

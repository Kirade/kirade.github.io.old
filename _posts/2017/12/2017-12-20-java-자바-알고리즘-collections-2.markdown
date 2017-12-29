---
layout: "post"
title: "[Java] 자바 알고리즘 Collections #2"
date: "2017-12-20 16:55"
category: Algorithm
tags: Java Algorithm
---

## Background
앞서 살펴 본 ArrayList, LinkedList에 이어 Collection들을 알아보겠습니다.

---
## Study

# 1. Stack
한쪽 끝에서만 자료를 넣고 뺄 수 있는 자료구조 입니다. Last In First Out라고도 부릅니다.(LIFO)

### 메서드
* `E push(E item)`
* `E pop()` - C++ 와는 다르게 pop을 할 때, 리턴값이 있다.
* `E peek()`
* `bool empty()`
* `int size()`

### 구현
```java
Stack newStack = new Stack();
```

# 2. Set
Set은 중복된 원소를 포함하지 않습니다. Java에서는 인터페이스로 구현한 것들로는 HashSet, TreeSet, LinkedHashSet 있습니다.

### 메서드
* `boolean add(E e)`
* `void clear()`
* `boolean contains(Object o)`
* `boolean isEmpty()`
* `boolean remove(Object o)`
* `int size()`
* `Object[] toArray()`

C++ 에서는 add, celar, contains의 시간 복잡도는 O(logN)이 었지만, Java 에서는 그 구현에 따라 시간 복잡도가 다릅니다.

### HashSet
삽입 / 삭제 / 제거 연산의 시간 복잡도가 O(1)이지만, 순서가 보장이 되지 않습니다. 따라서 순서가 중요할 때가 아닌, 원소가 들어있는지 없는지를 판단할 때 유용합니다.

### TreeSet
이진 검색 트리(레드 블랙 트리)를 이용해서 구현되어 있어 삽입 / 삭제 / 제거 연산의 시간 복잡도는 O(logN)입니다.

### LinkedHashSet
해쉬테이블과 링크드리스트를 이용해서 구현되어 있습니다. 삽입 / 삭제 / 제거 연산의 시간 복잡도가 O(1)이고, 추가한 순서가 보장이 됩니다.

### 언제 어떤 구현을 사용하는가?
일반적인 경우에는 HashSet
순서가 중요한 경우에는 TreeSet
입력으로 넣은 순서가 중요한 경우에는 LinkedHashSet을 사용한다.

### 구현
```java
Set hash_set = new HashSet();
Set tree_set = new TreeSet();
Set linkedhash_set = new LinkedHashSet();
```

# 3. Map
Key - Value 쌍을 이루는 사전과 비슷한 자료구조 입니다. Map도 앞서 이야기한 Set과 같이 인터페이스이고, 구현으로는 HashMap, TreeMap, LinkedHashMap이 있습니다.

### 메서드
* `void clear()`
* `boolean containsKey(Object key)`
* `boolean containsValue(Object value)`
* `Set<Map.Entry<K,V>> entrySet()` - key,  value 쌍을 이용한 Set 생성
* `V get(Object key)`
* `boolean isEmpty()`
* `Set<K> keySet()` - key 를 이용한 Set 생성
* `V put(K key, V value)`
* `boolean remove(Object o)`
* `int size()`

```java
# 맵을 순회하는 방법

for(Map.Entry<String, Integer> entry : var_map.entrySet()){
  String key = entry.getKey();
  Integer value = entry.getValue();
  /* logic */
}
```

### 구현
```java
Map<k, v> hash_map = new HashMap<>();
Map<k, v> tree_map = new TreeMap<>();
Map<k, v> linkedhash_map = new LinkedHashMap<>();
```


# 4. Queue
한쪽 끝에서만 자료를 넣고 다른쪽 끝에서만 뺄 수 있는 자료구조 입니다. First In First Out라고도 합니다.(FIFO)

큐는 구현이 필요한 인터페이스이고, 구현으로는 ArrayDeque, LinkedList, PriorityQueue가 있습니다.

### 메서드
* `booelan offer(E e)`
* `E poll()` - C++ 와는 다르게 리턴값이 존재한다.
* `E peek()`
* `boolean isEmpty()`
* `int size()`

### 구현
```java
Queue dequeQueue = new ArrayDeque();
Queue linkedlistQueue = new LinkedList();
Queue priorityQueue = new PriorityQueue();
```

# 5. PriorityQueue
Queue의 구현중 하나인 PriorityQueue는 최대 힙 혹은 최소 힙으로 구현하는 경우가 많다.

기본적으로 최소값을 높은 우선순위를 주기 때문에 최소 힙은 그대로 구현할 수 있지만, 최대 힙의 경우는 comparator을 만들어 어떻게 compare 할지 결정해야한다.

---
layout: "post"
title: "[Java] 자바 알고리즘 Collections #1"
date: "2017-12-20 15:46"
category: Algorithm
tags: Java Algorithm
---

## Background
C++을 이용해서 알고리즘을 공부할 때에는 STL에 구현되어 있는 Stack, Queue, List, Deque, Set, Map 등과 같은 자료구조들을 활용하였습니다. 비슷하게 자바에는 Collection를 사용하면 C++의 STL과 같은 기능을 하는 자료구조들을 간편하게 사용할 수 있습니다.

## Study

# 1. ArrayList  
길이가 변화하는 리스트입니다. C++에서 Vector와 같은 역할을 합니다.

ArrayList를 만들 때, 괄호를 비워두면 빈 리스트를, 숫자를 입력하면 크기(Capacity)를 지정할 수 있습니다.
```java
import java.util.*;
public class Main{
  public static void main(String[] args){
    ArrayList<Integer> a = new ArrayList<Integer>();
    ArrayList<Integer> b = new ArrayList<Integer>(40);
  }
}
```
### 메서드
 * `boolean add(E e)`  
 * `void add(int index, E element)`
 * `void clear()`
 * `boolean Contains(Ojbect o)`
 * `E get(int index)`
 * `boolean isEmpty()`
 * `E remove(int index)`
 * `E set(int index, E element)`
 * `Object[] toArray()` - 예시 `int[] arr = (int[])a.toArray();`

ArrayList는 배열이기 때문에 중간에 원소를 추가하거나 삭제, 포함여부를 판단하는 경우 모두 O(n)시간이 걸린다.

### 인접리스트
ArrayList는 그래프를 활용하는 알고리즘에서 많이 사용된다. 다음과 같이 초기화하고 리스트의 내용을 추가할 수있다.

```Java
ArrayList<Integer>[] a = (ArrayList<Integer>[]) new ArrayList[n+1];
for(int i=1; i<n; i++){
  a[i] = new ArrayList<Integer>();
}
for(int i=0; i<m; i++){
  int u = sc.nextInt();
  int v = sc.nextInt();
  a[u].add(v);
  a[v].add(u);
}
```

# 2. LinkedList
여기서의 LinkedList는 이중연결 리스트를 말합니다. C++의 List와 같은 역할을 합니다. 알고리즘 문제를 푸는데 있어서 링크드리스트 자료구조는 드물게 사용됩니다.

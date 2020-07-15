---
title: "Java Collection Framework"
date: 2020-07-15
---



# <!--Collection Framework-->

Java Collection은 데이터 집합의 저장 및 조작을 위한 구조를 제공하는 프레임워크다.

다시 쉽게 말해, **Java Collection Framework는 다양한 인터페이스와 클래스를 제공하는 FW**다. ([참고](https://www.javatpoint.com/collections-in-java))

- Collection ? 오브젝트의 단일 유닛(=그룹)을 나타낸다.

- Framework ? 이미 만들어진 구조를 제공한다. 클래스와 인터페이스의 set을 나타낸다.
  
  - 인터페이스 : Set, List, Queue, Deque, Map
    - List와 Set은 Collection 인터페이스를 상속받지만, 구조상의 차이로 Map은 별도로 정의한다.
  
  - 클래스 : ArrayList, Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet, HashTable, HashMap, SortedMap, TreeMap  

![Collection](/img/20200714-02.JPG)

(...부끄럽지만 일단 올리고 보는 이미지. 아이패드&애플펜슬 필기 연습 좀 해야겠다.)

## Collection Interface

대표적인 Collection 인터페이스에는 List, Set, Map이 있다.



| 인터페이스 | 특징                                                         |
| :--------: | ------------------------------------------------------------ |
|    List    | 순서가 있는 데이터의 집합 / 데이터 중복 허용 / 구현 클래스 : ArrayList, LinkedList, Stack, Vector 등 |
|    Set     | 순서가 없는 데이터의 집합 / 데이터 중복 허용하지 않음 / 구현 클래스 : HashSet, TreeSet 등 |
|    Map     | 키와 값의 쌍으로 이루어진 데이터 집합으로 순서 없음 / 키의 중복을 허용하지 않음 / 구현 클래스 : HashMap, HashTable 등 |



## Collection Interface Method

Collection 인터페이스에서 제공하는 주요 메소드는 다음과 같다.



| 메소드                     | 설명                                                         |
| -------------------------- | ------------------------------------------------------------ |
| boolean add(E e)           | 컬렉션에 요소를 추가한다.                                    |
| void clear()               | 컬렉션의 모든 요소를 제거한다.                               |
| boolean contains(Object o) | 컬렉션이 객체를 포함하고 있는지 확인한다.                    |
| boolean equals(Object o)   | 컬렉션이 객체와 같은지 확인한다.                             |
| boolean isEmpty()          | 컬렉션이 비어있는지 확인한다.                                |
| Iterator<E> iterator()     | 컬렉션의 반복자를 반환한다. <br />(Iterator 인터페이스 상속) |
| boolean remove(Object o)   | 컬렉션에서 객체를 제거한다.                                  |
| int size()                 | 컬렉션의 모든 요소의 개수를 반환한다.                        |
| Object[] toArray()         | 컬렉션의 모든 요소를 Object 타입의 배열로 반환한다.          |



## Iterable Interface

Collection 인터페이스는 Iterable 인터페이스를 상속받는다. Root 인터페이스라고 볼 수 있다.

Iterable 인터페이스는 **Iterator<T> iterator()** 한 개의 추상 메소드를 포함한다.

따라서 Iterable을 상속받는 하위 클래스에서 iterator() 메소드를 구현할 수 있다.



## Iterator Interface

Collection, List, Set 인터페이스에서도 Iterator<E> iterator() 처럼 정의만 되어있고,

실제 iterator() 메소드는 하위 클래스(ArrayList, LinkedList, HashSet 등)에서 구현된다.



## Iterator Interface Method

Iterator 인터페이스에서 제공하는 주요 메소드는 다음과 같다.



| 메소드            | 설명                                                         |
| ----------------- | ------------------------------------------------------------ |
| boolean hasNext() | 컬렉션에 다음 요소가 있으면 true, <br />다음 요소가 없으면 false를 반환한다. |
| Object next()     | 다음 요소를 반환하고 그 다음 요소로 커서를 옮긴다.           |
| void remove()     | 요소를 삭제한다.                                             |


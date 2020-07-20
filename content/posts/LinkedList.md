---
title: "Java LinkedList"
date: 2020-07-20
---

# <!-- LinkedList -->

Java LinkedList 클래스는 요소를 조작하기 위해 **이중 연결 리스트**를 사용한다.

AbstractSequentialList 클래스를 상속받으며 List와 Deque 인터페이스를 구현한다.

[참고](https://www.javatpoint.com/java-linkedlist)

![LinkedList](/img/20200720-01.jpg)



## 주요 특징

* LinkedList 클래스는 중복 요소를 가질 수 있다.

* LinkedList 클래스는 삽입 순서를 유지한다.

* LinkedList 클래스는 비동기적(non-synchronized)이다.

* LinkedList 클래스는 삽입/제거 시 요소의 이동이 없기 때문에 비교적 빠르다.

* LinkedList 클래스는 list, stack, queue로 사용할 수 있다.



## 이중 연결 리스트(Doubly Linked List)

일반적인 연결 리스트(Linked List)의 노드들은 다음 노드를 가리키는 포인터(next)만 가지고 있어 단방향으로만 탐색이 가능하다.

그러나 이중 연결 리스트(Doubly Linked List)는 다음 노드 포인터(next)와 이전 노트 포인터(prev)를 가지고 있어 **양방향 탐색**이 가능하다.

다시 말해, 노드와 노드가 앞 뒤로 서로 연결되어 있다.

![LinkedList](/img/20200720-02.jpg)



## LinkedList 선언

```java
LinkedList list = new LinkedList();//타입 미설정
LinkedList<Integer> num1 = new LinkedList<Integer>();//타입 설정 - int 타입만 사용 가능
LinkedList<Integer> num2 = new LinkedList<>();//new에서 타입 파라미터 생략
LinkedList<Integer> num3 = new LinkedList<Integer>(Arrays.asList(1, 2)); //생성시 값 추가
```

LinkedList와 [ArrayList의 선언 방법](https://kimkonpig.github.io/posts/arraylist/)은 동일하다.

한가지 다른 점은 LinkedList는 선언 시 크기를 미리 설정할 수 없다. 

JDK 5.0 이후 부터 타입 안정성을 위해 제너릭스(Generics) 개념이 도입되었다.

위 예시의 num1, num2처럼 LinkedList에 데이터타입을 명시하여 사용하면

잘못된 타입으로 캐스팅하는 오류를 예방할 수 있다.

제너릭스 사용해서 선언 시 데이터타입은 원시타입이 아닌 참조타입(wrapper class)를 사용해야 한다.



## LinkedList  주요 메소드

LinkedList 사용 시 자주 쓰는 메소드 몇 가지만 소개한다. 다른 메소드를 확인하고 싶다면 [여기](https://www.javatpoint.com/java-linkedlist)로.

| 메소드                                            | 설명                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| boolean add(E e) / void add(int index, E element) | LinkedList 맨 뒤에 value를 추가하거나, 지정한 index에 value를 추가한다. |
| void addFirst(E e) / void addLast(E e)            | LinkedList 맨 앞 또는 맨 뒤에 데이터를 추가한다.             |
| E get(int index) / E getFirst() / E getLast()     | 해당 index 또는 맨 앞, 맨 뒤의 value를 반환한다.             |
| int indexOf(Object o) / int lastIndexOf(Object o) | 찾고자 하는 값(o)이 LinkedList 맨 앞 또는 맨 뒤에 있으면 해당 index를 반환한다. 없으면 -1 반환. |
| boolean offer(E e)                                | LinkedList 마지막에 요소를 추가한다.                         |
| E peek()                                          | LinkedList 첫번째 요소를 반환한다. (제거X)                   |
| E poll()                                          | LinkedList 첫번째 요소를 반환 후 제거한다.                   |
| int size()                                        | LinkedList의 크기를 반환한다.                                |
| E remove() / E remove(int index)                  | LinkedList의 첫번째 요소 또는 해당 index의 요소를 제거한다.  |



## LinkedList 활용 예

- 첫번째 : LinkedList Iterator를 사용한 출력

```java
import java.util.*;

public class MyClass {
    public static void main(String args[]) {
      LinkedList<String> list = new LinkedList<String>();
      
      list.add("Dokdo");
      list.add("is");
      list.add("Korean");
      list.add("territory");
      
      Iterator<String> itr = list.iterator();
      while(itr.hasNext()){
          System.out.println(itr.next());
      }
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2bjo)



* 두번째 : add와 remove 메소드 사용, Object 출력

```java
import java.util.*;

public class MyClass {
    public static void main(String args[]) {
      LinkedList<String> list = new LinkedList<String>();
      
      list.add("Dokdo");
      list.add("is");
      list.add("Korean");
      list.add("territory");
      System.out.println("Before add() : " + list);
      
      list.add("remover");
      list.add(2, "clearly");
      System.out.println("After add() : " + list);
      
      list.removeLast();
      System.out.println("After removeLast() : " + list);
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2bjs)



* 세번째 : descendingIterator 메소드 사용하여 마지막 입력값부터 출력

* Collections 클래스의 sort 메소드 사용해서 동일하게 출력 가능
  - Collections.sort(list, Comparator.reverseOrder());

```java
import java.util.*;

public class MyClass {
    public static void main(String args[]) {
      LinkedList<String> list = new LinkedList<String>();
      
      list.add("Dokdo");
      list.add("is");
      list.add("Korean");
      list.add("territory");
      
      Iterator itr = list.descendingIterator();
      while(itr.hasNext()){
          System.out.println(itr.next());
      }
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2bjt)


---
title: "Java ArrayList"
date: 2020-07-17
---

# <!--ArrayList-->

Java ArrayList 클래스는 요소를 저장하기 위해 동적배열을 사용한다. 배열과 같지만 크기 제한이 없다.

메소드를 사용해 언제든 요소를 추가/제거할 수 있다. C++의 Vector와 비슷하다.

ArrayList는 [List 인터페이스](https://www.javatpoint.com/java-list)를 구현하기 때문에 List 인터페이스의 모든 메소드를 사용할 수 있다.

ArrayList는 중복 요소를 가질 수 있으며 삽입 순서를 유지한다. [참고](https://www.javatpoint.com/java-arraylist)

![ArrayList](/img/20200716-01.JPG)



## 주요 특징

- ArrayList 클래스는 중복 요소를 가질 수 있다.

- ArrayList 클래스는 삽입 순서를 유지한다.

- ArrayList 클래스는 비동기적(non-synchronized)이다.

- ArrayList 클래스는 index 기반으로 랜덤 접근이 가능하다.

- ArrayList에서 어떤 요소가 제거될 때 요소의 대량 이동이 발생하므로 LinkedList 보다 느리다.(*little bit slower*)



## ArrayList 선언

```java
ArrayList list = new ArrayList(); //타입 미설정
ArrayList<Integer> num1 = new ArrayList<Integer>(); //타입 설정 - int 타입만 사용 가능
ArrayList<Integer> num2 = new ArrayList<>(); //new에서 타입 파라미터 생략
ArrayList<Integer> num3 = new ArrayList<>(10); //초기 크기 설정
ArrayList<Integer> num4 = new ArrayList<>(Arrays.asList(1,2,3)); //생성 시 값 추가
```

JDK 5.0 이후 부터 타입 안정성을 위해 제너릭스(Generics) 개념이 도입되었다.

위 예시의 num1, num2처럼 ArrayList에 데이터타입을 명시하여 사용하면 

잘못된 타입으로 캐스팅하는 오류를 예방할 수 있다.

제너릭스 사용해서 선언 시 데이터타입은 원시타입이 아닌 참조타입(wrapper class)를 사용해야 한다.



## ArrayList 주요 메소드

ArrayList 사용 시 자주 쓰는 메소드 몇 가지만 소개한다. 다른 메소드를 확인하고 싶다면 [여기](https://www.javatpoint.com/java-arraylist)로.

| 메소드                       | 설명                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| void add(int index, E value) | index에 value를 추가한다. index 생략 시 ArrayList 맨 뒤에 value가 추가된다. |
| E remove(int index)          | index의 value를 제거한다.                                    |
| void clear()                 | ArrayList의 모든 요소를 제거한다.                            |
| int size()                   | ArrayList의 크기를 반환한다.                                 |
| E get(int index)             | index의 value를 반환한다.                                    |
| boolean contains(Object o)   | 찾고자 하는 값(o)이 ArrayList에 있으면 true를 반환한다.      |
| int indexOf(Object o)        | 찾고자 하는 값(o)이 ArrayList에 있으면 해당 index를 반환한다. 없으면 -1 반환. |



## ArrayList 활용 예

* **첫번째 : ArrayList Object 출력**

```java
import java.util.*;

public class Example{
    public static void main(String[] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("kim");
        list.add("kon");
        list.add("pig");
        
        System.out.println(list);
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2aPr)



* **두번째 : Iterator를 사용한 출력**

```java
import java.util.*;

public class Example{
    public static void main(String[] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("kim");
        list.add("kon");
        list.add("pig");
        
        Iterator itr = list.iterator();
        while(itr.hasNext()){
            System.out.println(itr.next());
        }
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2aPu)



* **세번째 : For-each loop를 사용한 출력**

```java
import java.util.*;

public class Example{
    public static void main(String[] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("kim");
        list.add("kon");
        list.add("pig");
        
        for(String values:list){
            System.out.println(values);
        }
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2aPv)



* **네번째 : Collections 클래스의 sort 메소드를 사용한 오름차순 정렬**

```java
import java.util.*;

public class SortArrayList{
    public static void main(String[] args){
        ArrayList<String> list1 = new ArrayList<>();
        list1.add("Mango");
        list1.add("Apple");
        list1.add("Banana");
        list1.add("Grapes");
        
        Collections.sort(list1);
        
        for(String fruit : list1){
            System.out.println(fruit);
        }
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2aPw)



* **다섯번째 :  Collections 클래스의 sort 메소드와 Comparator 클래스의 reverseOrder 메소드를 사용한 내림차순 정렬**

```java
import java.util.*;

public class SortArrayList{
    public static void main(String[] args){
        ArrayList<String> list1 = new ArrayList<>();
        list1.add("Mango");
        list1.add("Apple");
        list1.add("Banana");
        list1.add("Grapes");
        
        Collections.sort(list1, Comparator.reverseOrder());
        
        for(String fruit : list1){
            System.out.println(fruit);
        }
    }
}
```

[코드 결과 확인](https://www.jdoodle.com/embed/v0/2aPy)




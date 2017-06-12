# Part 2-1 Java
* [JVM에 대해서, GC의 원리](#jvm에-대해서,-gc의-원리)
* [Collection](#collection)
* [Annotation](#annotation)
* [Generic](#generic)
* [final](#final)
* [Overriding vs Overloading](#overriding-vs-overloading)
* [Access Modifier](#access-modifier)
* [Wrapper class](#wrapper-class)
* [Multi-Thread 환경에서의 개발](#multi-thread-환경에서의-개발)

[뒤로](https://github.com/JaeYeopHan/for_beginner)

</br>

## JVM에 대해서, GC의 원리
그림과 함께 설명해야 하는 부분이 많아 링크를 첨부합니다.  
* [Java Virtual Machine에 대해서](http://asfirstalways.tistory.com/158)
* [Garbage Collection 에 대해서](http://asfirstalways.tistory.com/159)


[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Collection
Java Collection에는 `List`, `Map`, `Set` 인터페이스를 기준으로 여러 구현체가 존재한다. 이에 더해 `Stack`과 `Queue` 인터페이스도 존재한다.
* List  
대표적인 구현체로는 `ArrayList`가 존재한다. DataStructure 부분에서 설명한 Array라고 생각하면 쉽지만 내부적으로는 `Red-Black tree`로 구성되어 있다. 이외에도 `LinkedList` 등의 구현체가 존재한다.

* Map  
대표적인 구현체로는 `HashMap`이 존재한다. (밑에서 살펴볼 멀티스레드 환경에서의 개발 부분에서 HashTable과의 차이점에 대해 살펴본다.) key-value의 구조로 이루어져 있으며 Map에 대한 구체적인 내용은 DataStructure부분의 hashtable과 일치한다. key를 기준으로 중복된 값을 저장하지 않으며 순서를 보장하지 않는다. key에 대해서 순서를 보장하기 위해서는 `LinkedHashMap`을 사용한다.

* Set  
대표적인 구현체로는 `HashSet`이 존재한다. `value`에 대해서 중복된 값을 저장하지 않는다. 사실 Set 자료구조는 Map의 key-value 구조에서 key 대신에 value가 들어가 value를 key로 하는 자료구조일 뿐이다. 마찬가지로 순서를 보장하지 않으며 순서를 보장해주기 위해서는 `LinkedHashSet`을 사용한다.

* Stack과 Queue  
DataStructure 부분의 설명을 참고하면 된다.


[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Annotation
어노테이션이란 본래 주석이란 뜻으로, 인터페이스를 기반으로 한 문법이다. 주석과는 그 역할이 다르지만 주석처럼 코드에 달아 클래스에 특별한 의미를 부여하거나 기능을 주입할 수 있다. 또 해석되는 시점을 정할 수도 있다.(Retention Policy) 어노테이션에는 크게 세 가지 종류가 존재한다. JDK에 내장되어 있는 `built-in annotation`과 어노테이션에 대한 정보를 나타내기 위한 어노테이션인 `Meta annotation` 그리고 개발자가 직접 만들어 내는 `Custom Annotation`이 있다. built-in annotation은 상속받아서 메소드를 오버라이드 할 때 나타나는 @Override 어노테이션이 그 대표적인 예이다. 어노테이션의 동작 대상을 결정하는 Meta-Annotation에도 여러 가지가 존재한다.

#### Reference
* http://asfirstalways.tistory.com/309


[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Generic
제네릭은 자바에서 안정성을 맡고 있다고 할 수 있다.  다양한 타입의 객체들을 다루는 메서드나 컬렉션 클래스에서 사용하는 것으로, 컴파일 과정에서 타입체크를 해주는 기능이다. 객체의 타입을 컴파일 시에 처크하기 때문에 객체의 타입 안전성을 높이고 형변환의 번거로움이 줄어든다. 자연스럽게 코드도 더 간결해진다. 예를 들면, Collection에 특정 객체만 추가될 수 있도록, 또는 특정한 클래스의 특징을 갖고 있는 경우에만 추가될 수 있도록 하는 것이 제네릭이다. 이로 인한 장점은 collection 내부에서 들어온 값이 내가 원하는 값인지 별도의 로직처리를 구현할 필요가 없어진다. 또한 api를 설계하는데 있어서 보다 명확한 의사전달이 가능해진다.

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## final
* final class  
다른 클래스에서 상속하지 못한다.

* final method  
다른 메소드에서 오버라이딩하지 못한다.

* final variable  
변하지 않는 상수값이 되어 새로 할당할 수 없는 변수가 된다.

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Overriding vs Overloading
* 오버라이딩(Overriding)  
상속받은 클래스에 존재하는 메소드를 하위 클래스에서 필요에 맞게 재정의하는 것을 의미한다.
* 오버로딩(Overloading)  
같은 클래스 내에 return value와 메소드명이 동일한 메소드를 매개변수만 다르게 만들어 다양한 상황에 메소드가 호출될 수 있도록 하는 것입니다.

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Access Modifier
변수 또는 메소드의 접근 범위를 설정해주기 위해서 사용하는 Java의 예약어를 의미하며 총 네 가지 종류가 존재한다.

* public  
어떤 클래스에서라도 접근이 가능하다.

* protected  
클래스가 정의되어 있는 해당 패키지 내 그리고 해당 클래스를 상속받은 외부 패키지의 클래스에서 접근이 가능하다.

* (default)  
클래스가 정의되어 있는 해당 패키지 내에서만 접근이 가능하도록 접근 범위를 제한한다.

* private  
정의된 해당 클래스에서만 접근이 가능하도록 접근 범위를 제한한다.

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Wrapper class
기본 자료형(Primitive data type)에 대한 클래스 표현을 Wrapper class라고 한다. `Integer`, `Float`, `Boolean` 등이 Wrapper class의 예이다. int를 Integer라는 객체로 감싸서 저장해야 하는 이유가 있을까? 일단 컬렉션에서 제네릭을 사용하기 위해서는 Wrapper class를 사용해줘야 한다. 또한 `null` 값을 반환해야만 하는 경우에는 return type을 Wrapper class로 지정하여 `null`을 반환하도록 할 수 있다. 하지만 이러한 상황을 제외한 일반적인 상황에서는 Wrapper class를 사용해야 하는 이유는 객체지향적인 프로그래밍을 위한 프로그래밍이 아니고서야 없다. 일단 해당 값을 비교할 때, Primitive data type인 경우에는 `==`로 바로 비교해줄 수 있다. 하지만 Wrapper class인 경우에는 `.intValue()` 메소드를 통해 해당 Wrapper class의 값을 가져와 비교해줘야 한다.

### AutoBoxing
JDK 1.5 부터는 `AutoBoxing`과 `AutoUnBoxing`을 제공한다. 이 기능은 각 Wrapper class에 상응하는 Primitive data type일 경우에만 가능하다.

```java
List<Integer> lists = new ArrayList<>();
lists.add(1);
```
우린 `Integer`라는 Wrapper class로 설정한 collection에 데이터를 add할 때 Integer 객체로 감싸서 넣지 않는다. 자바 내부에서 `AutoBoxing`해주기 때문이다.

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

## Multi-Thread 환경에서의 개발
개발을 시작하는 입장에서 멀티 스레드를 고려한 프로그램을 작성할 일이 별로 없고 실제로 부딪히기 힘든 문제이기 때문에 많은 입문자들이 잘 모르고 있는 부분 중 하나라고 생각한다. 하지만 이 부분은 정말 중요하며 고려하지 않았을 경우 엄청난 버그를 양산할 수 있기 때문에 정말 중요하다.

### Field member
`필드(field)`란 클래스에 변수를 정의하는 공간을 의미한다. 이곳에 변수를 만들어두면 메소드 끼리 변수를 주고 받는 데 있어서 참조하기 쉬우므로 정말 편리한 공간 중 하나이다. 하지만 객체가 여러 스레드가 접근하는 싱글톤 객체라면 field에서 상태값을 갖고 있으면 안된다. 모든 변수를 parameter로 넘겨받고 return 하는 방식으로 코드를 구성해야 한다.

### 동기화
필드에 Collection이 불가피하게 필요할 때는 어떠한 방법을 사용할까? Java에서는 `synchronized` 키워드를 사용하여 스레드 간 race condition을 통제한다. 이 키워드를 기반으로 구현된 Collection들도 많이 존재한다. `List`를 대신하여 `Vector`를 사용할 수 있고, `Map`을 대신하여 `HashTable`을 사용할 수 있다. 하지만 이 Collection들은 제공하는 API가 적고 성능도 좋지 않다.

기본적으로는 `Collections`라는 util 클래스에서 제공되는 static 메소드를 통해 이를 해결할 수 있다. `Collections.synchroziedList()`, `Collections.synchroziedSet()`, `Collections.synchroziedMap()` 등이 존재한다.
JDK 1.7 부터는 `concurrent package`를 통해 `ConcurrentHashMap`이라는 구현체를 제공한다. Collections util을 사용하는 것보다 `synchronized` 키워드가 적용된 범위가 좁아서 보다 좋은 성능을 낼 수 있는 자료구조이다.

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

#### Personal Recommendation
* (도서) [Effective Java 2nd Edition](http://www.yes24.com/24/goods/14283616?scode=032&OzSrank=9)
* (도서) [스프링 입문을 위한 자바 객체 지향의 원리와 이해](http://www.yes24.com/24/Goods/17350624?Acode=101)


[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](#part-2-1-java)

</br>

</br>

_Java.end_  
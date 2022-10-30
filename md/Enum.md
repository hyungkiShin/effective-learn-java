### 열거 타입

- 상수 목록을 담고 있는 열거 타입.
- 특정한 변수가 가질 수 있는 값을 재현할 수 있다. (타입-세이프티 (Type-Safety) 를 보장할 수 있다.)
- 싱클톤 패턴을 구현할 때 사용하기도 좋다.

1) 특정 enum 타입이 가질 수 있는 모든 값을 순회하며 출력하라.

```java

public enum OrderStateus {
    PREPARING, SHIPPED, DELIVERING, DELIVERED
}

Arrays.Stream(OrderStateus.values()).forEach(System.out::println);

```

2) enum 은 자바의 클래스처럼 생성자, 메소드, 필드를 가질 수 있는가 ?

- 있다.

3) enum 의 값은 == 연산자로 동일성을 비교할 수 있는가 ?

```java

Order order=new Order();
        if(order.orderStatus==OrderStatus.DELIVERED){
        System.out.println("delivered")
        }
```

과제)

### 과연 어떨때 enumMap 과 enumSet 을 사용할까 ? 
enum 을 키로 쓸때는 enumMap 을 써야하고, enum 만을 담고 있을때는 enumSet 을 써야 한다.

### 그렇다면 왜 enumMap 과 enumSet 을 사용하면 좋을까 ?

1. EnumMap은 값을 찾을 때, 이늄상수가 index정보를 ordinal메소드로 제공하고 있기 때문에, 바로 찾을 수 있다.

2. 반면, HashMap은 찾을 때, key값을 hash메소드로 index로 변환하고 찾아야 한다.

3. 값을 넣을 때, EumMap은 key의 index정보로 값이 저장된 위치를 찾아서 바로 값을 넣는다.

4. 하지만, HashMap은 key값을 hash로 만들고, 배열의 크기를 조절하는 등의 일이 추가로 필요하다.

5. 때문에, 배열의 크기가 고정되고 바로 찾을 수 있는 EnumMap이 성능상 훨씬 더 효율적이다.

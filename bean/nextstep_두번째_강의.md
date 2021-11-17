# 두번째 강의



### 레거시 코드가 사용하는 곳이 많아서 수정하기 어렵다면?

로직내 메서드를 분리하여 오버라이드한다.



**Q. 원시값과 문자열을 래핑해야한다는 것은**

값을 래핑한것을 다시 꺼내려고 하지마라

equals, hashcode 로 비교해라. 

assertThat(new RandomValue(4)).isEqualTo(new RandomValue(3));

getter 를 사용하지 않고 원시값을 포장 할 수 있는 방법을 고민해야한다.



객체지향의 중요한 점은 객체가 가지고 있는 맴버변수에게 메시지를 보내 물어봐야한다.



Q. 가변 객체보다는 불변 객체를 사용하도록 하자

```java
public class Position {
    private final int position;
    
    public Position(int position) {
        this.position = position;
    }
    
    public Position move() {
        return new Position(position + 1);
    }
}
```

-> 매번 이동시 객체가 새로 생긴다면 성능이슈는?

-> 캐싱을 사용하면 된다. -> 가변 객체는 방법을 찾다찾다 없으면 그때 사용해라!! 그리고 지금은 하드웨어 성능은 좋다.  기계의 비용을 신경쓰지말고 우리의 몸값을 신경쓰자.



Q 인터페이스로 커플링을 느슨하게 하라

- DI 는 스프링과 관련없이 사용할 수 있다. 
- 스프링에 너무 의존적이게 사용하지 마라
- 클래스 설계는 스프링에서 벗어날때 더 실력이 는다.





## 일급 콜렉션

Q 일급 콜렉션이란?

콜렉션을 래핑한것



팁!!

- 로컬변수는 피하자
- 생성자를 많이 만들어서 클래스를 많이 사용하도록 하여라!!!!
- 맴버변수는 불변객체로 만들어봐라
- 인덴트를 줄일때 스트림을 사용하지 말아라
- getter 메서드 사용하지 마라 (객체에게 메시지를 보내라)
  - car.isSamePosition(maxPosition) -> 너무 로직에 의존하는 메소드명이다.
  - car.isWinner(maxPosition) 처럼 네이밍을 하자
- 객체지향 코드는 테스트하기 쉬워진다.
  - TDD 를 잘하려면 객체를 꺼내지 말고 메시지를 던져라
- 객체를 아주 많이 만들다보면 단순 위임만 하는 메소드가 많이 생기는데 이것은 이상한게 아니다!!!!
  - 하지만 자바지기는 단순히 TDD 테스트를 위해 위임만하는 코드는 테스트 하지 않아도 된다고 생각한다.
  - 그럼 서비스 레이어드 테스트코드는 필요한가?



```java
private List<Car> getWinners(int maxNum) {
    List<Car> winners = new ArrayList<>);
    for (Car car : cars) {
        winners.add(car);
    }
    return winners;
}
```


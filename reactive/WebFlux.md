# WebFlux



스프링 프레임워크 5.0 버전에 추가된 웹플럭스는 리액티브 스택 웹 프레임워크이다. 

완전한 논블로킹 방식으로 동작하며 Reactive Streams back pressure 지원, Netty, Undertow, 서블릿 3.1+ 컨테이너 서버에서 실행된다.

Web MVC 를 포함한 기존의 웹 프레임워크와 함게 사용가능하다. 



## 왜 만들었나?

- 적은 쓰레드로 동시 처리 제어, 적은 하드웨어 리소스로 확장하기 위한 논플로킹 웹 스택이 필요해서
- 자바 8 에서 추가된 람다 표현식 덕분에 함수형 API 를 작성할 수 있게 되었다.



## 리액티브란?

용어의 의미 : 변화에 반응항는 것을 중심에 두고 만든 프로그래밍 모델

I/O 이벤트에 반응하는 네트워크 컴포넌트, 마우스 이벤트에 반응하는 UI 컨트롤러 등) 논블로킹은 작업을 기다리기 보단 완료되거나 데이터를 사용할 수 있게 되면 반응하므로 논블로킹도 리액티브이다.



## Programming Models

스프링 웹플럭스는 두 가지 프로그래밍 모델을 지원한다.

- Annotated controllers: 스프링 MVC 와 동일하며 spring-web 모듈에 있는 같은 어노테이션을 사용한다. 스프링 MVC 와 웹플럭스 컨트롤러 모두 리액티브(Reactor, RxJava) 리턴 타입을 지원하기 때문에 이 둘을 구분하기 어렵다. 한 가지 눈에 띄는 차이는 웹플럭스에선 @RequestBody 로 리액티브 인자를 받을 수 있다는 것이다. 
- Functional Endpoints: 경량화 된 람다 기반 함수형 프로그래밍 모델, 요청을 라우팅해주는 조그만한 라이브러리나 유틸리티 모음이라고 생각할 수 있다. Annotated controller 와 다른점은 어노테이션으로 의도를 선언해서 콜백 받기 보단 요청을 어플리케이션이 처음부터 끝까지 다 제어한다는 것이다.



## 단어 정리

### Reactive Streams

데이터 스트림을 비동기로 다룰 수 있는 공통 메카니즘



- 데이터 스트림
  - 정보를 전송할 때 사용되는 디지털 방식
- webflux
  - Reactor 에서 데이터를 통지(또는 발행, 방출) 하는 생산자(publisher)의 역할 = Flux, Mono
  - RxJava 에서 Observable(1건이상), Flowable(1건이상), Single(1건), Maybe(0~1건) 등 의 역할



## RxJava Reactor 차이

- RxJava

```java
@Test 
public void ObservableFilterTest() { 
    Observable<Integer> observable = Observable.just(1, 2, 3, 4, 5, 6, 7, 8, 9, 10) 
        .filter(n -> n % 2 == 0); 
    
    observable.test() 
        .assertValues(2, 4, 6, 8, 10) 
        .assertComplete(); 
}
```

- Reactor

```java
@Test
public void fluxFilterTest() {
    Flux<Integer> flux = Flux.just(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
        .filter(n -> n % 2 == 0);
    
    StepVerifier.create(flux)
        .expectNext(2, 4, 6, 8, 10)
        .verifiyComplete();
}
```





## 스프링을 이용한 리액티브 프로그래밍 - 기본개념

### 관찰자 패턴

일반적인 관찰자 패턴은 Subject 와 Observer 2개의 인터페이스로 구성된다. 

Observer(관찰자)는 Subject(주체)에 등록되고 Subject로 부터 알림을 수신한다. 
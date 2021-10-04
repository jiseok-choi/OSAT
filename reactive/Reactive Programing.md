# Reactive Programing



Reactive 란 멍때리는 시간을 없애고 물어보지 않아도 알려주는 것이다.



멍때리는 시간을 줄이기 위해

기존방법으로는

1. Thread 를 생성했다(Time 슬라이싱)
2. 이때문에 컨텍스트스위칭이 일어났다.

쓰레드를 생성하는 방식은 느리다



그럼?



비동기 방식으로 진행해야한다.



응답을 유지하는 방식 SSE 프로토콜 (stream) 이라고 한다.



webFlux 는 reactive-streams 라이브러리의 구현체이다.




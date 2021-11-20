## 📅 2021/11/20

<br/>

### 🏹 주간 목표

- [x] 클린코드를 위한 TDD with Java 13기 자동차 경주 수행
- [ ] 클린코드를 위한 TDD with Java 13기 로또 수행

<br/>

### 일일 체크리스트(어제 정한 목표)

- [x] TDD 자동차 경주 과제 step 4 리뷰 반영
- [x] TDD 자동차 경주 과제 step 5 진행

<br/>

### 💯 오늘 한 일

- TDD 자동차 경주 과제 step 4 리뷰 반영
- TDD 자동차 경주 과제 step 5 진행

<br/>

### 📈 내일 할 일

- TDD 자동차 경주 과제 step 5 리뷰 반영 (있다면)
- TDD 로또 과제 step 1 진행

<br/>

### 🧐 간단 회고

- 리팩토링을 진행하며 중점적으로 생각했던 것
  - 파라미터 요소중 객체화 할 수 있는 요소를 중점으로 리팩토링 시도
  - domain, view, util, exception 패키지로 기존 클래스 분리
  - InputView 로직에 domain 로직이 포함되어 관련 로직 분리
    - 테스트 코드에서도 Scanner 요소를 테스트 할 수 있다는 것을 알아냈다.
      ```java
        String data = "What_I_could_put_in_console";
        InputStream stdin = System.in;
        System.setIn(new ByteArrayInputStream(data.getBytes()));
        Scanner scanner = new Scanner(System.in);
        System.setIn(stdin);
      ```
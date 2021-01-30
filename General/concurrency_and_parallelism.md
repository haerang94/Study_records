### Concurrency 동시성

> 동시에 실행되는 것처럼 보이는 것

- 논리적인 용어
- 싱글 코어에서 멀티 스레드 동작시키기 위한 방식 (멀티 코어에서 가능)
- 멀티 태스킹 위해서 여러 개의 스레드가 번갈아가면서 실행되는 성질
- 각 스레드가 병렬적으로 실행되는 것처럼 보이지만 사실은 번갈아가면서 조금씩 실행되고 있는 것이다 (시분할 시스템)

### Parallelism 병렬성

> 실제로 작업이 동시에 처리되는 것

- 물리적인 용어
- 멀티 코어에서 멀티 스레드 동작시키는 방식
- 데이터 병렬성과 작업 병렬성이 있다

### 데이터 병렬성

> 같은 작업을 병렬 처리하는 것

- 전체 데이터를 서브 데이터로 나눈 뒤, 서브 데이터를 병렬 처리하는 것
- 멀티 코어 수만큼 쪼개서 각각의 데이터를 분리된 스레드에서 병렬처리한다

### 작업 병렬성

> 서로 다른 작업을 병렬 처리하는 것

- 웹 서버 (각각의 브라우저에서 요청한 내용을 개별 스레드에서 병렬로 처리함)

---

- 출처
  - [https://atin.tistory.com/567](https://atin.tistory.com/567)
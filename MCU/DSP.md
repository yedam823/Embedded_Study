MCU와 비슷하지만, 디지털 신호 처리 작업을 하는 프로세서(필터링, 압축, 해독, 인코딩, 복호화 등)

- 실시간 처리에 최적화됨
- 고성능 산술연산, 고속 데이터 스트림 처리
- 고속 연산, 병렬 처리를 위한 다양한 하드웨어 기능

> 구성
> 
1. SIMD(Single introduction, Multiple Data) : 하나의 명령어가 여러개의 데이터를 한번에 처리함
2. 주기억 장치와 프로그램 메모리 분리함(빠르게 접근)
3. DMA : 데이터 전송을 프로세서 개입없이 빠르게 가능

---

# Control Block

RTOS가 관리해야하는 객체마다 하나씩 있는 내부 관리 구조체

### TCB(Task Control Block)

- 관리대상 : 태스크 하나
- 담는 정보
    - 스택포인터
    - 상태 (READY / RUNNING / BLOCKED)
    - 우선순위
    - 문맥교환정보

### ECB (Event Control Block)

- 관리대상 : 세마포어, 뮤텍스, 이벤트 플래그
- 담는 정보
    - 이벤트 타입
    - 상태 / 카운트
    - 대기중인 태스크 리스트
- SCB (Semaphore) , MCB (Mutex), EFCB (Event Flag) 등의 control block이 파생됨

### QCB (Queue Control Block)

- 관리 대상 : 메세지 큐
- 담는 정보
    - 버퍼 시작 주소
    - 버퍼 크기
    - 읽기 / 쓰기 인덱스
    - 송신 / 수신 대기 태스크

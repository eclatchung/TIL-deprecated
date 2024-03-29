# SQS

## 대기열 유형

![대기열 유형](/img/sqs_유형.png)

### FIFO 대기열

- 이름 지을 때 뒤에 `.fifo`를 기입해줘야함
- 이벤트 순서가 중요하거나 중복 항목이 허용되지 않을 경우
- FIFO 대기열은 정확히 1회 처리를 제공하지만 초당 트랜잭션 수가 제한적
- FIFO대기열은 개별 메시지의 타이머를 지원하지 않음

## Amazon SQS 메시지 작업

1. 적시에 메시지 처리
2. 요청 오류 처리
3. 긴폴링 설정
4. 문제가 있는 메시지 캡처
5. 배달 못한 편지 대기열 보존 설정
6. 일관되지 않은 메시지 처리 방지
7. 요청-응답 시스템 구현

## SQS 작동 방식

### Amazon SQS SQS 아키텍처

#### 분산 대기열

분산 메시징 시스템

- 분산 시스템의 구성요소
- 대기열(Amazon SQS 서버에 분산)
- 대기열의 메시지

용어

- 생산자 : 메시지를 대기열로 전송하는 구성요소
- 소비자 : 대기열의 메시지를 수신하는 구성요소

#### 메시지 수명 주기

![메시지 수명 주기](/img/sqs-message-lifecycle-diagram.png)

1. 생서자(Component1)는 메시지 A를 대기열로 전송하고 해당 메시지는 Amazon SQS 서버에 중복 분산 됨
2. 소비자 (Component2)는 메시지를 처리할 준비가 될때 대기열에서 메시지를 소비하고 메시지 A가 반환됨. 메시지 A는 처리되는 동안 대기열에 그대로 남아있고 `제한 시간 초과`가 지속 되는 동안 후속 수신 요청으로 반환되진 않음
3. 소비자(Component2)는 대기열에서 메시지 A를 삭제하여 제한 시간 초과가 만료되면 이 메시지가 수신되어 다시 처리되지 못하도록 함.

- 최대 메시지 보존기간을 넘길동안 대기열에 존재해온 메시지를 삭제 / 기본 메시지 보존 기간은 4일
  - `SetQueueAttributes`작업 진행시 보존기간을 60초 14일까지 지속.

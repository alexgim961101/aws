# 05. Serverless — 서버리스와 이벤트 기반 아키텍처

## 목표

Lambda 중심의 서버리스 API를 구축하고, SQS를 이용한 비동기 처리 패턴을 익힌다.

## 이론

- [ ] Lambda 실행 모델: 실행 환경 수명주기, 콜드 스타트, 동시성(예약·프로비저닝), 타임아웃·메모리 설정
- [ ] Lambda와 VPC: VPC 연결이 필요한 경우와 대가(ENI), 환경 변수와 시크릿 다루기
- [ ] API Gateway: REST API vs HTTP API 차이, Lambda 프록시 통합, 스로틀링
- [ ] SQS: 표준 vs FIFO, 가시성 타임아웃, DLQ(Dead Letter Queue), 멱등성 있는 컨슈머 설계
- [ ] SNS와 팬아웃 패턴, EventBridge: 이벤트 버스, 규칙, 스케줄러
- [ ] Step Functions 개요: 어떤 워크플로에서 Lambda 체인보다 나은가
- [ ] 서버리스 설계 패턴: 동기 API + 비동기 워커 분리, 이벤트 기반 아키텍처의 장단점

## 실습 (labs/)

- API Gateway(HTTP API) + Lambda + DynamoDB로 CRUD API 구성
- 쓰기 요청을 SQS로 보내고 별도 Lambda 컨슈머가 처리하는 비동기 경로 추가
- 컨슈머에서 강제로 실패시켜 DLQ로 메시지가 이동하는 것 확인

⚠️ 비용: 이 단계는 대부분 프리 티어 범위. 다만 프로비저닝 동시성은 상시 과금이므로 실습 금지 항목.

## 완료 기준

- notes/ 에 이론 정리 작성
- API 호출 → 비동기 처리 → DLQ 동작까지 검증
- apply → destroy 완주

## 셀프 체크

1. 콜드 스타트가 발생하는 조건과 완화 방법 세 가지는?
2. SQS 가시성 타임아웃을 Lambda 타임아웃보다 짧게 잡으면 어떤 버그가 생기는가?
3. 같은 메시지가 두 번 처리될 수 있는 이유와, 컨슈머를 멱등하게 만드는 방법은?
4. SNS와 SQS와 EventBridge — 각각 언제 선택하는가?
5. 이 아키텍처에서 요청이 유실될 수 있는 지점과 그것을 막는 장치는?

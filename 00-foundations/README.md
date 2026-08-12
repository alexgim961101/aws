# 00. Foundations — 계정과 도구 준비

## 목표

실습을 안전하게(보안·비용) 시작할 수 있는 계정 상태를 만들고, 이후 모든 단계에서 사용할 도구(CLI, Terraform)를 준비한다.

## 이론

- [ ] AWS 글로벌 인프라: 리전, 가용 영역(AZ), 엣지 로케이션 — 서비스가 리전/AZ/글로벌 중 어느 범위에 속하는지 구분
- [ ] 계정 구조와 루트 계정: 루트 계정의 위험성, MFA, 루트를 써야 하는 유일한 작업들
- [ ] IAM 기초: 유저·그룹·역할·정책의 관계, 자격 증명 기반 vs 리소스 기반 정책
- [ ] 액세스 키 vs 역할(임시 자격 증명): 왜 장기 키를 피해야 하는가
- [ ] AWS CLI 설정: 프로필, IAM Identity Center(SSO) 로그인
- [ ] AWS 요금 구조: 과금 단위(시간·요청·전송량), 프리 티어 범위, 데이터 전송 비용의 함정
- [ ] Terraform 기초: provider, resource, state의 개념과 역할, plan/apply/destroy 흐름, 변수와 모듈 맛보기

## 실습 (labs/)

1. 루트 계정 MFA 설정, 작업용 IAM 유저(또는 Identity Center 유저) 생성 — 콘솔
2. **AWS Budgets 알람 설정** (예: 월 $10 초과 시 이메일) — 이후 모든 실습의 안전장치
3. AWS CLI 프로필 구성 및 `aws sts get-caller-identity` 확인
4. Terraform으로 첫 리소스(S3 버킷) 생성 → plan 출력 읽기 → destroy

## 완료 기준

- notes/ 에 이론 정리 작성
- Budget 알람 동작 확인 (테스트 알람 수신)
- Terraform apply → destroy 사이클 1회 완주

## 셀프 체크

1. 리전과 AZ의 차이는? Multi-AZ 배치가 막아주는 장애와 못 막는 장애는?
2. 루트 계정으로만 할 수 있는 작업 두 가지는?
3. EC2에서 실행되는 앱에 S3 접근 권한을 줄 때 액세스 키 대신 무엇을 쓰고, 왜 그게 더 안전한가?
4. Terraform state 파일은 무엇을 담고 있고, 왜 잃어버리면 곤란한가?
5. `terraform plan`이 "변경 없음"인데 실제 인프라와 다를 수 있는 경우는 언제인가?

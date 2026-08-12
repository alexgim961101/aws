# 07. Security — 보안 심화

## 목표

IAM 정책 평가를 정확히 이해하고, "코드에 비밀이 없는" 구조와 최소 권한 설계를 실전 수준으로 만든다.

## 이론

- [ ] IAM 심화: 정책 평가 로직(명시적 Deny > SCP > 경계 > 세션 정책 > 자격 증명/리소스 정책), 정책 문법 정독
- [ ] AssumeRole: 역할 전환의 동작 원리, 신뢰 정책, 역할 체이닝, 외부 ID
- [ ] Permission Boundary: 위임된 관리에서의 상한선 설정
- [ ] KMS: 고객 관리형 키, 봉투 암호화, 키 정책, 서비스별 암호화 통합(S3/EBS/RDS)
- [ ] **비밀 관리 심화**:
  - Secrets Manager: 자동 로테이션(RDS 연동), 비용
  - Parameter Store: 계층 구조, SecureString, Secrets Manager와의 선택 기준
  - 앱에 비밀을 주입하는 패턴: ECS 태스크 정의 `secrets`, Lambda 환경변수 + KMS, EC2/SSM
  - 개발 환경 비밀 관리: 로컬에서 비밀 다루기, git 유출 방지(gitleaks, pre-commit 훅)
- [ ] WAF: 관리형 규칙, 레이트 제한
- [ ] GuardDuty · Security Hub · Config 개요: 탐지·감사 서비스의 역할 분담
- [ ] 최소 권한 설계 실전: 사람 / 앱 / CI 각각의 권한 전략

## 실습 (labs/)

- 03의 RDS 자격증명을 Secrets Manager로 이관 + 자동 로테이션 설정
- 앱(ECS 또는 Lambda)이 시크릿을 런타임에 읽도록 변경 — 코드·환경변수에 평문 비밀 제거
- S3 버킷에 KMS 고객 관리형 키 암호화 적용
- gitleaks를 pre-commit에 걸어 비밀 커밋 차단 확인

⚠️ 비용: Secrets Manager는 시크릿당 월 과금(소액), KMS 고객 관리형 키는 월 $1 + 요청 과금.

## 완료 기준

- notes/ 에 이론 정리 작성 (특히 IAM 정책 평가 순서도)
- 로테이션 후에도 앱이 DB 접속을 유지하는 것 확인
- apply → destroy 완주

## 셀프 체크

1. 자격 증명 정책과 리소스 정책이 하나라도 Allow면 허용되는 경우와, 둘 다 필요해지는 경우(크로스 계정)는?
2. Secrets Manager와 Parameter Store를 선택하는 기준 세 가지는?
3. ECS 태스크 정의의 `environment`와 `secrets`의 차이, 그리고 후자가 안전한 이유는?
4. 봉투 암호화에서 데이터 키와 KMS 키의 역할 분담은?
5. CI 파이프라인에 AdministratorAccess를 주면 안 되는 이유와 대안은?

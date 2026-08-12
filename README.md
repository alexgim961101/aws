# AWS 실전 운영 학습

실 운영 환경에서 매끄럽게 AWS를 사용하는 것을 목표로 하는 학습 저장소.
실제 서비스가 성장하는 순서대로 단계(Phase)를 밟아가며, 각 단계마다 **이론 정리 + Terraform 실습**을 병행한다.

## 학습 규칙

- 각 phase 디렉토리 구성: `README.md`(목표·주제·완료 기준) + `notes/`(이론 정리) + `labs/`(Terraform 코드)
- 실습은 **apply → 검증 → destroy** 까지 완료해야 끝 (비용 누수 방지)
- 각 phase의 셀프 체크 질문에 스스로 답할 수 있으면 다음 단계로 진행
- 서비스 단위 딥다이브는 본문에 넣지 않고 `reference/`에 누적 (본문은 운영 흐름 유지)
- 실습 전 필수: 00 단계에서 Budget 알람부터 설정

## 전체 목차

| Phase | 주제 | 핵심 내용 | 진행 |
|-------|------|-----------|------|
| [00-foundations](00-foundations/) | 계정과 도구 준비 | 글로벌 인프라, IAM 기초, CLI, 예산 알람, Terraform 기초 | ⬜ |
| [01-networking](01-networking/) | VPC 제대로 설계하기 | 서브넷·라우팅·NAT, SG vs NACL, VPC 엔드포인트 | ⬜ |
| [02-compute](02-compute/) | EC2 기반 웹서비스 | EC2, ALB, ASG, Route 53, ACM(HTTPS), CloudFront | ⬜ |
| [03-storage-db](03-storage-db/) | 데이터 계층 | S3, EBS/EFS, RDS, DynamoDB, ElastiCache | ⬜ |
| [04-containers](04-containers/) | 컨테이너 운영 | ECR, ECS/Fargate, 배포 전략, ECS vs EKS | ⬜ |
| [05-serverless](05-serverless/) | 서버리스·이벤트 기반 | Lambda, API Gateway, SQS/SNS, EventBridge | ⬜ |
| [06-observability](06-observability/) | 관측 가능성 | CloudWatch, CloudTrail, X-Ray, 알람 설계 | ⬜ |
| [07-security](07-security/) | 보안 심화 | IAM 심화, KMS, 비밀 관리, WAF, 최소 권한 설계 | ⬜ |
| [08-data-batch](08-data-batch/) | 데이터 파이프라인·배치 | 데이터 레이크, Glue, Athena, 배치 설계 | ⬜ |
| [09-hybrid](09-hybrid/) | 온프레미스·엣지 연계 | VPN, Direct Connect, Transit Gateway, SSM | ⬜ |
| [10-cost-ops](10-cost-ops/) | 비용·자동화·운영 | 비용 최적화, CI/CD(OIDC), 백업, DR | ⬜ |
| [11-account-governance](11-account-governance/) | 계정 관리와 거버넌스 | Organizations, SCP, Identity Center, 자격 증명 수명주기 | ⬜ |
| [reference](reference/) | 서비스별 딥다이브 | 학습 중 깊이 팔 주제를 수시 누적 | — |

진행 표시: 완료한 phase는 ⬜ → ✅ 로 변경.

## 학습 흐름

- **01 → 05**: 서비스 하나를 띄우는 여정 (네트워크 → 컴퓨팅 → 데이터 → 컨테이너 → 서버리스)
- **06 → 07**: 운영 품질 (관측 가능성, 보안)
- **08 → 09**: 폭 확장 (데이터 파이프라인, 하이브리드)
- **10 → 11**: 조직 수준 운영 (비용·자동화, 멀티 계정 거버넌스)

업무에서 이미 AWS를 사용 중이라면 00은 빠르게 훑고 01부터 밀도를 높인다.

## 실습 환경

- 개인 AWS 계정 (소액 과금 감수, 단 모든 실습은 destroy로 마무리)
- 도구: AWS 콘솔(개념 확인) + Terraform(코드화), AWS CLI
- 비용 주의 리소스는 각 phase README에 ⚠️ 표시

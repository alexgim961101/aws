# 10. Cost & Ops — 비용, 자동화, 운영 성숙도

## 목표

비용을 구조적으로 관리하는 방법을 익히고, 액세스 키 없는 CI/CD 배포 파이프라인과 백업·DR 전략을 갖춘다.

## 이론

- [ ] 비용 분석: Cost Explorer 읽는 법, 비용 할당 태그 전략(팀·서비스·환경), Cost Anomaly Detection
- [ ] 약정 할인: Savings Plans vs 예약 인스턴스(RI), 언제 어떤 것을 사는가
- [ ] 흔한 비용 낭비 카탈로그: 유휴 리소스, 미사용 EIP, NAT 통과 트래픽, 로그 무제한 보존, 오버프로비저닝
- [ ] CI/CD: GitHub Actions + **OIDC 연동** — 장기 액세스 키 없이 AWS에 배포하는 구조
- [ ] Terraform 운영: 원격 state(S3 + 잠금), plan 리뷰 문화, 환경 분리(workspace vs 디렉토리)
- [ ] 백업: AWS Backup으로 백업 중앙화, 백업 정책과 복원 테스트
- [ ] DR 패턴: RTO/RPO 정의, 백업·복원 / 파일럿 라이트 / 웜 스탠바이 / 액티브-액티브 비용 스펙트럼

## 실습 (labs/)

- Terraform state를 S3 백엔드로 이전 (버전닝 + 잠금)
- GitHub Actions OIDC로 AWS 역할을 assume → `terraform plan`을 PR에서 자동 실행하는 파이프라인 구성
- 비용 할당 태그 활성화 + Cost Explorer에서 태그별 비용 확인
- AWS Backup으로 EBS/RDS 백업 계획 생성 → 복원 테스트 1회

## 완료 기준

- notes/ 에 이론 정리 작성 (특히 "우리 계정 비용 점검 체크리스트")
- 액세스 키 없이 GitHub Actions에서 AWS 인증 성공
- 백업 → 복원 사이클 1회 완주

## 셀프 체크

1. OIDC 배포가 액세스 키 방식보다 안전한 이유를 신뢰 정책 관점에서 설명할 수 있는가?
2. Savings Plans와 RI의 차이는? 어떤 워크로드에 각각 적합한가?
3. RTO와 RPO의 차이, 그리고 각 DR 패턴이 두 지표를 어떻게 바꾸는가?
4. Terraform state를 S3에 두고 잠금을 거는 이유는? 잠금이 없으면 어떤 사고가 나는가?
5. 이번 달 비용이 갑자기 늘었다는 알림을 받았을 때, 원인을 추적하는 순서는?

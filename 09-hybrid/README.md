# 09. Hybrid — 온프레미스·엣지 연계

## 목표

온프레미스와 AWS를 연결하는 선택지들을 이해하고, 멀티 VPC 허브인 Transit Gateway를 직접 구성해본다.

## 이론

- [ ] Site-to-Site VPN: 구성 요소(VGW/TGW, CGW), 터널 이중화, 대역폭 한계
- [ ] Direct Connect: 전용선의 효용(대역폭·지연·비용), VPN과의 선택 기준, DX + VPN 백업 패턴
- [ ] Transit Gateway: 멀티 VPC·온프레미스 허브, VPC 피어링과의 비교(전이 라우팅)
- [ ] 하이브리드 DNS: Route 53 Resolver 인바운드/아웃바운드 엔드포인트 — 사내 DNS와 양방향 조회
- [ ] Systems Manager: 하이브리드 활성화로 온프레미스 서버 관리(Session Manager, Patch Manager)
- [ ] Storage Gateway · Outposts · Snow 패밀리 개요: 어떤 문제를 푸는 서비스인가
- [ ] 네트워크 설계 관점: 온프레미스와 CIDR 충돌 방지, 경로 광고 범위 설계

## 실습 (labs/)

- VPC 2개를 Transit Gateway로 연결(온프레미스 연계 시뮬레이션)
- 각 VPC의 인스턴스 간 통신을 TGW 라우팅 테이블로 제어 (허용/차단 실험)
- ⚠️ VPN·DX는 상시 과금 + 물리 조건이 필요하므로 이론 위주로 정리 (VPN은 구성 요소와 라우팅 흐름을 그림으로)

⚠️ 비용: TGW는 연결(attachment)당 시간 과금. 실습 후 즉시 destroy.

## 완료 기준

- notes/ 에 이론 정리 작성 (VPN vs DX vs TGW 비교표 포함)
- TGW 라우팅 제어 실험 완주
- apply → destroy 완주

## 셀프 체크

1. VPC 피어링 대신 TGW를 선택해야 하는 시점은? (몇 개 VPC부터, 어떤 요구부터)
2. Site-to-Site VPN 터널이 2개인 이유는?
3. DX가 있어도 VPN을 함께 두는 이유는?
4. 사내 서버가 AWS 프라이빗 도메인(예: RDS 엔드포인트)을 조회하려면 무엇이 필요한가?
5. 온프레미스 CIDR과 VPC CIDR이 겹치면 무슨 일이 생기고, 사전에 어떻게 막는가?

- KCMVP 서버 -> 상용 VPN 교체
  - 과제 범위가 아니며
  - 보통 CC 인증을 받은 VPN 서버는 KCMVP 기능도 포함하고 있음
  - 군에서 사용중인 VPN 서버 (또는 CC 인증 받은 서버) 가 있으며
  - 이를 그대로 활용하면 될 듯
  - 이 경우
    - 클라이언트 파트에서 상용 VPN 서버에 맞도록 클라이언트를 제공하여야 함
    - VPN 서버는 ID/PASS 기반으로 동작하며 이 경우 단말에 대한 인증은 하지 않는데
    - 우리의 경우 HW 단말 까지 포함되기에 ID/PASS + KCMVP 쌍으로 키 관리
- 사용자 및 단말 인증 순서를 나열하자면
  1) HW 단말 -(인증)-> 스마트 단말
  2) 스마트 단말 -(인증, OpenSSL)-> VPN 서버
  3) 스마트 단말 -(인증)-> 사용자 인증 서버
- 그림에서 KCMVP 서버 이름을 우선 `구간 암호화 서버` 로 바꾸고 색상도 바꿔서 우리 개발영역이 아님을 표시
- 사용자/단밀 인증 관련
  - qSIM + eSIM 관리서버 영역으로 이동
- 5G 보안 GW 는
  - 5G IPS 로서 control/user plane 으로 구분
    - core 의 각 모듈 (AMF,SMF,...) 을 사용하는 특별한 인터페이스 (N1~N9) 가 있음
    - 이러한 인터페이스에 특화된 보안이 포함되어야 함 (N3 인터페이스만 강조할 경우 IPS 기능만 보임)
- 스마트폰 키면
  - 국방망 5G 와 인증 관련 기능 진행 (USIM 기반, AUSF)
    - PDU 세션 연결
  - 단말 -(인증)-> HW 단말
  - qSIM 인증 (5G 사용자에 대한 2차 인증)
    - 국방망 (USIM 과 같은 의미로 양자 모듈 내부에 사용자 정보 포함) 사용 사용자 식별정보
  - 구간 암호화 서버를 통해 인증
  - 서비스 사용
- 
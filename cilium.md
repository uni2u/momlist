
- iptables을 기반으로 IP와 Port기반의 전통적인 포워딩 기술은 벌써 20년이라는 세월동안 널리 사용되어 왔다.
- 특히 퍼블릭/프라이빗 클라우드 제품군들 모두 iptables기반의 Security Group등을 기본으로 제공하고 있고 Kubernetes 마저도 CNI 핵심으로 iptables을 활용하고 있다.

- 동적으로 변화하고 매우 복잡한 마이크로서비스를 사용하는 시대에 전통적인 방식의 IP, Port관리는 비효율적인 측면이 없지 않다.
- BPF을 활용하여 리눅스 커널내에서 데이터 포워딩을 할 수 있고
  - Kubernetes Service기반 Load Balancing이나 istio와 같은 Service Mesh를 위한 Proxy Injection 을 통해 여러 활용을 할 수 있다.

- 고효율 BPF Datapath
  - 모든 데이터 경로가 클러스터 전체에 완전 분산
  - Envoy같은 proxy injection 제공, 추후 sidecar proxy 형태 제공예정
- CNI, CMM plugins
  - Kubernetes, Mesos, Docker에 쉽게 통합가능
- Packet, API 네트워크 보안
  - 패킷기반 네트워크 보안과 API 인증을 결합하여 전통적인 패킷기반 네트워크 보안과 마이크로서비스 아키텍처 모두에게 보안 제공가능
  - ID기반: Source IP에만 의존하지 않고 모든패킷에 workload identity를 encoding하여 식별성 강화
  - IP/CIDR기반이외에도 Kubernetes Service기반으로 정책 설정가능
  - L7기반 API보안 적용가능
- 분산,확장가능한 Load Balacing BPF를 사용한 고성능 L3,L4 Load Balancer 제공 (Hasing, Weighted round-robin)
  - kube-proxy 대체: Kubernetes ClusterIP가 생성될때 BPF기반으로 자동으로 적용됨
  - API driven: 직접 API를 활용하여 확장가능
- 단순화된 네트워크 모델
  - Overlay/VXLAN, Direct/Native Routing 지원
- 가시성
  - Microscope: 클러스터 레벨에서 모든 이벤트 필터링 가능
  - API기반 가시성 제공


---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-12"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# VMware vSphere 6 NSX 개요

VMware NSX&reg;는 네트워크에 대한 가상 머신의 운영 모델을 제공하는 소프트웨어 네트워킹 및 보안 가상화 플랫폼입니다. 가상 네트워크는 소프트웨어에서 Layer2 - Layer7 네트워크 모델을 재현하며 추가적인 {{site.data.keyword.BluSoftlayer_notm}} 사설 네트워크 없이도 복잡한 멀티티어 네트워크 토폴로지를 프로그래밍 방식으로 몇 초 안에 작성하고 프로비저닝할 수 있습니다. 또한 NSX는 네트워크 보안에 대한 새 모델을 제공합니다. 보안 프로파일은 가상 포트로 분배되고 가상 포트에 의해 적용되며 가상 머신과 함께 이동합니다. 

NSX는 VMware의 소프트웨어 정의 데이터 센터 전략을 지원합니다. 모든 데이터 센터 리소스와 서비스에서 추출, 풀링 및 자동화의 가상화 기능을 확장하면 소프트웨어 정의 데이터 센터 아키텍처에서는 정책 기반 자동화를 통해 컴퓨팅, 스토리지 및 네트워킹 리소스의 관리 및 프로비저닝을 간소화하고 가속화할 수 있습니다. 네트워크를 가상화함으로써 NSX는 현재의 실제 네트워크 장벽을 해결하고 VMware와 {{site.data.keyword.BluSoftlayer_notm}}를 적은 비용으로 가속화할 수 있는 네트워크의 새로운 운영 모델을 제공합니다. 

NSX에는 논리 네트워킹 서비스(논리 스위치, 논리 라우터, 논리 방화벽, 논리 로드 밸런서, 논리 VPN 및 분산 보안)의 라이브러리가 포함되어 있습니다. 수정 없이 기존 애플리케이션을 지원하는 격리된 소프트웨어 기반 가상 네트워크에서 이러한 소프트웨어의 조합을 사용자 정의하거나 새 애플리케이션 워크로드에 대한 고유 요구사항을 제공할 수 있습니다. 가상 네트워크는 {{site.data.keyword.BluSoftlayer_notm}} 네트워킹 구성 요소와는 별개로 프로그래밍 방식으로 프로비저닝되고 관리됩니다. 하드웨어의 이러한 디커플링은 데이터 센터 오퍼레이션을 혁신할 수 있는 운영 효율성, 민첩성 및 가속화의 시작이 됩니다. NSX의 혜택에는 다음 기능이 포함되어 있습니다. 
* 데이터 센터 자동화
* 셀프 서비스 네트워킹 서비스
* 자동화된 네트워크 및 서비스 프로비저닝을 사용하여 신속한 애플리케이션 배치
* 동일한 베어메탈 인프라에서 개발, 테스트 및 프로덕션 환경 격리
* 단일 계정 다중 테넌트 클라우드

vSphere 웹 클라이언트, 명령행 인터페이스(CLI) 및 REST API를 통해 NSX를 구성할 수 있습니다. NSX에서 제공하는 코어 네트워크 서비스는 다음과 같습니다. 

## 논리 스위치
클라우드 배치 또는 가상 데이터 센터에는 여러 테넌트 사이에서 다양한 애플리케이션이 있을 수 있습니다. 이러한 애플리케이션과 테넌트는 IP 주소 지정이 중복되는 문제를 방지하고 보안, 결함 분리를 위해 서로 격리되어야 합니다. NSX 논리 스위치는 애플리케이션 또는 테넌트 가상 머신을 논리적으로 연결할 수 있는 논리 브로드캐스트 도메인 또는 세그먼트(VXLAN vWires)를 작성합니다. 이를 통해 물리적 계층 2 확장 없이 실제 네트워크의 브로드캐스트 도메인(VLAN)의 모든 특성을 계속 제공하면서 배치 유연성 및 속도를 높일 수 있습니다. 논리 스위치는 단일 {{site.data.keyword.BluSoftlayer_notm}} 사설 네트워크(VLAN)에 프로비저닝될 수천 개의 테넌트 네트워크를 고려합니다. 논리 스위치가 배포되며 동일한 데이터 센터 내의 Pod에서도 임의 대규모 컴퓨팅 클러스터를 포함할 수 있습니다. 이는 Pod 사이에서 물리적 계층 2(VLAN) 경계의 제한 없이 데이터 센터 내에서 가상 머신의 이동성을 고려합니다. 

## 논리 라우터
동적 라우팅은 계층 2 브로드캐스트 도메인(VXLAN vWires/논리 스위치) 간에 필요한 전달 정보를 제공하며 그렇게 함으로써 계층 2 브로드캐스트 도메인을 줄이고 네트워크 효율성과 스케일을 향상시킬 수 있습니다. NSX는 동서 간의 라우팅 기능을 제공하기 위해 워크로드가 있는 위치로 이 인텔리전스를 확장합니다. 이를 통해 홉을 확장하는 데 비용과 시간을 소비하지 않고 더 직접적으로 가상 머신 간 통신을 수행할 수 있습니다. 동시에 NSX는 또한 {{site.data.keyword.BluSoftlayer_notm}} 데이터 센터의 남북 연결 인바운드/아웃바운드를 제공함으로써 테넌트에서 안전하고 효율적으로 공용 네트워크에 액세스할 수 있습니다. 

## 논리 방화벽
논리 방화벽은 동적 가상 데이터 센터를 위한 보안 메커니즘을 제공합니다. NSX Logical Firewall의 Distributed Firewall 구성요소를 통해 VM 이름 및 속성, 사용자 ID, 데이터 센터 및 호스트와 같은 vCenter 목표, IP 주소와 같은 일반적인 네트워킹 속성과 VLAN 등을 기반으로 가상 머신과 같은 데이터 센터 엔티티를 세그먼트화할 수 있습니다. Edge Firewall 구성요소는 IP/VLAN 구성요소, 다중 테넌트 가상 데이터 센터에서 테넌트 간 격리, NAT(Network Address Translation), VPN 및 사용자 기반 SSL VPN을 기반으로 DMZ 구축과 같은 주요 외부 보안 요구를 실현하는 데 도움을 줍니다. 외부 보호를 위해 {{site.data.keyword.BluSoftlayer_notm}}의 Vyatta & Fortinet 서비스 대신에 또는 함께 결합하여 Edge 방화벽을 활용할 수 있습니다. 방화벽 Flow Monitoring 기능은 애플리케이션 프로토콜 레벨에서 가상 머신 간의 네트워크 활동을 표시합니다. 이 정보를 사용하여 네트워크 트래픽을 감사하고, 방화벽 정책을 정의 및 세분화하며 사용자 네트워크에 대한 위협을 식별할 수 있습니다. 

## 논리 가상 사설망(VPN)
SSL VPN-Plus를 통해 원격 사용자들이 사설 기업 애플리케이션에 액세스할 수 있습니다. IPSec VPN은 NSX Edge 인스턴스와 원격 사이트 간의 사이트 간 연결을 제공합니다(VMware는 {{site.data.keyword.BluSoftlayer_notm}}에서 실행 중임). L2 VPN을 통해 사용자는 지역적 경계 및 {{site.data.keyword.BluSoftlayer_notm}} 데이터 센터와 로컬 VMware 환경에서 네트워크 연결을 유지하도록 가상 머신을 허용하여 데이터 센터를 확장할 수 있습니다. 

## 논리 로드 밸랜서
NSX Edge 로드 밸런서는 특정 대상으로의 여러 경로를 따르도록 네트워크 트래픽을 사용으로 설정합니다. 로드 분산이 수신 서비스 요청을 사용자에 대해 투명한 방식으로 여러 서버 간에 고르게 분배합니다. 따라서 로드 밸런싱은 최적으로 리소스를 활용하고, 처리량을 극대화하고, 응답 시간을 최소화하며 과부하를 방지하는 데 도움을 줍니다. NSX Edge는 최대 계층 7까지 로드 밸런싱을 제공합니다.

## 서비스 작성기
서비스 작성기는 가상 인프라의 애플리케이션에 네트워크 및 보안 서비스를 프로비저닝 및 지정하는 데 도움을 줍니다. 보안 그룹에 있는 가상 머신에 이러한 서비스를 맵핑하고 적용할 수 있습니다. Data Security는 {{site.data.keyword.BluSoftlayer_notm}}를 포함하여 조직의 가상화된 클라우드 환경에 저장된 민감한 데이터에 대한 가시성을 제공합니다. NSX Data Security에서 보고한 위반사항을 기반으로 민감한 데이터가 적절하게 보호되고 있는지 확인하고 전 세계 규제를 준수하는지 평가할 수 있습니다. 

## NSX 확장성
VMware 파트너는 고유 네트워크 서비스 솔루션을 NSX 플랫폼과 통합할 수 있으며 고객들은 VMware 제품과 파트너 솔루션을 전체적으로 경험할 수 있습니다. 데이터 센터 운영자는 {{site.data.keyword.BluSoftlayer_notm}}의 기본 네트워크 토폴로지 또는 컴포넌트와 관계없이 몇 초 안에 복잡한 멀티티어 가상 네트워크를 프로비저닝할 수 있습니다. 

## NSX 코어 컴포넌트
이 섹션에서는 {{site.data.keyword.BluSoftlayer_notm}}에 배치되는 코어 NSX 컴포넌트에 대해 설명합니다. vSphere 웹 클라이언트, 명령행 인터페이스(CLI) 및 REST API를 통해 이러한 컴포넌트를 구성/관리할 수 있습니다. VMware NSX에는 최소 vSphere & vCenter 버전 6이 배치된 기능적 {{site.data.keyword.BluSoftlayer_notm}} 환경이 필요합니다. 이 섹션에서 설명되는 모든 컴포넌트는 {{site.data.keyword.BluSoftlayer_notm}}에서 실행 중인 VMware 어플라이언스 VM으로 배치됩니다. NSX 컴포넌트는 VSI(Virtual Server Instance)로 지원되지 않습니다. 안내에 따라 전용 ESX 관리 클러스터를 작성하는 것을 권장하며 이 문서에서 이후에 논의될 Edge Services 클러스터가 필요할 수도 있습니다. 

<!-- ![Figure 1](images/vmware6_nsx_overview_1.png)-->

## NSX Manager
NSX Manager는 NSX의 중앙 집중식 네트워크 관리 컴포넌트이며 vCenter Server 환경의 ESX 호스트에 가상 어플라이언스로 설치됩니다. {{site.data.keyword.BluSoftlayer_notm}} 아키텍처는 이 VM을 전용 관리 ESX 클러스터에 배치하도록 권장합니다. 하나의 NSX Manager는 단일 vCenter Server 및 여러 NSX Edge, vShield Endpoint 및 NSX Data Security 인스턴스에 맵핑됩니다. 

## NSX vSwitch
NSX vSwitch는 서버와 실제 네트워크 간에 소프트웨어 추상화 계층을 구성하기 위해 {{site.data.keyword.BluSoftlayer_notm}} ESX 호스트에서 운영되는 소프트웨어입니다. 데이터 센터의 요구가 계속 증가하고 가속화되면서 데이터 자체에 대한 액세스 및 속도와 관련된 요구사항도 계속 증가하고 있습니다. 대부분의 인프라에서 가상 머신 액세스 및 이동성은 일반적으로 머신이 있는 실제 네트워킹 인프라 및 실제 네트워킹 환경에 따라 달라집니다. 이는 특정 Pod에서 특정 {{site.data.keyword.BluSoftlayer_notm}} 사설 네트워크(VLAN)에 의존하는 것처럼 잠재적인 계층 2 또는 계층 3 경계로 인해 이상적이지 않은 환경으로 가상 워크로드를 강요할 수 있습니다. NSX vSwitch를 통해 실제 기본 네트워크 인프라에 상관없이 데이터 센터의 사용 가능한 인프라에 이러한 가상 워크로드를 배치할 수 있습니다. 이는 유연성과 이동성을 높일 뿐만 아니라 가용성과 복원성도 높여줍니다. 

## NSX Controller 
NSX Controller는 가상 네트워크 및 VXLAN 오버레이 전송 터널을 제어하는 고급 분산 상태 관리 시스템입니다. NSX Controller는 네트워크 내의 모든 논리 스위치에 대한 중앙 제어 지점이며 모든 가상 머신, 호스트, 논리 스위치 및 VXLAN의 정보를 유지보수합니다. 제어기는 멀티캐스트, 유니캐스트 및 하이브리드의 세 가지 논리 스위치 제어 플레인 모드를 지원합니다. 이러한 모드는 실제 네트워크에서 NSX를 분리합니다. {{site.data.keyword.BluSoftlayer_notm}}는 {{site.data.keyword.BluSoftlayer_notm}} 사설 네트워크(VLAN)에서 멀티캐스트 또는 하이브리드 모드에 대한 IGMP 서비스를 제공하지 않는 경우 유니캐스트 모드가 필요합니다. NSX Controller는 VXLAN 브로드캐스트, 알 수 없는 유니캐스트 및 멀티캐스트 (BUM) 트래픽을 논리 스위치에서 허용하도록 mac 학습 및 다른 기능을 제공하기 위해 가상 터널 엔드포인트(VTEPS)와 함께 유니캐스트 모드를 이용합니다. 유니캐스트 모드는 모든 BUM 트래픽을 호스트에 로컬로 복제하며 VTEPS 간에 계층 3 연결 외부의 실제 네트워크 구성은 필요하지 않습니다. NSX Controller는 (분산된) 계층 3 라우팅 서비스를 지원하기 위해 다양한 기타 노드뿐만 아니라 최소 3개 제어기 노드 세트로 NSX Manager에 의해 배치됩니다. 모든 노드는 가상 머신으로 배치되고 {{site.data.keyword.BluSoftlayer_notm}}에서 ESX 관리 클러스터의 NSX Manager에 의해 관리됩니다. 

## NSX Edge
NSX Edge는 가상화된 네트워크를 격리하기 위해 네트워크 에지 보안 및 게이트웨이 서비스를 제공합니다. NSX Edge를 논리 (분산) 라우터 또는 서비스 게이트웨이 중 하나로 설치할 수 있습니다. NSX Edge 논리 (분산) 라우터는 테넌트 IP 주소 영역 및 데이터 경로 격리로 동서 분산 라우팅을 제공합니다. 다른 서브넷의 동일한 호스트에 있는 가상 머신 또는 워크로드는 일반 라우팅 인터페이스를 순회하지 않고 서로 통신할 수 있습니다. NSX Edge Gateway는 DHCP, VPN, NAT, 동적 라우팅 및 로드 밸런싱과 같은 일반 게이트웨이 서비스를 제공하여 격리된 스텁 네트워크를 공유 (업링크) 네트워크에 연결합니다. NSX Edge의 공통 배치는 NSX Edge가 각 테넌트에 대한 가상 경계를 작성하는 DMZ, VPN Extranets 및 다중 테넌트 환경에 포함됩니다. 
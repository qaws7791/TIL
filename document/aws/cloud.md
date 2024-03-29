# Cloud

## 온프레미스(on-premise)

on-premise: 사무실, 시설과 같은 로컬 환경에서 기기를 설치하여 운영하는 IT 인프라스트럭처

"클라우드 컴퓨팅", "외부 데이터 센터"와 대조적

😀장점: 자유로운 기기 구성 및 이용, 낮은 운용 비용

😔단점: 높은 초기 투자 비용, 긴 설치 시간, 예상치 못한 기기 고장 시 추가 비용



### 클라우드(cloud)

cloud computing: 클라우드 서비스 제공자가 기기를 준비하고 사용자는 해당 기기를 원격으로 사용하고  이용료를 지불

😀장점: 서비스 제공자가 하드웨어를 관리하여 사용자는 이를 신경쓰지 않아도 됨. 컴퓨터 자원을 안정적으로 사용

😔단점: 서비스 제공자가 제공하는 서비스만 사용할 수 있어 시스템 구성이 제한적. 지속적인 클라우드 사용 비용 발생



### 가상화(virtualization)

클라우드 서비스에서 사용자는 원하는 사양의 서버를 임대하여 사용한다. 서비스 제공자는 가상화 기술을 통해 사용자가 원하는 서버를 생성하여 제공한다. 이렇게 제공되는 서버는 가상화 기술을 물리적 서버에서 컴퓨터 자원을 일부 독점적으로 사용하여 마치 독립된 서버처럼 동작하게 된다. 가상화는 cpu, memory부터 스토리지, 네트워크 등 다양한 물리적 하드웨어에 적용될 수 있다



### 서버리스(serverless)

"서버가 없는"이라는 뜻의 서버리스는 항상 서버를 가동하는 기존의 서비스방식과 달리 사용자가 필요로 할 때만 서버를 가동하는 방식이다. 일반적으로 가동 시간을 기준으로 가격을 매기는 클라우드 서비스 특성 상 서버 가동 시간을 줄일 수 있어 비용을 효율적으로 관리할 수 있다





### 클라우드의 유형

#### 개방형 클라우드(Public Cloud)

누구나 제약 없이 접근하여 사용할 수 있는 클라우드 환경

* 아마존 - AWS
* 구글 - GCP
* 마이크로소프트 - Azure
* 네이버 - NCloud



#### 폐쇄형 클라우드(Private Cloud)

접근이 허용된 사용자만 사용할 수 있는 클라우드 환경.

일반적으로 특정 기업 혹은 조직 안에서 사용하기 때문에 온프레미스와 비슷하다

많은 개방형 클라우드에서 폐쇄형 클라우드 서비스도 함께제공하고 있다

* 정부 - G Cloud



#### **하이브리드 클라우드 (Hybrid Cloud)**

공용 클라우드와 사설 클라우드를 연결하여 사용.  보안이 필요한 데이터는 폐쇄형 클라우드에서 관리하고, 덜 민감한 데이터는 개방형 클라우드에 저장하여 데이터를 효율적으로 관리하고 보안성을 높일 수 있다



#### **멀티 클라우드 (Multi-Cloud)**

여러 공용 클라우드 제공자나 사설 클라우드를 동시에 사용

클라우드 서비스 제공자(vender)의 의존(lock-in)을 최소화하고, 특정 클라우드 제공자의 장애에 대비할 수 있습니다. 여러 제공자들의 서비스 중 원하는 서비스들을 선택하여 자유도 높은시스템을 구축할 수 있다



### 클라우드 서비스 분류



#### IaaS

(서버 + 스토리지 + 네트워크 등)

사용자가 플랫폼을 직접 구축하여 사용 할 수 있도록 컴퓨팅 영역(네트워크, 컴퓨터, 스토리지  등) 제공

#### PaaS

(IaaS + 미들웨어 + 운영체제 등)

클라우드 서비스 제공자가 인프라부터 플랫폼까지 관리하고, 사용자는 기반 인프라를 관리할 필요 없이 애플리케이션을 개발

#### SaaS

(PaaS + 애플리케이션 + 데이터 등)

서비스 제공자에 의해 제공되는 완전한 제품을 고객에게 제공


# OSI 7 계층

OSI 7계층은 참조형 모델이고 실제로 사용하는 프로토콜은 TCP/IP 프로토콜 스택으로 구현되어 있다.

![OSI 7](images/osi7.png)

### 1계층 (피지컬 계층)

전기 신호를 전달하는 데 초점이있다. 주요 장비로는 허브, 리피터, 케이블, 커넥터, 트랜시버, 탭이 있다. 1계층에서는 들어온 전기 신호를 잘 전달하는 것이 목적이므로 전기 신호가 1계층 장비에 들어오면 이 전기 신호를 재생성하여 내보낸다.

- 허브, 리피터: 네트워크 통신을 중재하는 네트워크 장비
- 케이벌, 커넥터: 케이블
- 트랜시버: 컴퓨터의 랜 카드와 케이블을 연결하는 장치
- 탭: 네트워크 모니터링과 패킷 분석을 위해 전기 신호를 다른 장비로 복제

### 2계층 (데이터 링크 계층)

전기 신호를 모아 알아볼 수 있는 데이터 형태로 처리한다. 주소 정보를 정의하고 정확한 주소로 통신이 되도록 하는 데 초점이 있다. 1계층에서는 전기 신호를 잘 보내는 것이 목적이므로 출발지와 목적지를 구분할 수 없지만 2계층에서는 출발지와 도착지 주소를 확인한 후 데이터 처리를 수행한다.

2계층에서는 주소 체계가 생기면서 여러 통신이 한꺼번에 이루어지는 것을 구분하기 위한 기능이 주로 정의된다. 이더넷 기반 네트워크의 2계층에서는 에러를 탐지하는 역할을 수행한다. 주소 체계가 생긴다는 의미는 한 명과 통신하는 것이 아니라 동시에 여러 명과 통신할 수 있다는 것이므로 무작정 데이터를 던지는 것이 아니라 받는 사람이 현재 데이터를 받을 수 있는지 확인하는 작업을 먼저 해야한다. 이를 “플로 컨트롤(Flow control)” 이라고 한다.
2계층에서 동작하는 네트워크 구성 요소는 네트워크 인터페이스 카드와 스위치이다. 2계층의 주요한 특징은 MAC 주소가 있다는 것이다.
- 전기 신호를 데이터 형태로 만든다
- 목적지 MAC 주소와 출발지 MAC 주소를 확인한다
- 네트워크 인터페이스 카드와 MAC 주소를 확인
- 목적지 MAC 주소와 네트워크 인터페이스 카드가 갖고 있는 MAC 주소가 맞으면 데이터 처리, 다르면 폐기

스위치는 단말이 어떤 MAC 주소인지, 연결된 포트는 어느 것인지 주소 습득 과정에서 알 수 있다. 이 데이터를 기반으로 단말들이 통신할 때 포트를 필터링하고 정확한 포트로 포워딩해준다.

### 3계층 (네트워크 계층)

3계층에서는 IP 주소와 같은 논리적인 주소가 정의된다. 데이터 통신을 할 때는 MAC 주소와 IP 주소를 사용한다. IP 주소는 사용자 환경에 맞게 변경해 사용할 수 있고 네트워크 주소 부분과 호스트 주소 부분으로 나뉜다. 3계층에서 동작하는 장비는 라우터이다.  라우터는 IP 주소를 사용해 최적의 경로를 찾아주고 해당 경로로 패킷을 전송하는 역할을 한다.

### 4계층 (트랜스포트 계층)

4계층은 실제로 데이터들이 정상적으로 잘 보내지도록 확인하는 역할을 한다. 패킷 네트워크는 데이터를 분할해 패킷에 실어 전송하다보니 중간에 패킷이 유실되거나 순서가 바뀌는 경우가 생길 수 있다. 이를 해결하는 역할을 4계층에서 담당한다. 패킷에 보내는 순서를 명시한 것이 시퀀스 번호, 받는 순서를 나타낸 것이 ACK 번호이다. 장치 내의 많은 애플리케이션을 구분할 수 있도록 포트 번호를 사용해 상위 애플리케이션을 구분한다.

4계층에서 동작하는 장비는 로드 밸런서와 방화벽이 있다. 이 장비들은 포트 번호와 시퀀스, ACK 번호 정보를 이용해 부하를 분산하거나 보안 정책을 수행한다.

### 5계층(세션 계층)

세션 계층은 양 끝단의 응용 프로세스의 연결을 성립하도록 도와주고 연결이 안정적으로 유지되도록 관리하고 작업 완료 후에는 연결을 끊는 역할을 한다. TCP/IP 세션을 만들고 없애는 책임을 지고 에러로 중단된 통신에 대한 복구와 재전송을 수행한다.

### 6계층 (프레젠테이션 계층)

표현 방식이 다른 애플리케이션이나 시스템 간의 통신을 돕기 위해 하나의 통일된 구문 형식으로 변환시키는 기능을 수행한다. MIME 인코딩이나 암호화, 압축, 코드 변환과 같은 동작이 이루어진다.

7계층 (애플리케이션 계층)

애플리케이션 프로세스를 정의하고 서비스를 수행한다. 네트워크 소프트웨어의 UI 부분이나 사용자 입,출력 부분을 정의한다.

---

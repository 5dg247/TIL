# IP(internet protocol)
* protocol의 사전적 의미는 통신 규약.
* 데이터를 보내는 쪽과 받는 쪽에서 ip 주소를 부여 받는 것에서 시작한다.
* 지정한 ip address에 데이터 전달. 패킷(Packet) 통신 단위로 데이터 전달.
* 출발지ip, 도착ip, 기타 등등의 값들을 담은 것을 ip패킷이라 한다.
* 인터넷망에 패킷을 던지면 인터넷이 인터넷 규악을 따르고 있기 때문에 패킷이 담고 있는 주소로 이동한다.
* 출발지ip에서 인터넷 중간 중간에 존재하는 노드(node)를 타고 타고 도착ip에 도착한다.
* 도착ip에서 다시 메세지를 보내는 것 또한 같은 방식으로 각각의 주소가 적힌 패킷을 인터넷에 던지면 노드를 타고 도착ip에 도착한다.
## IP 프로토콜의 한계
* 비연결성
    * 패킷을 받을 대상이 연결 상태가 아니어도 패킷 전송 받는 대상 서버가 받는 상태인지 아닌지 확인이 불가능 하다.
* 비신뢰성
    * 중간에 노드를 커져가는 도중에 서버가 꺼져있는 상황이라면 패킷은 소실된다.
    * 패킷을 '안녕', '밥 먹었니?' 로 보냈어도, 도착ip에서는 순서대로 오지 않는다. 패킷을 보낸다고 해서 언제나 같은 노드를 타고 패킷이 서버를 타고 이동하지 않기 때문이다.
* 프로그램 구분
    * 같은 ip를 사용하는 서버에서 애플리케이션이 둘 이상이면 구분을 어떻게 하는 것인가?




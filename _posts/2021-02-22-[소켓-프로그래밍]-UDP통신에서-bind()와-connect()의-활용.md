---
layout: single
title: UDP 통신에서 bind(), connect()
categories:
  - socket
tags:
  - socket
  - UDP socket
---

### bind() 
- 소켓통신에서 bind 한다는 것의 의미는 소켓에 ip address와 port를 연결시키겠다는 의미이다
- 즉, 외부에서 패킷이 들어왔을 때 이 패킷을 어디로 보낼지 정하는 것

### connect()
- TCP 통신에서 connect()는 2가지 일을 한다 (IP,PORT 할당 / 연결 요청)
- UDP 통신에서 connect()는 오직 IP와 임의의 PORT를 할당하는 일만 진행한다

UDP 소켓통신 테스트 중 bind() 함수를
1) receiver 에서 사용한 경우 sendto, recvfrom 모두 성공
2) sender 에서 사용한 경우 sendto 성공, recvfrom 실패
3) sender, receiver 둘 다에서 사용한 경우 모두 성공
이러한 결과가 나왔다.

TCP 소켓 통신에서는 일반적으로 클라이언트가 아닌 서버에서 bind()를 하는데
그 이유는 TCP 통신은 클라이언트가 서버의 주소에 접속하는 것이기 때문에 필요한 정보는 서버의 주소/포트 이고 클라이언트의 주소는 알 필요가 없는 것이다.

하지만 서버-클라이언트의 개념이 아니라 수신-송신의 개념으로 접근해야하는 UDP 통신에서는
송신측에서 bind를 해주어야 OS가 받은 데이터를 어디로 보낼 지 알 수 있는 것이다.
connection() 도 마찬가지로 receiver가 아닌 sender에 넣어주니 전송이 되었다.

### 패킷(데이터)이 어플리케이션(수신기)에 전달되는 프로세스
1. 랜카드를 통해 패킷 수신
2. 랜카드 드라이버가 OS에 패킷 전달
3. OS는 소켓 리스트에서 패킷의 목적지 address와 port번호와 일치하게 bind 되어있는 소켓을 찾음
4. 찾은 경우 해당 어플리케이션에 전달
5. 어플리케이션은 recvfrom을 통해 읽음
  
UDP 소켓은 명시적, 암시적 두 가지 방법에 의해 Local IP, Port binding을 수행할 수 있다. 
UDP 소켓이 로컬 ip, port 와 바인딩 되어있지 않다면 recvfrom()을 사용할 수 없다.

*결론 : UDP 통신에서는 bind(), connection()을 송신측에서 사용해야 한다.*

+추가)
connection() 함수를 sender에 붙인 후 send/recv 함수가 정상적으로 작동헀다.
이것은 UDP 통신에서도 sendto/recvfrom 이 아닌 TCP용 함수를 사용할 수 있다는 의미가 되었지만
서버가 어떻게 구현될지 확신할 수 없는 상황이니 안전하게 UDP 통신용인 recvfrom함수를 사용하기로 했다.

참고 : 
[https://nenunena.tistory.com/61][https://nenunena.tistory.com/61]
[https://min-310.tistory.com/79][https://min-310.tistory.com/79]
[https://mintnlatte.tistory.com/308][https://mintnlatte.tistory.com/308]

[https://nenunena.tistory.com/61]: https://nenunena.tistory.com/61
[https://min-310.tistory.com/79]: https://min-310.tistory.com/79
[https://mintnlatte.tistory.com/308]: https://mintnlatte.tistory.com/308



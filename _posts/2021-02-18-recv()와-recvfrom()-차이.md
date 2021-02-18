recv()

recv() 함수는 TCP 통신에서 소켓으로부터 데이터를 수신한다.
{% highlist ruby %}
int recv(int s, void \*buf, size_t len, int flags);
{% endhighlight %}

recvfrom()

recvfrom() 함수는 UDP/IP 통신에서 소켓으로부터 데이터를 수신한다.
{% highlist ruby %}
int recvfrom(int s, void \*buf, size_t len, int flags, struct sockaddr \*from, socklen_t \*fromlen);
{% endhighlight %}

recv()와 recvfrom()의 차이점은 address를 지정할 수 있는지 없는지이다.

이미 connect()를 통해 연결이 된 상태에서 데이터를 수신하는 TCP 프로토콜의 경우, 데이터 수신 시 address를 또 지정해 줄 필요가 없으므로 대부분 recv()를 사용한다. 
recvfrom()은 연결지향형이 아닌 UDP통신에서 주소지가 다른 데이터를 수신하는 것을 막기 위해 많이 사용한다.

참고 : [https://min-310.tistory.com/79][https://min-310.tistory.com/79]

[https://min-310.tistory.com/79]: https://min-310.tistory.com/79

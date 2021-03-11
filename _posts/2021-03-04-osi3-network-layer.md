---
layout: single
title: OSI모델 3계층(네트워크계층-스트림, 메세지 형식)
categories:
  - network
tags: 
  - OSI 7 layers
  - network
---

### 스트림 형식(TCP)
- 스트림(stream)이란 한쪽에서 다른 한쪽으로 연결된 데이터의 흐름 하나를 일컫는다.
- 네트워크에서 스트림 형식의 특징은 보낸 개수와 받는 개수가 다를 수 있다는 것이다. 또한 보낸 데이터의 시작과 받은 데이터의 시작이 다를 수도 있다.

{% highlight ruby %}
send(aaa)	receive()	=> aa
send(bbb)	receive()	=> aabb
send(ccc)	receive()	=> cc
 		receive()	=> c
{% endhighlight %}

- 위와 같이 스트림 송신 횟수와 수신 횟수가 불일치할 수도 있다.
- 따라서 스트림 형식으로 데이터를 송수신할 때, 보낼 데이터의 크기를 먼저 보낸다던지 데이터의 시작이나 끝을 알리는 특정 기호를 추가해야 한다. (헤더와 구분자)
- 증권 거래 표준 프로토콜인 FIX protocol이 위와 같은 스트림 형식으로 구성되어 있다.


### 메시지 형식(UDP)
- 스트림과 달리 자체적으로 데이터 시작과 끝을 구별한다.
- aaa, bbb, ccc를 보내면 aaa, bbb, ccc를 받는다.
- 보낸 개수와 받은 개수가 같으면, 보낸 데이터와 받는 데이터의 시작과 끝은 같다.


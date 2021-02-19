---
layout: post
title:  "Welcome to Jekyll!"
date:   2021-02-17 13:36:37 +0900
categories: jekyll update
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/


UDP 통신의 connect() 사용

* TCP/UDP connect()함수 차이
- TCP 통신에서 connect()는 2가지 일을 한다 (IP,PORT 할당 / 연결 요청)
- UDP 통신에서 connect()는 오직 IP와 임의의 PORT를 할당하는 일만 진행한다

UDP통신에서 recvfrom() 함수가 호출되는 순간 커널과 소켓이 연결되고 데이터 전송이 끝난 후에는 다시 연결이 끊어진다.
커널과 소켓을 연결하는 과정이 전체 전송시간의 1/3을 소비하게 되고 이것은 데이터 수신속도 저하의 원인이 된다.
대용량의 데이터를 빠르게 수신해야하는 UDP 통신의 경우 recvfrom()함수는 다소 비효율적이라고 할 수 있다.

따라서 UDP소켓 클라이언트는  connect()를 사용하여 주소와 포트를 설정해두고
recv()함수를 사용하여 데이터를 수신받으면 수신속도를 높일 수 있다는 장점이 있다.

하지만 이를 실무에 적용시키기 위하여 유닛 테스트를 진행해보니, 
UDP소켓 - connect() 후 send()/recv()를 통한 데이터 송수신 시 에러가 발생하였다.

connect() 후 send()/recv() => send 에러
connect() 후 



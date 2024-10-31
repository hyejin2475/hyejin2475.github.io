---
layout: single
title: Next.js 13버전 이상의 디렉토리 구조
categories:
  - web
tags:
  - next.js
---


테스트용 로그인 페이지를 빌드하다가 오류가 발생하여 확인해보니
router.push('/') 에 의해 리다이렉트 된 파일의 경로가 꼬여 발생한 것이었다.

기존에 내가 구성했던 디렉토리 구조이다.
{% highlight ruby %}
my-next-app/
  ㄴ src/
    ㄴ app/
      ㄴ login.tsx
      ㄴ ...
  ㄴ pages/
    ㄴ index.tsx
    ㄴ ...
{% endhighlight %}
src/app/ 폴더와 pages/ 폴더가 분리되어 있었다.

그런데 Next.js 13부터는 새로운 'app' 디렉토리 구조를 도입하여, 기존의 'pages'디렉토리와 함께 사용할 수 있게 되었다. 
즉, pages 디렉토리의 파일을 app 디렉토리로 이동시켜야 했다.

수정 후
{% highlight ruby %}
my-next-app/
  ㄴ src/
    ㄴ app/
      ㄴ login/
        ㄴ pages.tsx    // 로그인 페이지
    ㄴ pages.tsx        // 로그인 성공 시 router.push('/')에 의해 리다이렉트되는 페이지
{% endhighlight %}

추가로, Next.js 13 이상의 app 디렉토리 구조에서는 서버 컴포넌트와 클라이언트 컴포넌트를 구분해야 한다.
'useState'와 같은 React 훅은 클라이언트 컴포넌트에서만 사용할 수 있으므로, 클라이언트 컴포넌트로 지정하려면 파일 상단에 '"use client"' 지시어를 추가해야 한다.


---
layout: post
title: "Cloud9 + jekyll (엔지니어링 블로그 만들어보기-나)"
description: ""
category: jekyll
tags: [jekyll,Cloud9]
---
{% include JB/setup %}

참, [Jekyll](http://jekyllrb.com/)(지킬)은 Ruby언어로 만들어졌다고 합니다. 참고로, 갠적으로 Ruby는 전혀
모릅니다. ^^;

### 미리 준비할 사항
* [Cloud9](https://c9.io/)에서 Ruby on rails 프로젝트를 하나 생성한다.
* 기본적으로 생성되는 폴더들은 삭제해도 무방하다. 어차피, [JekyllBootstrap](http://jekyllbootstrap.com/)을 이용하여
  블로그를 만들기 때문에...

### jekyll(지킬) 설치하기 on Cloud9

Cloud9상의 Terminal을 하나 연다. 아래 구문을 입력하면 뭔가 진행됨.

    $gem install jekyll

### jekyllBootstrap 설치하기 on Cloud9

설치 전에, [GitHub](https://github.com/)에서 새로운 repository를 하나 생성한다.
만약, [GitHub](https://github.com/)를 이용한 호스팅을 하고자 한다면 한가지 유의할 사항이 있다.
repository명(username.github.io)과 당신의 github username을 동일하게 생성한다.
참고 사이트 : [http://pages.github.com/](http://pages.github.com/)

    $ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.io
    $ cd USERNAME.github.io
    /USERNAME.github.io $ git remote set-url origin git@github.com:USERNAME/USERNAME.github.io.git
    /USERNAME.github.io $ git push origin master

조금 사이트를 준비하는데 시간이 걸린다. 기다리자.
내려받은 소스 경로로 이동 후, jekyll 서비스 시작

    $cd USERNAME.github.io
    /USERNAME.github.io $jekyll serve --host $IP --port $PORT --watch

우린 Cloud9상에서 서비스를 시작하는 것이라서, `--host $IP --port $PORT`가 필요함.

### Hello World 포스트를 생성해보자

첨에, root directory로 이송

    $cd USERNAME.github.io

새 포스트를 생성

    /USERNAME.github.io $ rake post title="Hello World"

정상적으로 동작했다면, `_posts` 디렉토리에 날짜별로 생성되는걸 확인할수 있을 것이다.
    
페이지도 생성해보자.

    /USERNAME.github.io $ rake page name="about.md"

### Publishing~~

    /USERNAME.github.io $ git add .
    /USERNAME.github.io $ git commit -m "first commit~~"
    /USERNAME.github.io $ git push origin master





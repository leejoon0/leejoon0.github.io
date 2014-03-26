---
layout: post
title: "US-ASCII errors in Jekyll"
description: ""
category: Jekyll
tags: [Jekyll, US-ASCII]
---
{% include JB/setup %}

jekyll 서버 시작시, 발생할 수 있는 오류.
나도 오늘 갑작스럽게 발생해서 한참 찾았다.
markdown으로 작성된 포스트 파일(.md)에서 잘못된 character들을 지웠다 살렸다를
반복하면서...ㅜㅜ;;

I did get a nasty error when I tried to start jekyll...
I turned out some derpy characters in some of the posts.
But finding them was a bit tricky.

### 오류 사항

아래와 같은 오류 내용이 발생할 경우...

    ...
    ... invalid byte sequence in US-ASCII
    ...

터미널 상에서, jekyll 서버 시작전에 아래 내용을 먼저 실행후 서버 시작~. 끝!

    $ export LC_CTYPE=en_US.UTF-8
    $ export LANG=en_US.UTF-8
    

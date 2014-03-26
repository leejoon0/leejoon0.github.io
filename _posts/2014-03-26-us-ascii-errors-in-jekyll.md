---
layout: post
title: "US ASCII errors in Jekyll"
description: ""
category: Jekyll
tags: [Jekyll, US-ASCII]
---
{% include JB/setup %}

jekyll 서버 시작시, 발생할 수 있는 오류.
나도 오늘 갑작스럽게 발생해서 한참 찾았다.

### 오류 사항

아래와 같은 오류 내용이 발생할 경우...

    ...
    ... invalid byte sequence in US-ASCII
    ...

터미널 상에서, jekyll 서버 시작전에 아래 내용을 먼저 실행후 서버 시작~. 끝!

    $ export LANG=en_US.UTF-8
    

---
layout: post
title: "Google Snippet"
description: ""
category: 
tags: []
---
{% include JB/setup %}

구글 사내 운영 Snippets 이메일 시스템

[http://blog.idonethis.com/post/16736314554/silicon-valleys-productivity-secret](http://blog.idonethis.com/post/16736314554/silicon-valleys-productivity-secret)


### 미리 준비할 사항
snippet 관련 git 복사하기 : [https://github.com/kushal/snippets](https://github.com/kushal/snippets)

    $ git clone git://github.com/kushal/snippets.git

Google App Engine([GAE](https://appengine.google.com/)) Application에서 앱 생성하기


### 설정값 변경(app.yaml과 emails.py)

app.yaml : `fssnippets` 이부분을 본인이 생성한 앱명으로 변경.

    handlers:
    - url: /_ah/mail/snippets@.*fssnippets\.appspotmail\.com 


emails.py : 아래 부분들의  `fssnippets`을 본인이 생성한 앱명으로 변경.
    
    ...
    snippets@fssnippets.appspotmail.com
    ...
    snippets@fssnippets.appspotmail.com
    ...
    https://fssnippets.appspot.com
    

### 작업시 발생할 수 있는 에러 및 애로사항

아래 `threadsafe` 관련 오류는, `app.yaml`에 `threadsafe:true` 추가

![](http://crossfitwod.herokuapp.com/uploads/blog02.png)


아래와 같은 오류 발생시, `index.yaml`를 삭제하면 된다.
![](http://crossfitwod.herokuapp.com/uploads/blog01.png)

### 결과물

![](http://crossfitwod.herokuapp.com/uploads/blog03.png)

![](http://crossfitwod.herokuapp.com/uploads/blog04.png)
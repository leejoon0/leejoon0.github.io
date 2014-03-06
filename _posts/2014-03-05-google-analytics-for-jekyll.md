---
layout: post
title: "google analytics for jekyll"
description: ""
category: jekyll
tags: [jekyll, google analytics]
---
{% include JB/setup %}

무쟈게 간단하면서도 막강한 기능인 듯 하네요. 이미 많은 분들이 사용하고 계시죠.
저도 몇 년전에 어느 업무 사이트에 적용한 기억이 나네요.

### 미리 준비할 사항
* 구글 계정 필수!

### Google Analytics 등록

[Google Analytics](https://www.google.com/analytics/)에서 계정 등록.

이미지 추가 예정. 그림1

이미지 추가 예정. 그림2

`Tracking ID` 확인

### Config Jekyll

`_config.yml` 파일에 해당 google analytics와 관련된 곳에 `Tracking ID` 교체

    analytics :
    provider : google 
    google : 
        tracking_id : 'UA-48711323-1'

### 결과물

이미지 추가 예정. 그림3
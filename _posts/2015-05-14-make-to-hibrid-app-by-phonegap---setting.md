---
layout: post
title: "Make to Hibrid app by PhoneGap - setting"
description: ""
category: PhoneGap
tags: [PhoneGap,HibridApp]
---
{% include JB/setup %}
__`2015-05-14 상세 내용 및 이미지 추가 예정임!`__

### 미리 준비할 사항

* jdk, sdk 설치
* node.js 설치
* PhoneGap 설치
* ios-sim 설치

### 1. 프로젝트 생성
PhoneGap 사용

    phonegap create {프로젝트이름} -n {프로젝트 디스플레이명} -i {패키지명(app identifier)}
    
예를 들면,

    phonegap create phonegap-test -n PhoneGapTest -i test.leejoon0.tutorial.phonegaptest

### 2. iOS/Android App Build & Install to PhoneGap
iOS 빌드

    phonegap build ios
    
iOS 설치

    phonegap install ios

Android 빌드

    phonegap build android
    
Android 설치

    phonegap install android

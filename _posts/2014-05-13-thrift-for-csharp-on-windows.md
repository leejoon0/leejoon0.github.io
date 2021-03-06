---
layout: post
title: "Thrift for CSharp - 1/2 (on Windows)"
description: ""
category: thrift
tags: [thrift, cygwin]
---
{% include JB/setup %}

## Prerequisite

**Binary Communication Protocol**
 [Thrift](http://thrift.apache.org/)는 인터페이스 정의 언어(interface definition language) 및 다양한 언어에 대한 서비스를 
정의하고 생성하기 위해 사용되는 이진 통신 프로토콜(binary communication protocol)이다. 

**RPC Framework**
 페이스북에서 개발된 [Thrift](http://thrift.apache.org/)는 원격 프로 시저 호출 (RPC:RemoteProcedureCall) 프레임 워크로 사용하고 
"확장 가능한 언어 간 서비스 개발(scalable cross-language services development)”이다.

**Software Stack**
 [Thrift](http://thrift.apache.org/)는 다양한 개발언어들(C#, C++ (on POSIX-compliant systems), Cappuccino, Cocoa, Delphi, 
Erlang, Go, Haskell, Java, Node.js, OCaml, Perl, PHP, Python, Ruby and Smalltalk) 사이에 
다양한 수준과 원활하게 효율적으로 작동하는 서비스를 구축하기 위한 코드 생성 엔진을 가진 
소프트웨어 스택이다.

**Apache Open Source Project**
 페이스 북에서 2007년, 4월 릴리즈 되었지만, 현재는 Apache 오픈소스프로젝트로 관리되고 있다.

**Scalable Cross-language Services**
 서버간 이종언어 통신, 다른 서버와의 통신, 서버와 연결이 필요한 모바일 등에서 사용가능하다.

위키 : [Apache_Thrift](http://en.wikipedia.org/wiki/Apache_Thrift)

### 윈도우 환경

#### [thrift 다운로드](http://thrift.apache.org/download)

    thrift-0.9.1.exe
    thrift-0.9.1.tar.gz : 압축을 풀어보면 언어별 테스트 프로젝트와 소스들이 있다. 그외것들도 많지만 
                          잘 모르는 것들이라...
    당시의 thrift 버전임.

#### [Cygwin 다운로드](http://cygwin.com/install.html) & 설치

    설치
      기본설정으로 설치가 되었다면, C:\cygwin 폴더에 정상적으로 설치가 되었을 것이다.
      사실 윈도우 상에 Cygwin 설치하는데 조금 애를 먹었다. 사용해본 적이 없다보니, 
      다들 알겠지만, 구글링을 좀 해보면 해결 가능하다.
    Cygwin Terminal에서 Thrift 사용가능하도록 설정하기.
     .. 대충 감으로 적용한 것인데, 잘 동작한다.
     .. 다운 받은 thrift-0.9.1.exe파일의 파일명 변경 : thrift.exe
     .. C:\cygwin\bin 폴더에 thrift.exe 파일을 넣는다. 끝!
     .. Cygwin Terminal을 실행후, 간단하게 thrift 라도 입력하고 엔터를 쳐보자. 정상동작하면 끝

### Thrift CSharp 파일 생성하기

관련 파라메터 정의와 인터페이스 정의에 대한 상세한 내용은 [Thrift](http://thrift.apache.org/)에서 확인바람

#### .thrift 파일 생성하기

초간단 .thrift 소스 : test.thrift

    namespace csharp TestThrift
    struct ThriftStruct
    {
    1: string Val1,
    2: required i32 x1
    }
    service ThriftService
    {
        ThriftStruct getData(1:string param1);
    }
    끝!

### How to create a CSharp Server & Client File for Thrift

`Cygwin Terminal`을 실행후,

    thrift --gen <language> <Thrift filename>
    thrift --gen csharp test.thrift

여기서 `<Thrift filename>`는 .thrift 파일의 해당 경로를 입력해줘도 된다. 기본적으로 경로를 
입력하지 않으면, Cygwin이 설치된 `C:\cygwin\home\본인윈도우계정` 폴더 하위에 있는 .thrift 
파일을 찾게 되어 있다. 이 역시 에러 상황을 만들어보면 쉽게 확인할 수 있다. 나도 마찬가지로
에러 후에 알게된 내용이다. 

위 thrift 명령을 실행한 후에,  `C:\cygwin\home\본인윈도우계정` 폴더를 확인하면 `gen-csharp` 
폴더가 생성된 걸 확인할 수 있으며, 생성된 폴더 내에 관련 .cs 파일들이 생성된 걸 확인할 수 
있다.

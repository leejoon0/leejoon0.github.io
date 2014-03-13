---
layout: post
title: "MongoLab for Python"
description: ""
category: 
tags: [Django, MongoLab, MongoDB, Python]
---
{% include JB/setup %}

### 미리 준비할 사항
* [Cloud9](https://c9.io/)에서 Django/Python프로젝트를 하나 생성한다.
* 로컬 머신에서 물론 가능하다. Windows, Unix, OSX...
* [MongoLab](https://mongolab.com)에 계정 및 데이터베이스 생성한다.


### 관련 정보
* 조합 : Cloud9 + Django + Python + MongoLab(MongoDB)
* [PyMongo](https://github.com/mongodb/mongo-python-driver) : mongo-python-driver
* 설치관련 : [PyMongo 2.7rc1](http://api.mongodb.org/python/current/installation.html)
* 언어/환경 별 샘플 : [mongodb-driver-examples](https://github.com/mongolab/mongodb-driver-examples)


### PyMongo 설치하기 on Cloud9

위 '[설치관련](http://api.mongodb.org/python/current/installation.html)'정보들 중에서, 중간쯤에 있는
`Installing from source`의 내용을 적용했다.

생성된 Cloud9의 Django/Python 프로젝트상의 Terminal을 하나 연다. 아래 구문을 입력하면 뭔가 진행됨.

    $ git clone git://github.com/mongodb/mongo-python-driver.git pymongo
    $ cd pymongo
    $ python setup.py install
    
PyMongo 설치 끝!


### 간단하게 manage.py에 MongoLab(MongoDB) 연동하기

[MongoLab](https://mongolab.com)에 생성한 데이터베이스 정보 상단에 아래와 같은 내용이 있다.

`[캡쳐 이미지 삽입 예정]`

MongoLab 연동에 필요한 정보는

    mongodb://<dbuser>:<dbpassword>@ds035438.mongolab.com:35438/fitterlifedb

위에서 `<dbuser>:<dbpassword>` 이부분은 '본인의 mongoLab 계정과 비번'을 입력하면 된다.

manage.py에 적용된 소스 정보

    ..
    import pymongo
    ..
    .. 다른 소스들
    .. 
    MONGODB_URI = 'mongodb://<dbuser>:<dbpassword>@ds035438.mongolab.com:35438/fitterlifedb'
    client = pymongo.MongoClient(MONGODB_URI)
    db = client.get_default_database()
    fitters = db['fitter-collection'] <- 본인에 생성한 collection 정보 입력!
    cursor = fitters.find()
    for fitter in cursor:
        print ('fitter : %s' % (fitter['useremail'])) <- 본인에 생성한 collection의 필드 정보 입력!
    db.drop_collection('fitters');
    client.close();
    
위와 같이하면 간단하게 연동된 결과물을 얻을 수 있다.
실제 개발시에는 별도로 위 MongoDB 정보는 다른 곳으로~ 아시죠?


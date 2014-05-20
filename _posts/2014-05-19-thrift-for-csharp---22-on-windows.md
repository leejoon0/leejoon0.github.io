---
layout: post
title: "Thrift for CSharp - 2/2 (on Windows)"
description: ""
category: thrift
tags: [thrift, cygwin]
---
{% include JB/setup %}

## Create a CSharp Server/Client Simple Project for Thrift

간단한 C/S 프로젝트를 생성하여 Thrift가 어떻게 동작하는지 눈으로 확인해보자.

우선 Thrift Server 단부터

### Thrift Server Project (Console)

#### thrift.dll 참조하기

* 다운받은 `thrift-0.9.1.tar.gz` 파일 압축해제 
* 폴더경로 : 본인압축푼경로/thrift-0.9.1/thrift-0.9.1/lib/csharp/src/bin/Debug 에 `thrift.dll` 파일 존재.
* 아니면, '검색'하면 됨.

#### ThriftStruct.cs, ThriftService.cs 파일 추가하기

* **[지난 포스트](http://leejoon0.github.io/thrift/2014/05/13/thrift-for-csharp-on-windows/)** 마지막 부분에 진행했던 내용.

#### Thrift Server 구동에 필요한 Properties 선언

    TServer tSvr = null;
    TProcessor tProc = null;
    TServerTransport tSvrTrans = null;
    
아시겠지만, 오브젝트명은 각자 맘대로~
    
#### 서비스 핸들러 정의 (중요)

클라이언트에서 요청(request)가 왔을때, 응답(response)처리해주는 코드

    public class DataThriftSvcHandler : ThriftService.Iface
    {
        public DataThriftSvcHandler()
        {
        
        }
        
        public ThriftStruct getData(string param1, string param2)
        {
            ThriftStruct result = new ThriftStruct();
            result.Bar = param1;
            result.Foo = param2;
            result.X1 = 1;
            result.Y1 = 2;
            
            return result;
        }
    }
	
#### Thrift Server 시작

    try
    {
        int port = 9898;
        tProc = new ThriftService.Processor(new DataThriftSvcHandler());
        tSvrTrans = new TServerSocket(port);
        tSvr = new TThreadPoolServer(tProc, tSvrTrans, new Thrift.Server.TServer.LogDelegate(log));
        tSvr.Serve();
    }
    catch (Exception ex)
    {
        tSvr.Stop();
        tSvr = null;
    }

위에서 웬만한건 이해가 갈테고, **'log'** 부분도 이해가 갈테지만, 간략하게 설명하면, Server 오류 발생시
에러 메시지를 알려주는 역할을 한다.

### Thrift Client Project (Console)

#### thrift.dll 참조하기

위와 동일함.

#### ThriftStruct.cs, ThriftService.cs 파일 추가하기

위와 동일함.

#### Thrift Client 구동에 필요한 Properties 선언

    TBufferedTransport transport = null;
    TSocket clientSocket = null;
    ThriftService.Client connectedService = null;
    
아시겠지만, 오브젝트명은 각자 맘대로~

#### Thrift Server 연결

    public ThriftService.Client ConnectToThriftServer(string host, int port, int clientTimeOut)
    {
        clientSocket = new TSocket(host, port, clientTimeout);
        transport = new TBufferedTransport(clientSocket);
        TBinaryProtocol protocol = new TBinaryProtocol(transport);
        try
        {
            transport.Open();
        }
        catch (Exception ex)
        {
            return null;
        }
        
        return new ThriftService.Client(protocol);
    }

'host' 정보는 로컬에서 테스트하기 때문에, 우선 'localhost' 라하고, 'port' 는 위 Server 단에서
지정한 정보와 동일하게, 'clientTimeOut' 은 대충 '10000' 정도

#### 요청(request) 보내보기

    string param1 = "aa";
    string param2 = "bb";
    
    if (connectedService == null)
    {
        MessageBox.Show(string.Format("서버 연결하세요..."));
        return;
    }
    
    ThriftStruct result = connectedService.getData(param1, param2);
    














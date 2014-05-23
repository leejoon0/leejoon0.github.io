---
layout: post
title: "Web Crawler and Web Scraping on node.js"
description: ""
category: crawler, scraping
tags: [crawler, scraping]
---
{% include JB/setup %}

## 잡설
예전 `맥북`을 사기 전에 이런저런 정보를 눈팅하던 중에 [‘재미난(Web Scraping)’ 블로그 포스트](http://blog.hibrainapps.net/151)가 있어서, 
따라해보게 되었다. 당시 운동(`Crossfit`) 관련 [개인 사이트](http://crossfitwod.herokuapp.com/)를 만들던 중에 이거다 싶은걸 
이 [개인 블로그](http://blog.hibrainapps.net)에서 알게된 이후에 이것저것 좋은 정보를 많이 보게 되었다.

뭐든지 '넘어지고', '깨져봐야'... 안다!

## Prerequisite
기본적으로 Cloud9, node.js, XOS 에 대해서 알고 있다는 가정하게 작성함.

## Web Scraping on node.js
좀더 상세한 설명과 예제는 위 '잡설'에서 언급한 [‘재미난(Web Scraping)’ 블로그 포스트](http://blog.hibrainapps.net/151)를 확인하면 된다.

용어정의(위키피디아) : [Web scraping](http://en.wikipedia.org/wiki/Web_scraping)

#### [cheerio](https://github.com/cheeriojs/cheerio) 설치

    npm install cheerio

## Web Crawler on node.js
개인적으로 좀더 깊이있게 공부를 해야함. 지금은 단순히 오픈소스를 이용하여, '이런거구나~'하고 느끼는 수준임.
필요하다면 각자가 심도있는 스터디가 필요함.

용어정의(위키피디아) : [Web crawler](http://en.wikipedia.org/wiki/Web_crawler)

#### [node-crawler](https://github.com/sylvinus/node-crawler) 설치

    npm install crawler

#### 간단한 예제

    var Crawler = require("crawler").Crawler;
    var url = 'http://misfitathletics.com/mft-348'; <-- 개인적인 운동 관련 사이트임.
    
    var c = new Crawler({
        "maxConnections":10,
    
        // This will be called for each crawled page
        "callback":function(error,result,$) {
        
            // $ is a jQuery instance scoped to the server-side DOM of the page
            //$("#content a").each(function(index,a) {
            //    c.queue(a.href);
            //});
            
            //console.log(result.body)
            
            if(result){
                var page = result.body;
                var res = page.match(/bechtel/i);
                //var res = page.match(/helton/g);
                if(res && res.length >0) {
                    //console.log(result.body);
                }
                
                $('a').each(function(index, a) {
                    var aHref = a.href;
                    console.log(aHref);
                    c.queue(aHref);
                });
            
            }
        }
    });
    
    c.queue(urlmisfit);

아래와 같은 결과가 나오게 된다.

---
`이미지 추가 예정임.....`
---

## Warp-up
간단히 몇 가지 테스트를 통해 느낀거지만, 'WebScaping'은 웹서치엔진 'WebCrawler'에 일부분이네요. ^^;


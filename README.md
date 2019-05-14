# nginx-netty-hls
一、概述

采用nginx、netty实现hls协议的回看和时移。

二、性能

对m3u8的长连接下载并发连接可达4w。ts跑满网卡，系统瓶颈在net io。

三、架构

1.nginx

    负责m3u8的组装、ts下载，对于m3u8的下载需求，采用subrequest把请求打到后端netty。

2.netty

    负责m3u8内容的生成。
    
四、编译

1.netty

    基于maven，mvn clean package。

2.nginx

    ./configure --add-module=./src/http/hls 
    
    make && make install
	
	

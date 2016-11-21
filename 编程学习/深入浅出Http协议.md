
<h2 style='text-align:center'>深入浅出Http协议</h1>

+ ## Http基础

    - ### 简述
    
        http协议（*超文本传输协议*）为了Web上的信息共享而诞生
    
        三个版本：0.9; 1.0; 1.1

    - ### 网络基础

        建立在TCP/IP协议族的基础之上

        * TCP/IP协议族

            1. 应用层：决定了向用户提供应用服务时的通信活动，如FTP，DNS和HTTP等；

            2. 传输层：提供处于网络连接中的两台计算机之间的数据传输，TCP，UDP；

            3. 网络层：用来处理网络上流动的数据包，IP协议；

            4. 链路层：网络连接的硬件部分。

            数据在各层中封装后进行传输

            ![images](images/1.PNG)

            ![images](images/2.PNG)

        * IP协议
        
            IP协议的作用是把各种数据包传送给接收方，其中IP地址和MAC地址用于确定接收方的位置。IP地址可以通过ARP协议（*Adress Resolution Protocol*） 反查出对应的MAC地址

            ![images](images/3.PNG)

        * TCP协议

            TCP协议能够将数据准确可靠地传输给接收方,(*三次握手*)。

            ![images](images/4.PNG)

        * DNS服务

            DNS服务位于应用层。它提供域名到IP地址之间的解析服务

            域名易于人类理解，IP地址易于计算机理解

            ![images](images/5.PNG)

    - ### 简单结构

        http协议用于客户端与服务端之间的通信，切为无状态协议。

        通过URI（*Uniform Resource Identifier 统一资源标志符*）定位请求资源，url是URL的一个自己

        http方法，常用 post，get

        ![images](images/6.PNG)

        一个页面一般会存在很多资源请求，如图片，脚本等资源。每一个请求都进行打开关闭TCP连接操作，增加了通信的开销，页面的加载速度也会变慢。因此，http中又有了持久连接的机制。建立一次连接后可进行多次客户端与服务端之间的交互，直到其中一方明确表示需要断开连接。

        ![images](images/7.PNG)

        ![images](images/8.PNG)

        在持久连接基础上可以实现管线化，可以同时发送多个请求。

        ![images](images/9.PNG)

        http协议的无状态特性可以减少服务器的CPU以及内存资源的消耗，却也因此无法对用户进行认证。所以就有了Cookie来管理状态，将消耗分担到了每个客户端。

+ ** HTTP信息

    - ### 报文信息

        客户端的Htpp报文叫做请求报文，服务器端的Http报文叫响应报文，报文使用CR+LF作为换行符

        报文分为报文首部和报文主体,报文首部一般有四种：通用首部，请求首部，响应首部和实体首部

        ![images](images/10.PNG)

        ![images](images/11.PNG)

    - ### 状态码

        状态码用于描述服务器端返回的请求结果状态，是正常，错误还是其他。
        
        ![images](images/12.PNG)

        1. 200（*ok*）:服务器正常处理了请求

        2. 304（*Not Modified*）:资源未发生变动，一般浏览器会使用已经缓存过的资源

        3. 401（*UNauthorized*）:第一次返回表示需要认证，第二次则是表示认证失败

        4. 403（*Forbidden*）:请求资源的访问被服务器拒绝

        5. 404（*Not Found*）:服务器上不存在请求的资源

        6. 500（*Internal Server Error*）:服务器内部错误







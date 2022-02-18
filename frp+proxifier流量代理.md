# frp+proxifier
首先我们需要下载frp工具，此工具有Windows版本和Linux版本，且分为服务端和客户端两种。需要配合proxifier一起使用。服务端为frps,客户端为frpc，fprc需要发送到内网主机上。

## 内网
`frpc.exe -f 9091 -p 9090 -t 公网服务器IP`

![image](https://user-images.githubusercontent.com/71583369/146941596-6388ac03-6305-4e91-bca0-0829b892e2b6.png)

## 公网
`frps.exe -p 9090`监听本地端口


## proxifier
在proxifier上做的配置
![image](https://user-images.githubusercontent.com/71583369/146942666-cab1475c-2daf-40e6-a7a5-bb6b80ca83f6.png)


端口配置要与内网设置的-f参数一致


![image](https://user-images.githubusercontent.com/71583369/146942714-5a386c2e-38ea-4c66-affc-dcc521ace521.png)

然后打开Google浏览器查看ip会发现IP为内网服务器的出口IP。

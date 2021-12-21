# SSF+proxifier
SSF是加密传输，分为ssf和ssfd两种，ssfd为服务端，ssf为客户端，且两者都需要携带证书才会生效
![image](https://user-images.githubusercontent.com/71583369/146945197-9c982ce0-06ae-4d5f-982c-7df1bb76eb93.png)


## 公网
`ssfd.exe -p 9090`


![image](https://user-images.githubusercontent.com/71583369/146945392-4bef7142-abfd-4714-b06c-0850186aedf0.png)


需要的文件



![image](https://user-images.githubusercontent.com/71583369/146945465-6d034af8-6893-4e4d-ab4c-93ed1d55105e.png)



## 内网
`ssf.exe -F 9091 -p 9090 公网IP`

![image](https://user-images.githubusercontent.com/71583369/146945655-21f1f36b-858c-404c-a96b-8c4f36471a23.png)


需要的文件
![image](https://user-images.githubusercontent.com/71583369/146945852-7bd96cd5-1afa-4627-96de-7c5084fd4b0d.png)


## proxifier
此配置和frp写的配置相同。

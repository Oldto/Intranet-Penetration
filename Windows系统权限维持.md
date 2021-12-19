# Windows权限维持
在拿到服务器权限后，我们需要对系统进行权限维持，隐藏我们的木马，在Windows系统中我们可以将我们的exe文件写如到计划任务中，替换已应存在的计划任务来达到隐藏的地步，从而实现权限维持。

## schtasks
Windows计划任务，添加计划任务的条件，拿到的用户需要在管理员组中才可执行。
参考链接：https://blog.csdn.net/flyingleo1981/article/details/54405821

## 思路
通过msf生成的木马，对这个木马进行进制转换，从而绕过防火墙，达到免杀的效果。

通过获取的webshell执行sql语句`select hex(load_file("路径")) into outfile "输出路径" `。需要注意的是hex编码后的首位需要加上0x，输出路径一般为启动项的路径。可通过此语句先用mysql进行hex进制转换。

### Windows用户启动项目录
C:\Users\Administrator\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

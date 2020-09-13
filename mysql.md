## mysql忘记密码怎么办？:droplet:
1、找到my.ini 文件
my.ini 文件为 MySQl 设置文件， 如果你是默认的安装地址，文件在
C:\ProgramData\MySQL\MySQL Server 5.7 下
但是ProgramData 常规状态下是隐藏的

2、设置权限认证跳过
也就是在 [mysqld] 下 加上 **skip-grant-tables**

3、重启 **mysql** 服务

4、重启后， 以**mysql -uroot -p** 登陆会发现我们可以不需要密码就可以登陆

5、重新设置密码
首先先选择 mysql 数据库  **use mysql**
然后更新 password

 **update user set authentication_string = password ( 'new-password' ) where user = 'root' ;**
 
 6、重启，以新密码登录:sun_with_face:

### 2
1：打开cmd命令符，先关闭正在运行的数据库 **net stop mysql**

2：打开mysql.exe和mysqld.exe所在的文件夹,复制路径地址

3：输入命令  **mysqld --skip-grant-tables**  回车，此时就跳过了mysql的用户验证。注意输入此命令之后命令行就无法操作了，此时可以再打开一个新的dos窗口进入到mysql的bin目录下。

直接输入**mysql**，不需要带任何登录参数直接回车就可以登陆上数据库

4：:输入**show databases;**   可以看到所有数据库说明成功登陆。其中mysql库就是保存用户名的地方，输入 **use mysql;**   选择mysql数据库。
 
5：**show tables**查看所有表，会发现有个user表，这里存放的就是用户名，密码，权限等等账户信息。 　用MySQL视图工具可以看出user表中的字段

6：:输入**select user,host,password from user;**   来查看账户信息。 

7：更改root密码，输入**update user set password=password('admin123') where user='root' and host='localhost';**

8： 关闭两个窗口，重启mysql数据库，用新密码尝试登录。    

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

 **update user set authentication_string = password ( 'new-password' ) where user = 'root' ; **
 
 6、重启，以新密码登录:sun_with_face:

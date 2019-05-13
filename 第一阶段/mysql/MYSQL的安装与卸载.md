# 数据库的安装与卸载

## 2.1 数据库的安装

1. 打开下载的mysql安装文件双击解压缩，运行“mysql-5.5.40-win32.msi”。
   ![MYSQL安装01](image\MYSQL安装01.png)
   ![MYSQL安装02](image\MYSQL安装02.png)
2. 选择安装类型，有“Typical（默认）”、“Complete（完全）”、“Custom（用户自定义）”三个选项，选择“Custom”，按“next”键继续。
   ![MYSQL安装02](image\MYSQL安装03.png)
3. 点选“Browse”，手动指定安装目录。
   ![MYSQL安装02](image\MYSQL安装04.png)
4. 填上安装目录，我的是“d:\Program Files (x86)\MySQL\MySQL Server 5.0”，按“OK”继续。
   ![MYSQL安装02](image\MYSQL安装05.png)
5. 确认一下先前的设置，如果有误，按“Back”返回重做。按“Install”开始安装。
   ![MYSQL安装02](image\MYSQL安装06.png)
   ![MYSQL安装02](image\MYSQL安装07.png)
   ![MYSQL安装02](image\MYSQL安装08.png)
   ![MYSQL安装02](image\MYSQL安装09.png)
   ![MYSQL安装02](image\MYSQL安装10.png)
6. 正在安装中，请稍候，直到出现下面的界面, 则完成MYSQL的安装
   ![MYSQL安装02](image\MYSQL安装11.png)

> 数据库安装好了还需要对数据库进行配置才能使用
> MYSQL的配置

1. 安装完成了，出现如下界面将进入mysql配置向导。
   ![MYSQL安装02](image\MYSQL安装12.png)
2. 选择配置方式，“Detailed Configuration（手动精确配置）”、“Standard Configuration（标准配置）”，我们选择“Detailed Configuration”，方便熟悉配置过程。 
   ![MYSQL安装02](image\MYSQL安装13.png)
3. 选择服务器类型，“Developer Machine（开发测试类，mysql占用很少资源）”、“Server Machine（服务器类型，mysql占用较多资源）”、“Dedicated MySQL Server Machine（专门的数据库服务器，mysql占用所有可用资源）” 
   ![MYSQL安装02](image\MYSQL安装14.png)
4. 选择mysql数据库的大致用途，“Multifunctional Database（通用多功能型，好）”、“Transactional Database Only（服务器类型，专注于事务处理，一般）”、“Non-Transactional Database Only（非事务处理型，较简单，主要做一些监控、记数用，对MyISAM数据类型的支持仅限于non-transactional），按“Next”继续。
   ![MYSQL安装02](image\MYSQL安装15.png)
   ![MYSQL安装02](image\MYSQL安装16.png)
5. 选择网站并发连接数，同时连接的数目，“Decision Support(DSS)/OLAP（20个左右）”、“Online Transaction Processing(OLTP)（500个左右）”、“Manual Setting（手动设置，自己输一个数）”。 
   ![MYSQL安装02](image\MYSQL安装17.png)
6. 是否启用TCP/IP连接，设定端口，如果不启用，就只能在自己的机器上访问mysql数据库了，在这个页面上，您还可以选择“启用标准模式”（Enable Strict Mode），这样MySQL就不会允许细小的语法错误。如果是新手，建议您取消标准模式以减少麻烦。但熟悉MySQL以后，尽量使用标准模式，因为它可以降低有害数据进入数据库的可能性。按“Next”继续
   ![MYSQL安装02](image\MYSQL安装18.png)
7. 就是对mysql默认数据库语言编码进行设置（重要），一般选UTF-8，按 “Next”继续。
   ![MYSQL安装02](image\MYSQL安装19.png)
8. 选择是否将mysql安装为windows服务，还可以指定Service Name（服务标识名称），是否将mysql的bin目录加入到Windows PATH（加入后，就可以直接使用bin下的文件，而不用指出目录名，比如连接，“mysql.exe -uusername -ppassword;”就可以了，不用指出mysql.exe的完整地址，很方便），我这里全部打上了勾，Service Name不变。按“Next”继续。
   ![MYSQL安装02](image\MYSQL安装20.png)
9. 询问是否要修改默认root用户（超级管理）的密码。“Enable root access from remote machines（是否允许root用户在其它的机器上登陆，如果要安全，就不要勾上，如果要方便，就勾上它）”。最后“Create An Anonymous Account（新建一个匿名用户，匿名用户可以连接数据库，不能操作数据，包括查询）”，一般就不用勾了，设置完毕，按“Next”继续。
   ![MYSQL安装02](image\MYSQL安装21.png)
10. 确认设置无误，按“Execute”使设置生效，即完成MYSQL的安装和配置。
    ![MYSQL安装02](image\MYSQL安装22.png)
    ![MYSQL安装02](image\MYSQL安装23.png)

> 注意：设置完毕，按“Finish”后有一个比较常见的错误，就是不能“Start service”，一般出现在以前有安装mysql的服务器上，解决的办法，先保证以前安装的mysql服务器彻底卸载掉了；不行的话，检查是否按上面一步所说，之前的密码是否有修改，照上面的操作；如果依然不行，将mysql安装目录下的data文件夹备份，然后删除，在安装完成后，将安装生成的 data文件夹删除，备份的data文件夹移回来，再重启mysql服务就可以了，这种情况下，可能需要将数据库检查一下，然后修复一次，防止数据出错。
> ![MYSQL安装02](image\MYSQL安装24.png)

解决方法：卸载MySQL,重装MySQL

## 2.2 数据库的卸载

1. 停止window的MySQL服务。
   找到“控制面板”-> “管理工具”-> “服务”，停止MySQL后台服务。
   ![MYSQL卸载01](image\MYSQL卸载01.png)
2. 卸载MySQL安装程序。找到“控制面板”-> "程序和功能"，卸载MySQL程序。
   ![MYSQL卸载01](image\MYSQL卸载02.png)
3. 删除MySQL安装目录下的所有文件。
4. 删除c盘ProgramDate目录中关于MySQL的目录。路径为：C:\ProgramData\MySQL(是隐藏文件,需要显示出来)
   ![MYSQL卸载01](image\MYSQL卸载03.png)
   ![MYSQL卸载01](image\MYSQL卸载04.png)
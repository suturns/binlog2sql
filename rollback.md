数据库授权
	 grant usage on *.* to root@localhost identified by 'mysql123456';
	grant all privileges on infotool.* to root@localhost ;
	GRANT all privileges on infotool.* to 'root'@'localhost' IDENTIFIED BY 'mysql123456' WITH GRANT OPTION;

	权限恢复
	UPDATE user SET Password = password ( 'mysql123456' ) WHERE User = 'root' ;
	GRANT ALL PRIVILEGES ON *.* TO root@localhost IDENTIFIED BY 'password' WITH GRANT OPTION;
	恢复删除语句
	python binlog2sql/binlog2sql.py --flashback -hlocalhost -P3306 -uroot -pXXXXXX -dinfotool -ttest --start-file=mysql-bin.000002 --start-position=1020 --stop-position=1307

	python binlog2sql/binlog2sql.py --flashback -h10.169.XXX.XXX -P3306 -uroot -pXXXXXX -dinfotool -tt_tools_wnt_usermessagebyidp --start-file=mysql-bin.000158 --start-position=201778829 --stop-position=210259057 -B > D://rollback.sql



CLI:
- psql
	- psql -U $username -d $database_name
	- psql -h $remote_host -U $username -d $database_name(远程主机)
	- \l 列出所有数据库
	- \c $dbname 连接数据库
	- \d 列出所有表
	- \d $tablename 查看表结构
	- \q 退出
- pgcli
	- pgcli -U $username -d database_name
	- pgcli -h 192.168.1.100 -U myuser -d mydb(远程主机)
	- \l \c 与psql同
	- \dt 列出所有表
	- \d $tablename 查看表结构
	- \timing 开关SQL运行时间显示
	- \x 切换扩展模式
	- \q 退出
IDE:
- beekeeper
- datagrip

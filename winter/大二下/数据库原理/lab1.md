manjaro安装postgresql后需要手动初始化:
sudo -u postgres initdb --locale=C.UTF-8 --encoding=UTF8 -D /var/lib/postgres/data
__postgresql__ 的配置文件放在 /var/lib/postgres/data
systemctl status postgresql.service : 看psql状态
sudo systemctl enable postgresql.service 
sudo systemctl start postgresql.service
sudo -u postgres psql postgres: Connect to database postgres as postgres(user) 
\du list all roles in psql
\q quit

```sql
create database cs307 encoding='utf8';
```
创建数据库cs307

```sql
select datname from pg_database;
```
在postgresql(pg)的所有数据库中查询并选择数据库名

```sql
create user checker with superuser password '123456';
```
创建新的超级用户checker

```sql
create table lab(
id serial primary key,
address varchar(20) not null,
time varchar(20) not null,
capacity int,
teacher varchar(20),
unique (address,time)
);
```
创建新的表lab
- 列id 
	- serial: 是一种自增的数据类型，通常用于主键字段。它的作用是，当插入新记录时，PostgreSQL 会自动为该字段生成一个唯一的整数值（通常从 1 开始）.
	- primary key: 表示id是主键, 意味着id 的值唯一且不为空
- 列address, time
	- varchar(20):表示该列的数据类型是可变长度的字符串，最大长度为 20 个字符
	- not null:表示该列的值不能为空，必须提供有效的值
- 列capacity
	- 储存int
- 列unique
	- 约束address 和time的组合不会重复

```sql
insert into lab (address, time, capacity, teacher) values ('508','2-
78',36,'yueming');
insert into lab (address, time, capacity, teacher) values ('508','2-
56',36,'yueming');
insert into lab (address, time, capacity, teacher) values ('508','3-
56',36,'yueming');
insert into lab (address, time, capacity, teacher) values ('510','4-
34',36,'yueming');
```
插入数据

```sql
update lab set address='510' where time = '3-34';
```
更新

```sql
delete from lab where time = '2-56';
```
删除

```sql
select * from lab;
```
c补全
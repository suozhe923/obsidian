#### Select
- select * from [tablename]
	- To display the full content of a table. you can use select * (all columns)
	- The select clause(子句) lists the attributes desired in the result of a query
	> 这种查询在交互式工具中常用,但你不应该在应用程序中使用
#### Restrictions
- Filtering(过滤)
	- Performed in the "where" clause
	- Conditions are usually expressed by a column name
		- … followed by a comparison __operator__ and the value to which the content of the column is compared
	- Only rows for which the condition is true will be returned
```sql
select * 
from movies 
where country = 'us';
```



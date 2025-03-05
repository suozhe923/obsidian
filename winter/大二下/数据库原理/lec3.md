- Select
	- select * from [tablename]
		- To display the full content of a table. you can use select * (all columns)
		- The select clause(子句) lists the attributes desired in the result of a query
	> 	这种查询在交互式工具中常用,但你不应该在应用程序中使用
	
- Restrictions
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

- Comparison
	- you can compare to 
		- a number
		- a string constant
		- another column (from the same table or another, we'll see queries involving several tables later)
		- the result of a function (we'll see them soon)

> string constant must be quoted between single-quotes(' ')
> 	If they aren't quoted, they wiil be interpreted as column names

- Filtering
	- Note that a filtering condition returns a subset
		- If you return all the columns from a table without duplicates(重复), it won't contain duplicates either and will be a valid "relation"

- Select without From or Where
	- An attribute(属性) can be a literal with no from clause
		`select '437'`
		- Results is a table with one column and a single row with value “437”
		- Can give the column a name using:
		`select '437' as FOO`
	- An attribute can be a literal with from clause
		`select 'A' from movies`
		- Result is a table with one column and N rows (number of tuples in the movies table), each row with value "A"
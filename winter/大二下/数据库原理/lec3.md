- __Select__
	- select * from [tablename]
		- To display the full content of a table. you can use select * (all columns)
		- The select clause(子句) lists the attributes desired in the result of a query
	> 	这种查询在交互式工具中常用,但你不应该在应用程序中使用
	
- __Restrictions__
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

- __Comparison__
	- you can compare to 
		- a number
		- a string constant
		- another column (from the same table or another)
		- the result of a function (函数的结果)

> string constant must be quoted between single-quotes(' ')
> 	If they aren't quoted, they wiil be interpreted as column names

- __Filtering__
	- Note that a filtering condition returns a subset
		- If you return all the columns from a table without duplicates(重复), it won't contain duplicates either and will be a valid "relation"

- Select without From or Where
	- An attribute(属性) can be a literal with no from clause
		`select '437'`
		- Results is a table with one column and a single row with value “437”
		- __rename__: Can give the column a name using:
		`select '437' as FOO`
		![select1](Pic/select1.png)
	- An attribute can be a literal with from clause
		`select 'A' from movies`
		- Result is a table with one column and N rows (number of tuples in the movies table), each row with value "A"
		![select2](Pic/select2.png)

- Arithmetic Expression
	- select子句可以包含算术表达式(+ ,- ,* ,/ ), 作用在constants or arributes of tuples

- Logical Connectives
	- and, or, not
		- 就像编程语言一样
		- 有不同优先级(and > or), 可以用括号(parentheses)改变运算顺序
			![Operator_precedence](Pic/Operator_precedence.png)
- The operands of the logical connectives can be expressions __involving__ the comparison operators <, <=, >, >=, =, and <>.
	- != and <> 都可以表示not equal to
- 注意data type
	- 2 < 10 is true but '2' < '10' is false
- in()
	- It can be used as the equivalent for a series of equalities with or
		`where (a = 'us' or a = 'ch'`
		`where a in ('us`, 'ch')`
- Negation
	- All comparisons can be negated with not
```sql
where not (   (country in ('us', 'gb')) and (year_released between 1940 and 1949)   )
where (country in ('us', 'gb')) and (year_released between 1940 and 1949)
```

- between Comparison Operator
	- between ... and ...
		- shorthand for: >= and <= (左闭右闭)

- like
	- For strings, you also have like which is a kind of regex (regular expression 正则表达式) for dummies.
	- like compares a string to a pattern that can contain two wildcard characters:
		- % meaning "any number of characters, including none”
		- _ meaning "one and only one character"
	
- Date
	- Date formats 可能矛盾
		DD/MM/YYYY
		MM/DD/YYYY
		YYYY/MM/DD
	- Whenever you are comparing data of slightly different types, you should use functions that "cast" data types( 每当你比较略有不同类型的数据时，都应使用“cast”数据类型的功能)
	- If you compare datetime values to a date (without any time component) the SQL engine will __not understand__ that the date part of the datetime should be equal to that date
		It will consider that the date that you have supplied is actually a datetime
		- date(‘2020-03-20’) is equal to datetime(‘2020-03-20 00:00:00’)

- NULL
	- in SQL, NULL denotes that a value is missing(而不是0)
		- not a value
		`is null` 而不是 `= null`

- Some Functions
	- Show DDL of a table
		- 假设movies is a table
			- psql: \d movies
			- mysql, oracle: desc movies
			- SQLite: .schema movies
			- IBM DB2: describe table movies
	- concatenating two strings together(将两个字符串串在一起)
		- __||__ (most db like psql)
		- +, concat() : in other products
		![cast](Pic/cast.png)
		虽然year_released 是number, 但是会被DBMS隐式转化,最好用函数显式转化
	- age(年龄一直改变,需要用function)
		```sql
 select peopleid,surname
	 data_part('year', now()) - born as age 
 from people
 where died is null;
		```
	- Numerical function
		- round(3.141592, 3) --3.142
		- trunc(3.141592, 3) --3.141
	- String
		- upper
		- lower
		- substr('Citizen Kane', 5, 3) -- 'zen'
		- trim('      a ') --'a'
		- repalce('Sheep', 'ee', 'i') --'Ship'
	- Type casting
		- cast(column as type)
```sql
select cast(born as char) || 'abc' from people;
```

- Case
	- A very useful construct is the CASE ... END construct that is similar to IF or SWITCH statements in a program
	- usage 见/Pdf/T3

- Distinct
	- No duplicated identifier(没有重复标识符)



- Aggregate Functions(聚合功能)
	- Aggregate function will
		- aggregate all rows that share a feature (such as being movies from the same country)
		- … and return a characteristic of each group of aggregated rows
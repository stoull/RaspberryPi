# SQLite 常用场景

#### 1. 重设 AUTOINCREMENT 中的序列号
```
delete from your_table;    	// 清空所有数据记录
delete from sqlite_sequence where name='your_table';
```

#### 2. 判断一个记录是否存在

方法1:
>
```
IF EXISTS (SELECT * FROM Products WHERE id = ?)
BEGIN
--do what you need if exists
END
ELSE
BEGIN
--do what needs to be done if not
END
```

方法2 SQLite 不支持 TOP:
>
```
SELECT TOP 1 products.id FROM products WHERE products.id = ?
```

方法2 
>
`SELECT distinct 1 products.id FROM products WHERE products.id = ?;`


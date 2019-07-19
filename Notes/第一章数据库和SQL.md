## postgres

用户名： postgres
密  码： postgres

tom tom shop


1. 数据库： 数据集合


## DDL

对数据库和表进行创建，删除，修改

- CREATE
- DROP
- ALTER

> 列名 数据类型  约束


## DML

### SELECT 

#### 单表操作

> SELECT 列名 <,列名> <,列名> FROM 表名

- 设置别名 
```sql
SELECT product_id AS "商品编号",
        product_name AS "商品名称",
        purchase_price AS "进货单价"
FROM Product;
```
- 常数查询
```sql
SELECT '商品' AS string, 38 AS number, '2009-02-24' AS date,
 product_id, product_name
 FROM Product;
```

- 删除重复行 **DISTINCT 关键字只能用在第一个列名之前**
```sql
SELECT DISTINCT product_type FROM product
```

------------

- where条件

> WHERE子句要紧跟在FROM子句之后。


### 算术运算符

用于在列名中进行处理

```sql
select sale_price,sale_price*2 as sale_price_x2 from product;
```



### 比较运算符

- 大于，等于，小于等
- 可以对日期进行比较
```sql
select * from product where regist_date>'2009-01-15';
```
- 注意，在使用比较运算符时对于记录为NULL，查询时处理的状态是不确定（**UNKNOWN**），即既不是真也不是假。

> 没有查询到null的行

```sql
shop=> select * from product;
 product_id | product_name | product_type | sale_price | purchase_price | regist_date
------------+--------------+--------------+------------+----------------+-------------
 0001       | T恤衫        | 衣服         |       1000 |            500 | 2009-09-20
 0002       | 打孔器       | 办公用品     |        500 |            320 | 2009-09-11
 0003       | 运动T恤      | 衣服         |       4000 |           2800 |
 0004       | 菜刀         | 厨房用具     |       3000 |           2800 | 2009-09-20
 0005       | 高压锅       | 厨房用具     |       6800 |           5000 | 2009-01-15
 0006       | 叉子         | 厨房用具     |        500 |                | 2009-09-20
 0007       | 擦菜板       | 厨房用具     |        880 |            790 | 2008-04-28
 0008       | 圆珠笔       | 办公用品     |        100 |                | 2009-11-11
(8 行记录)


shop=> select * from product where purchase_price >=700;
 product_id | product_name | product_type | sale_price | purchase_price | regist_date
------------+--------------+--------------+------------+----------------+-------------
 0003       | 运动T恤      | 衣服         |       4000 |           2800 |
 0004       | 菜刀         | 厨房用具     |       3000 |           2800 | 2009-09-20
 0005       | 高压锅       | 厨房用具     |       6800 |           5000 | 2009-01-15
 0007       | 擦菜板       | 厨房用具     |        880 |            790 | 2008-04-28
(4 行记录)


shop=> select * from product where not purchase_price >=700;
 product_id | product_name | product_type | sale_price | purchase_price | regist_date
------------+--------------+--------------+------------+----------------+-------------
 0001       | T恤衫        | 衣服         |       1000 |            500 | 2009-09-20
 0002       | 打孔器       | 办公用品     |        500 |            320 | 2009-09-11
(2 行记录)
```

### 逻辑运算符

- NOT(NOT 不能单独使用，必须和其他查询条件组合起来使用)： **真假转换**
```sql
SELECT product_name, product_type, sale_price
 FROM Product
 WHERE NOT sale_price >= 1000;
```

- AND
- OR
- （括号）强化处理



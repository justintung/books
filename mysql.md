- 依價格price desc排序，但是要求產品數量為0的在最後
```
select quantity,price from oc_product order by `quantity`=0,isnull(quantity) or quantity='',`price` desc
```
- 唯一性
```
SELECT *,count(distinct product_id) FROM `order_product` GROUP BY product_id ORDER BY sort_order desc
```
```
SELECT COUNT(distinct product_id) AS total FROM `order_product` LIMIT 1
```
- 查询结果排序（加一个序号）
```
select (@rowNO := @rowNo+1) AS rowno,category_name,category_id,parent_id from (SELECT category_name,category_id,parent_id FROM category ORDER BY sort_order desc) a,(select @rowNO :=0) b
```
- 分组排序
```
set @n=0;set @f=0;
select * from (select category_name,category_id,sort_order,@n:=if(@f=parent_id,@n:=@n+1,1) as id,@f:=parent_id as parent_id from category  WHERE `parent_id` IN (231, 4, 3, 536,425,531,478)  order by parent_id,sort_order desc) a  where id <=20
```
- 根据select结果update表中数据
```
UPDATE oc_product p1 INNER JOIN ((SELECT DISTINCT p.product_id from oc_product p LEFT JOIN oc_product_to_category p2c on p.product_id=p2c.product_id  WHERE p2c.category_id in (20,18)) as cc) ON cc.product_id=p1.product_id set p1.type_id=1
```
- 导如sql文件中的数据到数据库
```
mysql -hlocalhost -uroot -p3344520 --default-character-set=utf8 test < /www/web/1.sql
```
- 批量设置表的存储引擎
```
SELECT CONCAT('ALTER TABLE ', table_name, ' ENGINE=InnoDB;') AS sql_statements FROM information_schema.tables AS tb WHERE table_schema = @DATABASE_NAME AND `ENGINE` = 'MyISAM' AND `TABLE_TYPE` = 'BASE TABLE' ORDER BY table_name DESC
```
@DATABASE_NAME改为数据库名，把查询结果，执行一遍就好了。
- 数据库访问授权
```
GRANT ALL PRIVILEGES ON *.* TO '帐号'@'IP'IDENTIFIED BY '密码' WITH GRANT OPTION
```
让来自IP的帐号（密码）具有访问数据库的所有权限,如：
```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.1.3'IDENTIFIED BY '123456' WITH GRANT OPTION;
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.%' IDENTIFIED BY '123456' WITH GRANT OPTION;
```
- 根据连表，更新结果
```
UPDATE user_order INNER JOIN menu ON user_order.menuid = menu.id SET user_order.sale_price = menu.price,user_order.real_price = menu.price,user_order.menudishes = menu.dishes
```


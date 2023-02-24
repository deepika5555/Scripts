# MYSQL
### Login to eks mysql pods
```sh
mysql -h mysql.${COMPONENT_NAMESPACE}.svc.cluster.local -P 3306 -u user -p${MYSQL_PASS} d_name
```
```sh
Login to dev mysql
 mysql -uroot -ppass
 use database_name;
 describe table_name;
 select * from table_name limit 1;
```

#### To describe create table
```sh
show create table notes
```
#### TO filter out null values
```sh
select * from cases where case_tenant is not null;
```
#### To match strings
```sh
select * from cases where case_tenant like "%abcd%";
 ```
```sh
unix time stamp - UNIX_TIMESTAMP(NOW() - INTERVAL 1 DAY)*1000
 
 
UPDATE table_name
SET column1 = value1, column2 = value2, ...

WHERE condition;
```
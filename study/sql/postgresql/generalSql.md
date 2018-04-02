<!-- MarkdownTOC -->

- [一.常用Sql](#一常用Sql)
    - [1.删除重复数据](#1删除重复数据)
    - [2.单引号转义](#2单引号转义)
    - [3.dblink\(跨库查询\)](#3dblink跨库查询)
    - [4. Convert Mysql to Postgresql](#4-Convert-Mysql-to-Postgresql)
- [二.存储过程](#二存储过程)
    - [1.创建存储过程](#1创建存储过程)

<!-- /MarkdownTOC -->

### 一.常用Sql
#### 1.删除重复数据
```sql
    delete from *tableName* a where a.ctid = any(array (select ctid from (select row_number() over 
    (partition by *field1, field2*), ctid from *tableName*) t where t.row_number > 1));
```

#### 2.单引号转义
在字符串前加*E*

eg. 
```sql
    update city set name = E'Xi\'an';
```

#### 3.dblink(跨库查询)
```sql
    select * from dblink ('hostaddr=127.0.0.1 port=5432 dbname=database 
       user=postgres password=123456',
    E'select id, name from city where name = \'Beijing\'') t (id varchar, name varchar);
```

#### 4. Convert Mysql to Postgresql

[参考](http://pgloader.readthedocs.io/en/latest/)

```sh
# pgloader mysql://username:passwd@ip:port/dbname pgsql://username:passwd@ip:port/dbname
pgloader mysql://root:123456@192.168.13.102:3306/oms pgsql://accu:123456@192.168.13.105:5433/stdoms

```

### 二.存储过程
#### 1.创建存储过程
```sql
    create or replace functions query_city_by_name(_name varchar)
    returns table(id varchar, name varchar)
    as $body$
    declare 
        variable varchar[];
    begin
        return execute E'select id, name from city where name = \''|| _name || '\'';
    end
    $body$
    language plpgsql;
```
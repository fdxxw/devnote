[TOC]
###一．常用Sql
####1.删除重复数据
>     delete from *tableName* a where a.ctid = any(array (select ctid from (select row_number() over (
>         partition by *field1, field2*), ctid from *tableName*) t where t.row_number > 1));

####2.单引号转义
>在字符串前加*E*
>eg. `update table set city = E'Xi\'an'E;`

####3.dblink(跨库查询)
>     select * from dblink ('hostaddr=127.0.0.1 port=5432 dbname=database user=postgres password=123456',
     E'select id, name from city where name = \'Beijing\'') t (id varchar, name varchar)
###二．存储过程
####1.创建存储过程
>     create or replace functions query_city_by_name(_name varchar)
    returns table(id varchar, name varchar)
    as $body$
    declare 
        variable varchar[];
    begin
        return execute E'select id, name from city where name = \''|| _name || '\'';
    end
    $body$
    language plpgsql;
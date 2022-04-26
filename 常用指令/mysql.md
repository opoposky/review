


## mysql 常用指令

1. 登陆 mysql -u[UserName]  -p[password] 
2. 创建 库/表 create databases/table [name] 
3. 列出 库/表 show databases/table
4. 删除 库/表 drop databases/table [name]
5. 选择库 use [database]
6. 查看表结构 desc [table] 
7. 登出 exit 
   

#### 数据库操作

1. 增加 create table [table] ( ...[key] [type] [other] )
2. 删除 delete from [table] [where]
3. 改变 update [table] set [key]=[value] [where]; 对于操作原来数据则 [table].[key] 即可; 
4. 查询 select [...key,] from [table] [where]
5. 关联 关联属于比较复杂的，我看很多人说不要用关联，直到我自己的数据库体量上来，关联数据速度太慢 
   1. left join 左连接  以左表作为主表 select * from [Ta] left join [Tb] on [Ta].[key] = [Tb].[key]   主表会全展示，从表则只会展示关联部分
   2. right join 右连接 和左联相反 `右边为主表`
   3. inner join 内连接 `主表和从表同时存在则展示` 


#### 数据库导入导出

1. 导出库 mysqldump -h [localhost] -u [username] -p [database] > [filePath]
2. 导入库 mysql -u [username] -p [database] < [filePath]

select * from (select title,id from comic limit 1) as comic left join chapter on comic.id = chapter.comicId;
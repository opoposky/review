
## mysql 常见问题

记录在使用 mysql 中的常见问题，用于以后方便查询和解决问题!


#### mysql 遇到存储 emoji 表情时出现错误

问题原因: mysql 的 utf8 编码一个字节最多为 3 个字节，但一个 emoji 表情为 4 字节，所以 utf8 不支持存储 emoji 表情。

解决问题: 使用 utf8 的超集 utf9mb4 可以拥有最多 4 字节，允许支持 emoji 表情的存储。

具体方式:

mysql: create database [tableName] default character set utf8mb4 collate utf8mb4_unicode_ci;

sequelize:
```js
    config.dialectOptions = { // 数据库参数设置  好像没用  还是手动更新数据库字段/整个数据库的字符集 比较靠谱
        charset:"utf8mb4",
        collate:"utf8mb4_general_ci"
    },
```
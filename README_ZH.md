# Mysql 与 SQL server 区别记录

公司新做的项目要考虑兼容 `MySQL` 和 `SQL Server`。一直是使用`SQL Server`,`Mysql`没深度使用过，所以一边开发一边记录下两者的差异。

## 基本语句

## 日常使用

1. 查看表结构

- SQL Server

  ```sql
  --如果是在MSSMS，可以直接写表名，选中表名 alt + F1
  EXEC sys.sp_help  @objname = N'TableName'
  ```

- Mysql

  ```sql
  show full FIELDS from tableName
  ```

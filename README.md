# mysql vs sqlserver

about SQL Server and mysql sql diff

[中文版](README_ZH.md)

## Basic

1. SHOW Table Definition
    - SQL Server

      ```sql
      -- 📌in SSMS，colud chose [tableName],then ALT + F1, like the img
      EXEC sys.sp_help  @objname = N'[TableName]'
      ```

      ![ssms_show_table_Definition](images/ssms_show_table_Definition.gif)

    - Mysql

      ```sql
      SHOW FULL FIELDS FROM [tableName]
      ```

2. Check table exists(if not exists, create it)

    - SQL Server

      ```sql
      IF NOT EXISTS(SELECT 1 FROM TABLE)
      BEGIN
      CREATE TABLE ...
      END
      ```

    - Mysql

      ```sql
      CREATE TABLE IF NOT EXISTS TABLE1(ID VARCHAR(30))
      ```

3. Associated multi table update

    - SQL Server

      ```sql
      UPDATE tableA
      SET tableA.Column1 = tableB.Column2
      FROM [tableName] tableA , [tableName] tableB [join ..]
      WHERE tableA.Id = tableB.XXId
        AND...
      ```

    - Mysql

      ```sql
      UPDATE tableA, tableB [join ..]
      SET tableA.Column1 = tableB.Column2
      WHERE tableA.Id = tableB.XXId
          AND...
      ```

      📌*mysql could update multi table in once update `update tableA,tableB set tableA.column1 = 'a',tableB.column2 = 'b' where ...`*

4. paging query

    - SQL Server

        ```sql
        SELECT * FROM [TableName] [WHERE ...] ORDER BY column [ASC|DESC] OFFSET {(page - 1) * rows} ROWS FETCH NEXT {rows} ROWS ONLY
        ```

        *SQL Server `OFFSET FETCH` support in `sqlserver 2012` for earlier version could use [ROW_NUMBER (Transact-SQL)](https://docs.microsoft.com/zh-cn/sql/t-sql/functions/row-number-transact-sql?view=sql-server-ver15) function*

    - Mysql

        ```sql
        SELECT * FROM [TableName] [WHERE ...] ORDER BY column [ASC|DESC] LIMIT {(page - 1) * rows} , {rows}
        ```

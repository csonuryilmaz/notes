### Mysql add column drop if it exists

MySql has no **add column drop if exists** syntax. Below code makes this possible. Also with a little modification it can be converted to **add column if not exists** function which is also not available in mysql.

```sql
SET sql_notes = 0;
DROP procedure IF EXISTS schema_change;

DELIMITER //
CREATE PROCEDURE schema_change() BEGIN

    /* delete columns if they exist */
    if exists (select * from information_schema.columns where table_schema = schema() 
                    and table_name = 'table' and column_name = 'column') then
        alter table `table` drop column `column`;
    end if;

    /* add columns */
    alter table `table` add column `column` varchar(255) null;

END //

DELIMITER;
CALL schema_change();

DROP PROCEDURE IF EXISTS schema_change;
SET sql_notes = 1;
```

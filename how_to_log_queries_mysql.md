#### Logging Queries Without Restarting MySQL

**1.** Enable table logging.
```sql
SET GLOBAL log_output = 'TABLE';
SET GLOBAL general_log = 'ON';
```
**2.** Logged queries will be written into **mysql.general_log** table. Table structure is:
```sql
SHOW CREATE TABLE mysql.general_log;

CREATE TABLE `general_log` (
  `event_time` timestamp(6) NOT NULL DEFAULT CURRENT_TIMESTAMP(6) ON UPDATE CURRENT_TIMESTAMP(6),
  `user_host` mediumtext NOT NULL,
  `thread_id` bigint(21) unsigned NOT NULL,
  `server_id` int(10) unsigned NOT NULL,
  `command_type` varchar(64) NOT NULL,
  `argument` mediumblob NOT NULL
) ENGINE=CSV DEFAULT CHARSET=utf8 COMMENT='General log';
```
**3.** You can select and examine all records from this table.
```sql
SELECT * from mysql.general_log;
```
**4.** Practically I use below query in order to filter queries in last 2 minutes:
```sql
SELECT event_time, user_host, thread_id, server_id, command_type, CONVERT(argument USING utf8)
FROM mysql.general_log 
WHERE argument <> "SELECT 1" AND argument <> "" 
AND argument <> "SET NAMES 'UTF8'"  AND argument <> "SHOW STATUS"  
AND command_type = "Query"  AND argument <> "SET PROFILING=1"
AND event_time  > (NOW() - INTERVAL 2 MINUTE)
ORDER BY event_time DESC;
```
**5.** At any time you can disable general query logging.
```sql
SET GLOBAL general_log = 'OFF';
```

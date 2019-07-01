# hw27-mysql

- Запускаем стенд **vagrant up**

- Выполняем задания в презентации

Таблицы на мастере:

```
mysql> show tables;
+------------------+
| Tables_in_bet    |
+------------------+
| bookmaker        |
| competition      |
| events_on_demand |
| market           |
| odds             |
| outcome          |
| v_same_event     |
+------------------+
7 rows in set (0.00 sec)
```

Таблицы на слейве:
```
mysql> show tables;
+---------------+
| Tables_in_bet |
+---------------+
| bookmaker     |
| competition   |
| market        |
| odds          |
| outcome       |
+---------------+
5 rows in set (0.00 sec)
```

Кусок лога на мастере с добавлением нового значения:

```
SET TIMESTAMP=1562009418/*!*/;
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'%' IDENTIFIED WITH 'mysql_native_password' AS '*DDB8CB6554EEC4C6B3A6553DC27AABD7D62D7CAC'
/*!*/;
# at 119568
#190701 21:09:44 server id 1  end_log_pos 119633 CRC32 0x25176e1d       GTID    last_committed=39       sequence_number=40      rbr_only=no
SET @@SESSION.GTID_NEXT= '1e2600d1-9c35-11e9-b7b5-525400261060:40'/*!*/;
# at 119633
#190701 21:09:44 server id 1  end_log_pos 119706 CRC32 0xf428b802       Query   thread_id=18    exec_time=0     error_code=0
SET TIMESTAMP=1562015384/*!*/;
BEGIN
/*!*/;
# at 119706
#190701 21:09:44 server id 1  end_log_pos 119833 CRC32 0xb938dbd6       Query   thread_id=18    exec_time=0     error_code=0
SET TIMESTAMP=1562015384/*!*/;
INSERT INTO bookmaker (id,bookmaker_name) VALUES(1,'1xbet')
/*!*/;
# at 119833
#190701 21:09:44 server id 1  end_log_pos 119864 CRC32 0xe7e41703       Xid = 646
COMMIT/*!*/;
SET @@SESSION.GTID_NEXT= 'AUTOMATIC' /* added by mysqlbinlog */ /*!*/;
DELIMITER ;
# End of log file
```

Кусок лога на слейве

```
/*!50530 SET @@SESSION.PSEUDO_SLAVE_MODE=1*/;
/*!50003 SET @OLD_COMPLETION_TYPE=@@COMPLETION_TYPE,COMPLETION_TYPE=0*/;
DELIMITER /*!*/;
# at 4
#190701 21:02:38 server id 2  end_log_pos 123 CRC32 0x7c0ce907  Start: binlog v 4, server v 5.7.26-29-log created 190701 21:02:38 at startup
# Warning: this binlog is either in use or was not closed properly.
ROLLBACK/*!*/;
BINLOG '
7nQaXQ8CAAAAdwAAAHsAAAABAAQANS43LjI2LTI5LWxvZwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAADudBpdEzgNAAgAEgAEBAQEEgAAXwAEGggAAAAICAgCAAAACgoKKioAEjQA
AQfpDHw=
'/*!*/;
# at 123
#190701 21:02:38 server id 2  end_log_pos 154 CRC32 0xfb88ba95  Previous-GTIDs
# [empty]
# at 154
#190701 21:05:17 server id 2  end_log_pos 219 CRC32 0xc6aa7bb2  GTID    last_committed=0        sequence_number=1       rbr_only=no
SET @@SESSION.GTID_NEXT= '8cbfca85-9c43-11e9-8c83-525400261060:1'/*!*/;
# at 219
#190701 21:05:17 server id 2  end_log_pos 414 CRC32 0x07ab3198  Query   thread_id=2     exec_time=0     error_code=0
SET TIMESTAMP=1562015117/*!*/;
SET @@session.pseudo_thread_id=2/*!*/;
SET @@session.foreign_key_checks=1, @@session.sql_auto_is_null=0, @@session.unique_checks=1, @@session.autocommit=1/*!*/;
SET @@session.sql_mode=1436549152/*!*/;
SET @@session.auto_increment_increment=1, @@session.auto_increment_offset=1/*!*/;
/*!\C latin1 *//*!*/;
SET @@session.character_set_client=8,@@session.collation_connection=8,@@session.collation_server=8/*!*/;
SET @@session.lc_time_names=0/*!*/;
SET @@session.collation_database=DEFAULT/*!*/;
ALTER USER 'root'@'localhost' IDENTIFIED WITH 'mysql_native_password' AS '*CEBBC4AA6683AAF72A3A2D0AD9B21ED62E44FBAD'
/*!*/;
# at 414
#190701 21:09:44 server id 1  end_log_pos 479 CRC32 0xb185c010  GTID    last_committed=1        sequence_number=2       rbr_only=no
SET @@SESSION.GTID_NEXT= '1e2600d1-9c35-11e9-b7b5-525400261060:40'/*!*/;
# at 479
#190701 21:09:44 server id 1  end_log_pos 552 CRC32 0x5b6e1784  Query   thread_id=18    exec_time=0     error_code=0
SET TIMESTAMP=1562015384/*!*/;
BEGIN
/*!*/;
# at 552
#190701 21:09:44 server id 1  end_log_pos 679 CRC32 0xcdcf4416  Query   thread_id=18    exec_time=0     error_code=0
use `bet`/*!*/;
SET TIMESTAMP=1562015384/*!*/;
INSERT INTO bookmaker (id,bookmaker_name) VALUES(1,'1xbet')
/*!*/;
# at 679
#190701 21:09:44 server id 1  end_log_pos 710 CRC32 0xee251100  Xid = 775
COMMIT/*!*/;
SET @@SESSION.GTID_NEXT= 'AUTOMATIC' /* added by mysqlbinlog */ /*!*/;
DELIMITER ;
# End of log file
```

# command_mysql

`CREATE USER 'MYUSER'@'%' IDENTIFIED BY 'YOUR_PASSWORD';`


`ALTER USER 'MYUSER'@'%' IDENTIFIED WITH mysql_native_password BY 'YOUR_PASSWORD';`


`GRANT ALL PRIVILEGES ON *.* TO 'MYUSER'@'%';`

`GRANT ALL PRIVILEGES ON DB_NAME.TABLE_NAME TO 'MYUSER'@'%';`

`GRANT UPDATE (column) ON  DB_NAME.TABLE_NAME TO 'MYUSER'@'%';`


`GRANT SELECT ON DB_NAME.* TO 'MYUSER'@'%';`


`SHOW GRANTS FOR 'MYUSER'@'%';`


`docker exec -it my_sql bash`

`mysql -uroot -p`

`SHOW DATABASES;`

`USE database_name;`

`SELECT user,host FROM user;`

**MySQL sets the database to read-only**

`show global variables like '%read_only%';`

**modify read_ Only parameter enable**

` set global read_only = 1;`

**modify read_ Only parameter disable**

` set global read_only = 0;`


`show variables like 'expire_logs_days';`

`set global expire_logs_days=1;`

`flush binary logs;`

`stop slave`

`CHANGE MASTER TO MASTER_HOST='IP_SERVER_MASTER', MASTER_PORT=PORT_MY_MASTER, MASTER_USER='USER_FOR_SLAVE', MASTER_PASSWORD='PASSWORD_USER_SLAVE', MASTER_LOG_FILE='mysql-bin.000123', MASTER_LOG_POS=356;`

`start slave`

`show master status`

`show slave status`


`UPDATE `table` SET expire = DATE_ADD(expire, INTERVAL 1 YEAR) WHERE `expire` <= '2022-01-31 00:00:00'`

**Dump Database Without lock tables**

`docker exec mysql-backup mysqldump -h **IP_server** -P **PORT_SERVER** -u root -p$Pass --quick --triggers --routines --lock-tables=false --single-transaction **DATABASE_NAME** **TABLE_NAME** > $Directory/$Service-$Today.sql`

**Dump Database Without lock tables , without drop tables AND create info tables**

`mysqldump --single-transaction=TRUE --lock-tables=false --skip-add-locks --skip-add-drop-table --no-create-info -u root -p **DATABASE_NAME** --tables **TABLE_NAME** > /var/lib/mysql/dump.sql `

**Dump Database With WHERE Cammand AND Without lock tables , without drop tables AND create info tables**

`mysqldump --single-transaction=TRUE --lock-tables=false --skip-add-locks --skip-add-drop-table --no-create-info -u root -p **DATABASE_NAME** --tables **TABLE_NAME** --where "messages_id >= 'XXXXX' AND messages_id <= 'XXXXX'" > /var/lib/mysql/dumo_where.sql`

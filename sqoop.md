# Sqoop
## Sqoop export
``` sql
sqoop export 
--connect "jdbc:mysql://namenode:3306/flightinfo"
--username root
--password hadoop
--table weather1
--export-dir "/user/horton/weather"
```

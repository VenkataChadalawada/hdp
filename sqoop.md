# Sqoop
## Sqoop export
``` sqoop
sqoop export 
--connect "jdbc:mysql://namenode:3306/flightinfo"
--username root
--password hadoop
--table weather1
--export-dir "/user/horton/weather"
```
## sqoop import
``` sqoop
sqoop import 
--connect "jdbc:mysql://namenode:3306/flightinfo"
--username root
--password hadoop
--table weather2
--target-dir "/user/horton/imported_weather"
```

## sqoop import into hive
``` sqoop
sqoop import
--connect "jdbc:mysql://namenode:3306/flightinfo
--table weather2
--username root
--passwood hadoop
--hive-import
-m 1
--hive-overwrite
```
## sqoop import all tables into hive
``` sqoop import 
--connect "jdbc:mysql://namenode:3306/flightinfo
--username root
--password hadoop
--warehouse-dir "/user/horton/fullhouse"
-m 2
```
## incremental import 
``` sqoop import 
--connect "jdbc:mysql://namenode:3306/flightinfo
--username root
--password hadoop
--table students
--target-dir "/user/horton/students"
--append
--where "sno>4"
-m 1
```
## incremental import using check-column
``` sqoop import 
--connect "jdbc:mysql://namenode:3306/flightinfo
--username root
--password hadoop
--table students
--target-dir "user/horton/students"
--append
--check-column "sno"
--incremental append
--last-value 7
```
## query import
``` sqoop import 
--connect "jdbc:mysql://namenode:3306/flightinfo
--username root
--password hadoop
--query "select * from orders where deptid='abc' and \$CONDITIONS"

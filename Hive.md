# Hive
## create an managed orc table from local dataset
``` sql
CREATE TABLE sfo_weather_staging(
station_name string,
Year int,
Month int,
DayOfMonth int,
precipitation int,
temperature_max int,
temperature_min int)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY','
STORED AS TEXTFILE;

LOAD DATA LOCAL INPATH '/home/horton/datasets/flightdelays/sfo_weather.csv' INTO TABLE sfo_weather_staging;

CREATE TABLE sfo_weather as select * from sfo_weather_staging; 
// ORC table creation from staging table as we cant directly create orc table from local csv files

//say if there is already a orc table its just we need to insert then
INSERT INTO TABLE sfo_weather as select * from sfo_weather_staging;

// Testing
select * from sfo_weather limit 10;
show create table sfo_weather; // this tells us all table properties
```

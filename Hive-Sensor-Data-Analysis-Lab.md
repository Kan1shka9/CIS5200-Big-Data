#### Hive Sensor Data Analysis Lab

- Download sensor data to the local systems in Bluemix BigInsights
- Upload it to HDFS
- Manipulate and analyze sensor data in HDFS using HiveQL
- Visualize the result in Excel

![Image of sensor](images/4/1.png)

![Image of sensor](images/4/2.png)

![Image of sensor](images/4/3.png)

![Image of sensor](images/4/4.png)

![Image of sensor](images/4/5.png)

![Image of sensor](images/4/6.png)

![Image of sensor](images/4/7.png)

![Image of sensor](images/4/8.png)

![Image of sensor](images/4/9.png)

![Image of sensor](images/4/10.png)

![Image of sensor](images/4/11.png)

```sh
wget -O SensorFile.zip http://s3.amazonaws.com/hw-sandbox/tutorial14/SensorFiles.zip
unzip SensorFile.zip
hdfs dfs -mkdir SensorFiles
hdfs dfs -mkdir SensorFiles/hvac
hdfs dfs -mkdir SensorFiles/building
hdfs dfs -ls
```

![Image of sensor](images/4/12.png)

```sh
cd SensorFiles
ls -l
hdfs dfs -put HVAC.csv SensorFiles/hvac
hdfs dfs -put building.csv SensorFiles/building
hdfs dfs -ls SensorFiles/building
hdfs dfs -ls SensorFiles/hvac
```

![Image of sensor](images/4/13.png)

```
hive

DROP TABLE IF EXISTS hvac;

CREATE EXTERNAL TABLE IF NOT EXISTS hvac(`date` STRING, time STRING, targettemp BIGINT, actualtemp BIGINT, system BIGINT, systemage BIGINT, buildingid BIGINT) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS TEXTFILE LOCATION '/user/kan1shka/SensorFiles/hvac' TBLPROPERTIES ('skip.header.line.count'='1');

show tables;

select * from hvac limit 10;
```

![Image of sensor](images/4/14.png)

```
describe formatted hvac;
```

![Image of sensor](images/4/15.png)

```
DROP TABLE IF EXISTS building;

CREATE EXTERNAL TABLE IF NOT EXISTS building(buildingid BIGINT, buildingmgr STRING, buildingage BIGINT, hvacproduct STRING, country STRING) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS TEXTFILE LOCATION '/user/kan1shka/SensorFiles/building' TBLPROPERTIES ('skip.header.line.count'='1');

select * from building limit 10;
```

![Image of sensor](images/4/16.png)

```
describe formatted building;
```

![Image of sensor](images/4/17.png)

```
DROP TABLE IF EXISTS hvac_temperatures;

CREATE TABLE hvac_temperatures ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS TEXTFILE LOCATION '/user/kan1shka/SensorFiles/hvac_temperatures/' AS SELECT *, targettemp - actualtemp AS temp_diff, IF((targettemp - actualtemp) > 5, 'COLD', IF((targettemp - actualtemp) < -5, 'HOT', 'NORMAL')) AS temprange, IF((targettemp - actualtemp) > 5, '1', IF((targettemp - actualtemp) < -5, '1', 0)) AS extremetemp FROM hvac;

show tables;
```

![Image of sensor](images/4/18.png)

```
describe hvac_temperatures;

select targettemp, actualtemp, system, systemage, temp_diff, temprange, extremetemp from hvac_temperatures LIMIT 10;
```

![Image of sensor](images/4/19.png)

```
DROP TABLE IF EXISTS hvac_building;

CREATE TABLE hvac_building ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' STORED AS TEXTFILE LOCATION '/user/kan1shka/SensorFiles/hvac_building/' AS SELECT h.*, b.country, b.hvacproduct, b.buildingage, b.buildingmgr FROM building b JOIN hvac_temperatures h ON b.buildingid = h.buildingid;

show tables hvac_building;
```

![Image of sensor](images/4/20.png)

```
describe hvac_building;

select targettemp, actualtemp, system, systemage, temp_diff, temprange, extremetemp, country, hvacproduct, buildingmgr from hvac_building LIMIT 10;
```

![Image of sensor](images/4/21.png)

![Image of sensor](images/4/22.png)

![Image of sensor](images/4/23.png)

![Image of sensor](images/4/24.png)

![Image of sensor](images/4/25.png)

![Image of sensor](images/4/26.png)

![Image of sensor](images/4/27.png)

![Image of sensor](images/4/28.png)

![Image of sensor](images/4/29.png)

![Image of sensor](images/4/30.png)

![Image of sensor](images/4/31.png)

![Image of sensor](images/4/32.jpeg)

![Image of sensor](images/4/33.jpeg)

![Image of sensor](images/4/34.jpeg)

![Image of sensor](images/4/35.jpeg)

![Image of sensor](images/4/36.jpeg)

![Image of sensor](images/4/37.jpeg)

![Image of sensor](images/4/38.jpeg)

![Image of sensor](images/4/39.jpeg)

![Image of sensor](images/4/40.jpeg)

![Image of sensor](images/4/41.jpeg)

![Image of sensor](images/4/42.jpeg)

![Image of sensor](images/4/43.jpeg)

![Image of sensor](images/4/44.jpeg)
## rtl433 to Elasticsearch

### 1. Start rtl_433 to send data
```sh
docker-compose -f rtl433_syslog-compose.yml up
```
or setup https://github.com/merbanan/rtl_433 manually and start as: 

```sh
rtl_433 -G -F syslog:127.0.0.1:1514
```
### 2. Start ELK stack: 
```sh
docker-compose -f elk-compose.yml up
```
### 3. Goto Kibana and create an index pattern

### 4. Visualize data

For example temperature from a temperature sensor with timelion
```
.es(index=rtl_433-*,metric="avg:rtl_433.temperature_C"), .es(index=rtl_433-*,metric="avg:rtl_433.temperature_C").trend(mode=liner)
```

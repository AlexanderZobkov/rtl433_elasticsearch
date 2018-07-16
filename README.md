## rtl433_elasticsearch

1. Build and start rtl_433: https://github.com/merbanan/rtl_433
```sh
rtl_433 -G -F syslog:127.0.0.1:1514
```
2. Start ELK stack: 
```sh
docker-compose up
```
3. Goto Kibana and create index pattern

4. Visualize data

For example temperature from a temperature sensor with timelion
```
.es(index=rtl_433-*,metric="avg:rtl_433.temperature_C"), .es(index=rtl_433-*,metric="avg:rtl_433.temperature_C").trend(mode=liner)
```

## TODO
1. Dockerize building and running rtl_433 tool 


### 基本使用

ab -n 100 -c 100 http://

### POST
1. 需要将post数据放到 ``json``文件中; 
格式:
```
params={key: value}
```

2. -p post.json -T "application/x-www-form-urlencoded" 配对使用
```

ab -n 100 -c 100 -p post.json -T "application/x-www-form-urlencoded" http://

```
## 结果
Server Software:
Server Hostname:        192.168.0.37
Server Port:            5000

Document Path:          /stat/total
Document Length:        50 bytes

Concurrency Level:      100                         //并发数
Time taken for tests:   0.036 seconds               //整个测试持续时间
Complete requests:      100                         //完成请求数量
Failed requests:        0                           //失败请求数量
Total transferred:      16700 bytes                 //整个过程中网络传输量
Total body sent:        29600                       //
HTML transferred:       5000 bytes                  //整个过程HTML传输量
Requests per second:    2741.23 [#/sec] (mean)      //每秒请求数数(平均)
Time per request:       36.480 [ms] (mean)          //请求响应时间(平均)
Time per request:       0.365 [ms] (mean, across all concurrent requests)  //每个请求实际响应时间（平均)
Transfer rate:          447.06 [Kbytes/sec] received    //平均每秒网络上的流量
                        792.39 kb/s sent
                        1239.44 kb/s total

Connection Times (ms)                               //网络消耗时间分解
              min  mean[+/-sd] median   max
Connect:        1    2   0.6      2       3
Processing:    17   29   3.3     30      33
Waiting:       17   29   3.3     30      33
Total:         18   31   3.3     31      36

Percentage of the requests served within a certain time (ms)  //整个场景中请求响应情况
  50%     31                  //50%的用户响应时间小于 31毫秒
  66%     32
  75%     33
  80%     33
  90%     34
  95%     35
  98%     35
  99%     36
 100%     36 (longest request)

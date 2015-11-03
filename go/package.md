gox
----
go 交叉编译工具
https://github.com/mitchellh/gox
``` 
$ gox -osarch="linux/amd64"
```
protobuf
---
https://github.com/golang/protobuf/
```   
  brew install protobuf --devel

  protoc --go_out=plugins=grpc:. *.proto
```

daemon
---
```
// 开发环境
goreman start


//部署环境
supervisorctl -c /etc/supervisord.conf

```

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
supervisord -c /etc/supervisord.conf

//cli
supervisorctl status ...

```

## 性能分析
```
go get github.com/davecheney/profile
```

## vscode 需要用到的工具
go get -u -v github.com/nsf/gocode
go get -u -v github.com/rogpeppe/godef
go get -u -v github.com/golang/lint/golint
go get -u -v github.com/lukehoban/go-find-references
go get -u -v sourcegraph.com/sqs/goreturns
go get -u -v golang.org/x/tools/cmd/gorename
go get -u -v github.com/derekparker/delve/cmd/dlv


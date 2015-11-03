1. fork 代码
2. clone fork 分支到本地
``` go
git clone git://...
```

3. 增加 ``源分支``
``` go
git remote add xxxx git://github.com/.....
```

4. fetch ``源分支`` 的新版本到本地 
``` go
git fetch xxxx
```
5. 合并两个版本的代码
```go
git merge xxxx/master
```

6. 将合并的代码push到github上去
``` go
git push origin master
```

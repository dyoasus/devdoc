# MAC 环境

## 安装
1. 安装 VirtualBox,从官网直接下载 (一般brew中的版本比官网中的版本要低)
2. brew 安装
```
brew install docker docker-machine docker-compose
brew cask install kitematic
```
> docker-machine: 用来管理虚拟机，之前的boot2docker已经合并到这个工具中了。
> docker-compose: 用来管理多个 docker container。
> kitematic     : 用来远程管理docker hub，自己构建的Docker Image 也可以用它来管理

## 配置
创建一台新的 ``Docker Machine``  
``` js
docker-machine create -driver virtualbox dev  //创建一台名为 “dev” 的机器
docker-machine env dev                        //查看刚创建的机器的信息
```
将``dev`` 信息添加到环境变量中
```
eval "$(docker-machine env dev)"
```
```
docker info
```
配置 docker 加速
1. 从阿里开发者平台获取专属加速器地址
2. 重启 dev
```
docker-machine ssh dev "echo 'EXTRA_ARGS=\"--registry-mirror=https://1ufqzhi9.mirror.aliyuncs.com\"' | sudo tee -a /var/lib/boot2docker/profile"
docker-machine restart dev
```
验证
```
docker run hello-world  
```

# aliyun 容器服务

CentOS
--

```
yum install docker
```

# 资源
[国内加速访问Docker相关资源](https://github.com/denverdino/aliyungo/wiki/Speed-Up-Docker-Access-In-China)

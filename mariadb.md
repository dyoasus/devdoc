## 安装
```
yum -y install mariadb-server mariadb
```
## 启动
```
systemctl start mariadb
```
## 开机启动
```
systemctl enable mariadb
```
## 查看状态
```
systemctl status mariadb
```
## 停止
```
systemctl stop mariadb
```
## Client
```
mysql
```
## CMD
```
show databases;

//使设置生效
FLUSH PRIVILEGES;
```



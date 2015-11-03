## 安装
##### centos

yum 安装
> yum install nginx
> chconfig nginx on # 开机启动

配置文件
> /etc/nginx/nginx.conf

web 目录
> /usr/share/nginx/html

## 负载均衡配置

```
// vim /etc/nginx/nginx.con

upstream webservers {
   server 192.168.18.201 weight=1;
   server 192.168.18.202 weight=1;
}

server {
      
      listen       80;
      server_name  _;                  #绑定域名
      location / {
        proxy_pass http://webservers;  #引用 webservers
      }

      ...
}

//systemctl restart nginx.service

```
##### upstream 支持的负载均衡算法
Nginx的负载均衡模块目前支持4种调度算法，下面进行分别介绍，其中后两项属于第三方调度算法。  
* 轮询（默认）。每个请求按时间顺序逐一分配到不同的后端服务器，如果后端某台服务器宕机，故障系统被自动剔除，使用户访问不受影响。Weight 指定轮询权值，Weight值越大，分配到的访问机率越高，主要用于后端每个服务器性能不均的情况下。
* ip_hash。每个请求按访问IP的hash结果分配，这样来自同一个IP的访客固定访问一个后端服务器，有效解决了动态网页存在的session共享问题。
* fair。这是比上面两个更加智能的负载均衡算法。此种算法可以依据页面大小和加载时间长短智能地进行负载均衡，也就是根据后端服务器的响应时间来分配请求，响应时间短的优先分配。Nginx本身是不支持fair的，如果需要使用这种调度算法，必须下载Nginx的upstream_fair模块。
* url_hash。此方法按访问url的hash结果来分配请求，使每个url定向到同一个后端服务器，可以进一步提高后端缓存服务器的效率。Nginx本身是不支持url_hash的，如果需要使用这种调度算法，必须安装Nginx 的hash软件包。

##### upstream 支持的状态参数
在HTTP Upstream模块中，可以通过server指令指定后端服务器的IP地址和端口，同时还可以设定每个后端服务器在负载均衡调度中的状态。常用的状态有：      
* down，表示当前的server暂时不参与负载均衡。
* backup，预留的备份机器。当其他所有的非backup机器出现故障或者忙的时候，才会请求backup机器，因此这台机器的压力最轻。
* max_fails，允许请求失败的次数，默认为1。当超过最大次数时，返回proxy_next_upstream 模块定义的错误。
* fail_timeout，在经历了max_fails次失败后，暂停服务的时间。max_fails可以和fail_timeout一起使用。

### 异常
* 403 Forbidden
  * 将nginx.conf 第一行改为 user root (开发)
  * 将目录移到 /usr/share/nginx/html 中（生产） 

### 资料
* [Nginx 反向代理、负载均衡、页面缓存、URL重写及读写分离详解](http://freeloda.blog.51cto.com/2033581/1288553)


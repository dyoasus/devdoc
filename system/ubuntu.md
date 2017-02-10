#防火墙
``
//iptables 防火墙配置工具
apt-get install ufw

ufw enable

ufw default deny

ufw allow 80  //允许外部访问

ufw allow delete allow 80 //禁止外部访问
```

```
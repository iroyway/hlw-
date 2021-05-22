# 在Alpine 中启动ssh

1. 【远程服务器】启动容器，把容器里面的22端口映射出来，例如映射到主机的3333端口：-p 3333:22
2. 【远程服务器docker】设置root密码
```
sudo passwd root
```
3. 【远程服务器docker】安装ssh服务
先依次运行下列命令
```
apk add openssh-server
apk add --no-cache openrc
rc-update add sshd
```
4. 【远程服务器docker】配置ssh 开启root权限
```
sed -i "s/#PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config
```
5. 【远程服务器docker】重启服务
```
rc-service sshd restart
```
6. 【远程服务器docker】  
看下这个ssh服务的网络连接情况:  
```
netstat -ntlp
```
如果看到如下内容,则表示已开启:  
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN 
7. 【远程服务器】连接测试
先查看服务器ip
```
docker container inspetc name/id
```
![ssh](./docker/dockerbiji/img/shh.png)
```
ssh root@your-server-ip -A -p 22
```
8. 【本地连接】
```
ssh root@your-server-ip -A -p 3333（3333为第1步设置的端口）
```


参考：https://stackoverflow.com/questions/35690954/running-openssh-in-an-alpine-docker-container